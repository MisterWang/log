# indexdb.md

## 简单封装
```
function IDBCon(cb) {
    this.db;
    this.dbname = 'mystars';
    this.version = '1';
    this.tables = ['stars', 'tags', 'cates', 'colors', 'lan'];

    //连接
    var con = this;
    this.open = function() {
        var req = indexedDB.open(con.dbname, con.version);
        req.onerror = function(req, ev) {
            console.log('error');
        };
        req.onsuccess = function(req, ev) {
            con.db = req.target.result;

            cb(con);
        };
        req.onupgradeneeded = function(req, ev) {
            con.db = req.target.result;

            console.log('onupgradeneeded');
            con.tables.forEach(function(elm) {
                console.log(elm);
                con.db.createObjectStore(elm, { keyPath: "id" });
            });
        };
    };
    
    //get obj
    this.get = function(table, key, cb) {
        var transaction = con.db.transaction([table], "readwrite");
        var store = transaction.objectStore(table);
        var req = store.get(key);
        req.onsuccess = function(ev) {
            cb(ev.target.result);
        };
    };
    this.set = function(table, val) {
        var transaction = con.db.transaction([table], "readwrite");
        var store = transaction.objectStore(table);
        console.log(store);
        // store.add(val);
        store.put(val);
    };
    this.forEach = function(table, cb, endCb) {
        var store = con.db.transaction(table).objectStore(table);

        store.openCursor().onsuccess = function(event) {
            var cursor = event.target.result;
            if (cursor) {
                // alert("Name for SSN " + cursor.key + " is " + cursor.value.name);
                cb(cursor.key, cursor.value);
                cursor.continue();
            } else {
                // alert("No more entries!");
                endCb();
            }
        };
    };
}
```
