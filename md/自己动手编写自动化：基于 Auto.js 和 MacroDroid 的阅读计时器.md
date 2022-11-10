> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [sspai.com](https://sspai.com/post/76721)

> 打开阅读软件那一刻开始计时、退出阅读软件后停止，要想实现这个功能，除了 Tasker 你还可以借助 Auto.js 和 MacroDroid 手动编写。

Don't Repeat Yourself
---------------------

除了消遣娱乐之外，阅读通常也是我使用手机最多的场景之一。

由于我个人有记录时间的习惯，所以当我阅读时会手动在计时应用上先开始计时，然后再进行阅读，结束之后再手动停止计时并打卡记录当天的完成情况。

经过多次人工重复性地操作之后，我似乎对这一过程感到有些枯燥和不耐烦，也下意识感觉到自己违反了软件开发中经典的 DRY 原则（**D**on't **R**epeat **Y**ourself），于是我就想：

> 为什么不能让手机自动地从我打开阅读软件那一刻开始计时，在退出阅读软件后停止计时呢？

借助搜索引擎发现了 Fairyex 使用 Tasker 自动化记录时间的文章之后，我才知道不仅只有我一个人有这样的想法；可考虑到我没有 Tasker 无法直接「照抄作业」，于是秉承着「只要思想不滑坡，方法总比困难多」想法，在稍加尝试之后我打算用自己 Android 手机上现有的两个工具——Auto.js 和 MacroDroid——来实现同样的功能。

效果如下：

![](https://cdn.sspai.com/editor/u_/cdlke55b34tcd6q36fb0)

**关联阅读：**[用 Tasker 实现时间记录自动化](https://sspai.com/post/56699)

我的实现思路
------

实现自动化时间记录的第一步，是要选择可以记录时间并且能提供类似 URL Schema 或类似 API 接口的计时工具。

![](https://cdn.sspai.com/editor/u_/cdlke5db34tcdtg9f300)

我和 Fairyex 一样，都是使用的 [Toggl](https://track.toggl.com/timer)（按：如今已更名为 Toggl Track）这一款简洁、无广告且跨平台工具的来记录时间，而该工具又提供了 [API](https://developers.track.toggl.com/docs/) 接口，所以该工具是这次自动化中用以记录时间的关键。

自动开始计时与停止计时两个过程我们都会通过 Toggl 提供的 API 接口来完成。

**关联阅读：**[时间量化管理：Toggl 的使用](https://sspai.com/post/44349)

确定了基本的切入点之后，接下来的步骤比较明确：

1.  检测到目标 App 打开后：开始向 Toggl API 发送 HTTP 请求开始计时，并给出提示消息；
2.  类似地，检测到目标 App 退出后：向 Toggl API 再发送一次 HTTP 请求，表示停止计时并同样给出提示消息，进而完成一次记录。

为什么不用 Tasker
------------

Fairyex 的文章介绍过一种完全使用 Tasker 来实现记录的自动化方案，所以本质上 MacroDroid 也能实现。

**但我个人不喜欢多次拖拽并在多层级界面中来回切换。**考虑到在实现的过程中会有一些复杂的逻辑，因此与 Toggl API 交互的部分我主要用 Auto.js 来完成，它可以让我直接编写代码来发送 HTTP 请求——我在之前的文章中有过介绍，Auto.js 是一款允许用户通过编写 JavaScript 代码来实现自动化的 Android 应用，并且也支持安装 [npm](https://www.npmjs.com/) 包来接入庞大的 JavaScript 生态资源。

**关联阅读：**[自己动手实现 Android 自动化：用 Auto.js 自动复制短信验证码](https://sspai.com/post/76377)

**不同于 Tasker 或 MacroDroid，在 Auto.js 上我们可以直接用代码编写更为复杂的操作逻辑，并且也可以随时对代码进行调试**。比如 Toggl 提供了 API 接口，那么用类似于 Tasker 这样的工具来访问请求就需要经过多步点击：

![](https://cdn.sspai.com/editor/u_/cdlke5tb34tcd6q36fbg)

_配图引自 Fairyex 文章_

而在使用 Auto.js 的情况下就可以略过多次跳转的过程，直接通过敲入代码来快速搞定，伪代码如下：

```
const token = '<toggl-token>'
const api = '<toggl-api>'
const data = {
    "description": "task name"
    ...
}
http.post(api, data, {
    headers: {
        'Authorization': `Basic ${token}`
    }
})


```

不过这可能让你以为整个自动化流程仅仅只需要这样简单的 HTTP 请求代码即可，但其实我们还会加入更多的判断逻辑，比如：

*   所在的前台应用是否为我们需要计时的目标应用？如果不是我们还是否需要操作？
*   如果我在桌面端已经有了一个 Toggl 计时，又或者是当前应用已经正在计时，那么我们该怎么处理？
*   ……

这些判断逻辑可以根据自己的需要随意增删，但随着判断逻辑的增加，倘若还完全地靠点击拖拽来增加更多的应对操作无疑是一件劳心劳力的事情，这也是为什么我是需要 Auto.js 来实现主要步骤。

至于「目标 App 是否打开 / 关闭」的条件检测，我打算使用 MacroDroid 这一款和 Tasker 类似的自动化工具来辅助，该应用提供的触发器可以很大程度上弥补 Auto.js 缺少的功能。并且 MacroDroid 还兼具功能丰富、易上手且提供中文界面等优点，我在后续将会再写一篇文章详细介绍它，此处暂且按下不表。

至此，整个自动化的实现思路就被我梳理成了如下流程图：

![](https://cdn.sspai.com/editor/u_/cdlke65b34tcdjag47e0)

基于 Auto.js 编写复杂的操作逻辑
--------------------

值得一提的是，除了上面提到的判断逻辑，Toggl API 在开源社区中已有许多第三方实现，并且 Auto.js 也允许我们安装 npm 包。

因此尽管是一套看上去更为复杂的实现方案，但我们依然可以「站在巨人的肩膀上」合理地「偷懒」，在第三方开源包的帮助下节省编程时间。

### 创建 Auto.js 项目并安装开源包

在桌面端上与手机端的 Auto.js 建立连接之后我们就可以在 VS Code 上开始进行代码编写，关于如何在桌面端使用 Auto.js 的具体流程可以参考我上一篇文章，这里就不过多赘述。

因为我使用的是 Auto.js 的付费版本，所以在电脑上创建一个文件夹之后，点击 Auto.js Pro 的插件图标后并选择「创建 V9 API 项目」用以在新建的文件夹中添加相关文件，这也包括常见的 `package.json` 开源包管理文件。

所以初始化后的文件夹中包含如下内容：

```
timetracker
├── node_modules
├── main.js
├── package-lock.json
├── package.json
├── project.json
└── tsconfig.json


```

参考 Toggl API 文档给出的[参考文档](https://developers.track.toggl.com/docs/next/third_parties)，我们可以自由选择开源社区的不同编程语言的 Toggl API 版本。

![](https://cdn.sspai.com/editor/u_/cdlke6db34tcdb5tu4rg)

由于 Auto.js 用的是 JavaScript 编程语言，也就对应的是文档中的 Node.js 部分，所以我就选择了第一项名为 [toggl-track](https://github.com/garyhtou/toggl-track) 的第三方实现。

接下来我们需要在电脑端进行安装所选的第三方开源包，所以请确保你的当前操作系统中安装了 [Node.js 环境](https://nodejs.org/en/)，它会自带一个 `npm` 安装工具，接着我们切换到项目文件夹中，比如前面的 `timetracker`，然后运行如下命令完成安装步骤：

```
npm install --no-bin-links toggl-track


```

> 注：由于 npm 的服务器是在国外，为了加速下载可能需要我们配置一下国内镜像源地址，具体可参考 npmmirror 中国镜像站的[使用说明](https://npmmirror.com/)。

之后当我们在电脑上编写好代码之后，我们就可以再次点击 Auto.js 图标，并选择「保存项目到设备」一项，将当前文件夹的所有内容发送至手机，这样就能确保脚本代码能在手机上直接运行。每次点击该选项时桌面端文件夹中的内容都会**直接覆盖**手机端上的同名文件夹内容。

不过由于我们的自动计时脚本也是可以独立运行，在后续代码中我们只会用引用到安装包的内容，而不会用到 `main.js` 代码文件，让其保持默认即可。

### 封装与 Toggl API 交互的模块

虽然 toggl-track 封装了许多向 Toggl API 发送请求的功能函数，但出于个人需要我们可以再基于此进行简单地封装。

考虑到 Auto.js 仅仅只负责整个自动化流程的一部分，加之停止计时可能也会用到 Toggl API，所以我就额外单独封装了一个名为 `toggl.js` 的自用脚本模块方便后续被其他脚本所使用：

```
'nodejs';
const { Toggl } = require('toggl-track');

class TogglClient {
  constructor({ token = null } = {}) {
    if (!token) {
      throw new Error('invalid token');
    }

    this._toggl = new Toggl({
      auth: {
        token: token,
      },
    });
  }

  async _getWorkspaceId() {
    const resp = await this._toggl.me.get();
    return resp.default_workspace_id;
  }

  async start(
    name,
    { projectId = null, tags = null, workspace_id = null } = {}
  ) {
    if (!workspace_id) {
      workspace_id = await this._getWorkspaceId();
    }

    const currentTimeEntry = await this._toggl.timeEntry.current();
    if (currentTimeEntry && currentTimeEntry.description === name) {
      console.log('duplicated. time entry has started.');
      return;
    }

    let start = new Date();
    const body = {
      created_with: 'Autojs', // ID
      description: name, // Description
      workspace_id: workspace_id, // Workspace ID
      start: start.toISOString(), // Start date time
      duration: -Math.floor(start / 1000), // transform seconds
      project_id: projectId,
      tags: tags,
    };
    const resp = await this._toggl.timeEntry.create(workspace_id, body);
    if (typeof resp === 'string') {
      const err = JSON.stringify(resp);
      console.error(`something wrong when creating time entry, resp: ${err}`);
      return;
    }
    console.log(`time entry<name=${resp.description}>`);
  }

  async stop() {
    const currentTimeEntry = await this._toggl.timeEntry.current();
    if (!currentTimeEntry) {
      console.log("there isn't any time entry.");
      return;
    }

    const {
      id: entryId,
      description: name,
      workspace_id,
      at,
    } = currentTimeEntry;
    const start = new Date(at);
    const now = new Date();

    const body = {
      stop: now.toISOString(),
      duration: Math.floor((now - start) / 1000),
    };

    await this._toggl.timeEntry.update(entryId, workspace_id, body);
    console.log(`stop time entry <${name}>`);
  }
}

const defaultClient = new TogglClient({
  token: '<your-toggl-token>',
});
module.exports = {
  defaultClient,
  TogglClient,
};


```

上述虽然代码看起来很多，可对于有 JavaScript 编程经验的人来说可能已经「见码知意」，无需多言；但对于没有编程经验的读者而言我还是需要啰嗦几句。

简单来说，为了让代码能够运行，需要我们填入 Toggl 应用的授权 Token，之后每次在请求 API 时都会用到该授权的 Token。

那么如何获取 Toggl Token？很简单，我们只需要打开登录网页端的 Toggl 之后点击左下角的「Profile」头像部分，再选择「Profile Settings」，最后下拉至「API Token」处点击并复制即可。

![](https://cdn.sspai.com/editor/u_/cdlke6lb34tcd6q36fc0)

除此之外就是额外封装了两个方法 `start()` 和 `stop()` 用以应对开始计时和停止计时两个行为，二者的核心逻辑类似：

1.  首先判断是否 Toggl 已经正在计时，甚至计时的任务名称与当前的任务名称一致，那么就不会进行额外请求 API 的操作，仅仅只是输出一下日志提示即跳过；
2.  除此之外，就会按照 Toggl API 的官方要求将请求需要发送的数据进行包装并发送对应操作的请求。

紧接着，我们就可以新建脚本并引用封装好的内容。由于我已经事先基于自己的 Toggl 应用 Token 创建了一个 `defaultClient`，因此我就无需再传入一次 Token 而直接使用，比如我将开始计时的代码命名为 `startReader.js`，其内容如下：

```
'nodejs';
// --------------------
// Auto.js built-in
// --------------------

const { currentPackage } = require('accessibility');
const { getAppName } = require('app');
const { showToast } = require('toast');

// --------------------
// Internal
// --------------------

const { defaultClient } = require('./toggl');

// --------------------

(async () => {
  let packageName = currentPackage();
  let appName = getAppName(packageName);

  console.log(`${packageName}, ${appName}`);

  const READER_APP_NAMES = ['京东读书', '微信读书', 'Raindrop'];
  if (!READER_APP_NAMES.includes(appName)) {
    console.log(`${appName} isn't in target reader app list.`);
    return;
  }

  await defaultClient.start(appName, { projectId: '<your-project-id>' });
  showToast('开始时间记录');
})();


```

在这段代码中我还会使用到 Auto.js 内置的一些模块进行用于额外的判断逻辑辅助：我会先获取到当前前台的应用是否为我常用的几个阅读类应用，如果不是那么就简单输出一下提示信息则不做其他处理；反之，则调用前面封装好的 `start()` 方法开始计时。

其中的任务名称参数为应用名称，并且我还填入了自己通常用于记录阅读类任务的项目组 ID，你如果没有那么可以保持为空。

类似地，停止计时的脚本代码 `stopReader.js` 内容如下所示，但相比于开始计时的脚本来说我们则不需要额外的判断：

```
'nodejs';
// --------------------
// Auto.js built-in
// --------------------

const { showToast } = require('toast');

// --------------------
// Internal
// --------------------

const { defaultClient } = require('./toggl');

// --------------------

(async () => {
  await defaultClient.stop();
  showToast('结束记录时间');
})();


```

至此，我们基本上已经完成了 Auto.js 的部分，现在只需要为其添加相应的触发机制即可，此时 `timetracker` 文件夹的内容又丰富了不少：

```
timetracker
├── main.js
├── node_modules
├── package-lock.json
├── package.json
├── project.json
├── startReader.js
├── stopReader.js
├── toggl.js
└── tsconfig.json


```

然后再次通过「保存项目到设备」选项来确保手机端上的代码是最新版本。

不过由于 Auto.js 中条件触发相关的 API 较为稀缺，因此我就借助了 MacroDroid 来补齐最后一块短板。

使用 MacroDroid 添加触发条件
--------------------

在 MacroDroid 中我们需要新建两个宏分别调用开始计时与停止计时的脚本，这里的宏就相当于我们的自动化流程集合，所有操作都会放到一个宏之中进行管理。

因为开始计时与停止计时的行为逻辑基本一致，所以本小节仅以开始计时为例而不再赘述停止计时的宏创建过程。

进入到 MacroDroid 主页之后我们可以点击选项卡中的「添加宏」模块来创建宏。在 MacroDroid 的宏界面里，除了宏名称之外，我们只需要分别对「触发器」和「动作」两个选项进行设置即可完成宏的创建。

![](https://cdn.sspai.com/editor/u_/cdlke6tb34tcd6q36fcg)

点击触发器区域右上角的加号后，我们选择「应用程序」一项，然后再点击「应用打开 / 关闭」并选择「应用打开」的选项并确定，之后我们再选择「选择应用」一项来根据名称选择则目标应用，选择完毕即可点击确认进而完成触发器的设置并回到宏界面。

![](https://cdn.sspai.com/editor/u_/cdlke75b34tcdtg9f30g)

紧接着再以类似的操作设置「动作」。具体而言就是：同样找到「应用程序」一项，然后点击「Tasker / 本地插件」选项，找到并选择 Auto.js 的插件，之后根据 Auto.js 默认的脚本存储路径（默认为系统文件夹下的「脚本」文件夹）找到对应的脚本。

![](https://cdn.sspai.com/editor/u_/cdlke7db34tcdb5tu4s0)

完成以上步骤后我们就可以点击宏界面右下角的按钮对其进行保存，保存的宏将会在 MacroDroid 的「宏」选项卡中展示（默认为「未分类」组），之后我们确保该宏处于启动状态即可。

![](https://cdn.sspai.com/editor/u_/cdlke7lb34tcdb5tu4sg)

当然最后还要记得为 MacroDroid 加上对应的无障碍权限、锁定后台以及关闭电池优化等设置，避免 MacroDroid 进程被杀掉。

尾巴
--

以上步骤完成后，就可以宣告我们的自动化流程大功告成，最终效果我们在开头已经展示过了，现在你可以再跳回去看看。

不过在我实际的多次使用中，发现 MacroDroid 的触发器机制可能就比较简单粗暴，会出现多次短暂计时的情况。如果我切出并挂起应用时，会触发 MacroDroid 的「应用关闭」导致直接停止计时；类似地，当我从后台唤醒应用时也会触发 MacroDroid 的「应用打开」并调用开始计时脚本。

可从某个角度来看似乎也合理，因为当我们切出当前应用时也说明我们此时并不是真正地在阅读或使用该应用，而重新唤醒并进入到应用则说明我们又开始使用，应当重新开始计时。

所以这看似「Bug」的「Feature」也让我更加专注于阅读，而不容易为其他无关紧要的消息通知所分神。

> 下载 [少数派 2.0 客户端](https://sspai.com/page/client)、关注 [少数派公众号](https://sspai.com/s/J71e)，解锁全新阅读体验 📰

> 实用、好用的 [正版软件](https://sspai.com/mall)，少数派为你呈现 🚀