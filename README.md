# Lua Inspect
这是一组API，用于调试Lua GCObject。主要思路是为每一个GCObject赋予一个age字段。根据age字段排查一段时间内新增的GCObject。

## inspect('set_age', age)
设置全局age。此后新增的GCObject的age都是这个全局age的值。

## inspect('dump', age, filename)
把指定age的GCObject的信息dump到指定文件中。
如果age是-1，那么dump所有GCObject。
在调用这个函数前，应该先进行一次(或多次)全量垃圾回收`collectgarage('collect')`

## inspect('get_ref_path', '0x561af05a5370')
查询指定GCObject的引用路径

## inspect('get_gco', '0x561af05a5370')
查询指定GCObject，包装为TValue，返回给Lua
