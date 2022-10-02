## URL和URI的区别

### URI
- **定义**：统一资源标志符(`Uniform Resource Identifier， URI`)，表示的是web上每一种可用的资源，如 HTML文档、图像、视频片段、程序等都由一个URI进行标识的。
- **如何理解**：
	- `Identifier`标识符，那就是用来标识的，唯一作用就是标识某个资源。
	- 那么按照什么方式、以什么标准去标识？
		- 用**定位**的方式：URL (Uniform Resource `Locator`)
		- 用**命名**的方式：URN (Uniform Resource `Name`)

### URL
- **定义**：统一资源定位符(`Uniform Resource Locator，URL` )，用于表示互联网上某一资源的网址。简单来说，`URL`就是**网址**。

- **格式**：
  
  - 协议`://`服务器地址`:`端口号`/`路径`/`文件名`?`查询参数`#`片段。
  
    protocol `://` hostname[`:`port]` / `path `/ `[;parameters] [`?`query]`#`fragment
  
  - 参数在`?`之后开始，使用`参数名=参数值`的方式，多个参数用`&`隔开。
  
  - `#`左边部分是浏览器可以从服务器下载的资源。
  
  - `#`右边部分是片段标识符。片段表示资源的某一位置，与从服务器返回的资源无关。
  
  - 端口号、查询、片段ID都属于选填项。

> [!Note|style:callout|label:总结]
> `URI`和`URL`都定义了资源是什么，但`URL`还定义了该如何访问资源。`URL`是一种具体的`URI`，它是`URI`的一个子集，它不仅唯一标识资源，而且还提供了定位该资源的信息。



