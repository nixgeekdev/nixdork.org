---
title: 'How to find the longest string in a varchar column in SQL Server'
slug: 'how-to-find-the-longest-string-in-a-varchar-column-in-sql-server'
date: 2010-11-17T18:32:50-08:00
tags: ['database']
---

If you need to find the longest string in a column in a table in SQL Server
which has a datatype of `varchar(X)` or `nvarchar(X)`, where `X` is a valid
integer value for the datatype, then you will need to use the following query:

    select MyVarcharColumnName
    from MyTableName
    where len(MyVarcharColumnName) =
        (select max(len(MyVarcharColumnName))
         from MyTableName)

In the query above you will need to substitute `MyVarcharColumnName` and
`MyTableName` by your respective column and table names.
