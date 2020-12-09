# vaptcha-iframe

演示 (同源, 可尝试将 index.html 部署到不同源的地址上): https://jixunmoe.github.io/vaptcha-iframe/

利用 iframe 实现 vaptcha 的验证与 token 获取。

* `frame.html` 通用 iframe 方案，通过在 URL 后面添加 `#` 参数实现简单的控制。
  * 参数为 `#<origin>|<验证单位 ID>`
* `index.html` 是主页面，用于演示调用 `frame.html` 获取验证 token 的代码样例。
  * 演示了如何在提交数据前进行人机验证。
  * 获取到的 `token` 需要之后发送到后端进行验证，前端无任何验证功能。
* `getVaptchaCode.js` 依赖文件
  * 这个文件提供了 `getVaptchaCode(frameURL: string, container: HTMLElement): Promise<string>` 函数。

---

`getVaptchaCode`:

* `frameURL`: iframe 指向的地址。
  * 有两个参数，一个是 `origin`，可通过 `location.origin` 属性获取；
  * 还有一个是 VID （验证单元 ID），后台获取。
  * 拼接：`const frameURL = 'https://jixunmoe.github.io/vaptcha-iframe/frame.html#' + location.origin + '|5b4d9c76a485e504101923df';`
* `container`: 放置 iframe 的容器，可自行定义容器的显示效果（如弹出效果）。
