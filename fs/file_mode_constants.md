
以下常量适用于 [`fs.Stats`] 对象的 `mode` 属性，用于决定文件的访问权限。

<table>
  <tr>
    <th>常量</th>
    <th>说明</th>
  </tr>
  <tr>
    <td><code>S_IRWXU</code></td>
    <td>表明所有者可读、可写、可执行。</td>
  </tr>
  <tr>
    <td><code>S_IRUSR</code></td>
    <td>表明所有者可读。</td>
  </tr>
  <tr>
    <td><code>S_IWUSR</code></td>
    <td>表明所有者可写。</td>
  </tr>
  <tr>
    <td><code>S_IXUSR</code></td>
    <td>表明所有者可执行。</td>
  </tr>
  <tr>
    <td><code>S_IRWXG</code></td>
    <td>表明群组可读、可写、可执行。</td>
  </tr>
  <tr>
    <td><code>S_IRGRP</code></td>
    <td>表明群组可读。</td>
  </tr>
  <tr>
    <td><code>S_IWGRP</code></td>
    <td>表明群组可写。</td>
  </tr>
  <tr>
    <td><code>S_IXGRP</code></td>
    <td>表明群组可执行。</td>
  </tr>
  <tr>
    <td><code>S_IRWXO</code></td>
    <td>表明其他人可读、可写、可执行。</td>
  </tr>
  <tr>
    <td><code>S_IROTH</code></td>
    <td>表明其他人可读。</td>
  </tr>
  <tr>
    <td><code>S_IWOTH</code></td>
    <td>表明其他人可写。</td>
  </tr>
  <tr>
    <td><code>S_IXOTH</code></td>
    <td>表明其他人可执行。</td>
  </tr>
</table>

