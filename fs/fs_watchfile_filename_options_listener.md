<!-- YAML
added: v0.1.31
changes:
  - version: v7.6.0
    pr-url: https://github.com/nodejs/node/pull/10739
    description: The `filename` parameter can be a WHATWG `URL` object using
                 `file:` protocol. Support is currently still *experimental*.
-->

* `filename` {string|Buffer|URL}
* `options` {Object}
  * `persistent` {boolean} **默认值:** `true`。
  * `interval` {integer} **默认值:** `5007`。
* `listener` {Function}
  * `current` {fs.Stats}
  * `previous` {fs.Stats}

监视 `filename` 的更改。
每当访问文件时都会调用 `listener` 回调。

`options` 参数可以省略。
如果提供，则它应该是一个对象。
`options` 对象可以包含一个名为 `persistent` 的布尔值，指示当文件正在被监视时，进程是否应该继续运行。
`options` 对象可以指定 `interval` 属性，指示轮询目标的频率（以毫秒为单位）。

`listener` 有两个参数，当前的 stat 对象和之前的 stat 对象：

```js
fs.watchFile('message.text', (curr, prev) => {
  console.log(`当前的最近修改时间是: ${curr.mtime}`);
  console.log(`之前的最近修改时间是: ${prev.mtime}`);
});
```

这些 stat 对象是 `fs.Stat` 的实例。

要在修改文件（而不仅仅是访问）时收到通知，则需要比较 `curr.mtime` 和 `prev.mtime`。

当 `fs.watchFile` 操作导致 `ENOENT` 错误时，它将调用一次监听器，并将所有字段置零（或将日期设为 Unix 纪元）。
如果文件是在那之后创建的，则监听器会被再次调用，且带上最新的 stat 对象。
这是 v0.10 之后的功能变化。

使用 [`fs.watch()`] 比 `fs.watchFile` 和 `fs.unwatchFile` 更高效。
应尽可能使用 `fs.watch` 代替 `fs.watchFile` 和 `fs.unwatchFile`。

当 `fs.watchFile()` 正在监视的文件消失并重新出现时，第二次回调事件（文件重新出现）返回的 `previousStat` 会与第一次回调事件（文件消失）返回的 `previousStat` 相同。

这种情况发生在:
- 文件被删除，然后又恢复。
- 文件被重命名，然后再第二次重命名回其原来的名称。

