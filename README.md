# Dirac Automatic Column Reference

 Automatically use a column for table references in schemas.
 
```javascript
/**
 * groups schema
 */

// Dirac table schema
{
  name: 'groups'
, schema: {
    id:    { type: 'serial', primaryKey: true }
  , name:  { type: 'text' }
    // No need to specify column: 'id' in the references
  , uid:   { type: 'integer', references: { table: 'users' } }
  }
}
```

```javascript
/**
 * Main DB module
 */

var dirac = require('dirac');
var tableRef = require('dirac-table-ref');

dirac.use(
  // Override default column used `id`
  tableRef({ column: 'uuid'  })
);
```
