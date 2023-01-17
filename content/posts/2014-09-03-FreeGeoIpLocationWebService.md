---
title: 'Free GeoIp location web service'
slug: 'free-geoip-location-web-service'
date: 2014-09-03T21:54:04-08:00
tags: ['linux','programming','python']
---

This weekend I found a really cool web service at
[FreeGeoIp.net](http://freegeoip.net/). Their API is really simple... just send
a HTTP GET request to:

    http://freegeoip.net/{format}/{ip_or_hostname}

Here are some of the implementation details:

1. SSL is supported
2. Formats are csv, json, and xml
3. IP is optional. It defaults to your current IP.

I quickly implemented a comnmand line client written in Python 3. It uses the
awesome [requests](http://docs.python-requests.org/en/latest/) library and
ElementTree to parse the resulting XML response. Here's the code...

    def main():
        args = parse_args()

        MYIP_URL = 'http://freegeoip.net/xml/'
        MYIP_HEADERS = {'Accept': 'application/xml'}

        if args.ip is not None:
            MYIP_URL = MYIP_URL + args.ip

        rspn = requests.get(MYIP_URL, headers=MYIP_HEADERS)
        tree = etree.ElementTree(etree.fromstring(rspn.text))
        root = tree.getroot()

        ip = root.find('Ip')
        cntr = root.find('CountryName')
        reg = root.find('RegionName')
        city = root.find('City')

        print('Your Current IP: %s' % ip.text)
        print('You appear to be in %s, %s, %s' % (city.text, reg.text, cntr.text))

Or you can get the
[whole code](https://github.com/gorauskas/Hacks/blob/master/python/myip) from my
[github profile](https://github.com/gorauskas).
