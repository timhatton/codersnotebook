---
layout: note
title: SQL tips and tricks
category: DB
---

To drop a database (when it keeps saying that it is currently in use):
```sql
ALTER DATABASE dbName SET SINGLE_USER WITH ROLLBACK IMMEDIATE
DROP DATABASE dbName
```

