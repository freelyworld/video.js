![Video.js logo][logo]

# [Video.js - HTML5 Video Player][vjs]

[![Build Status][travis-icon]][travis-link]
[![Coverage Status][coveralls-icon]][coveralls-link]
[![Greenkeeper badge](https://badges.greenkeeper.io/videojs/video.js.svg)](https://greenkeeper.io/)
[![Slack Status][slack-icon]][slack-link]

[![NPM][npm-icon]][npm-link]

> Video.js is a web video player built from the ground up for an HTML5 world. It supports HTML5 video and Media Source Extensions, as well as other playback techs like YouTube and Vimeo (through [plugins][plugins]). It supports video playback on desktops and mobile devices. This project was started mid 2010, and the player is now used on over ~~50,000~~ ~~100,000~~ ~~200,000~~ ~~400,000~~ [600,000 websites][builtwith].

## Table of Contents

* [Quick Start](#quick-start)
* [Contributing](#contributing)
* [Code of Conduct](#code-of-conduct)
* [License](#license)

## Quick Start

Thanks to the awesome folks over at [Fastly][fastly], there's a free, CDN hosted version of Video.js that anyone can use. Add these tags to your document's `<head>`:

```html
<link href="//vjs.zencdn.net/7.10.2/video-js.min.css" rel="stylesheet">
<script src="//vjs.zencdn.net/7.10.2/video.min.js"></script>
```

> For the latest version of video.js and URLs to use, check out the [Getting Started][getting-started] page on our website.

Video.js version 7 (and newer) CDN builds do not send any data to Google Analytics.

In older versions of Video.js (6 and earlier), in the `vjs.zencdn.net` CDN-hosted versions we include a [stripped down Google Analytics pixel](https://github.com/videojs/cdn/blob/master/src/analytics.js) that tracks a random sampling (currently 1%) of players loaded from the CDN. This allows us to see (roughly) what browsers are in use in the wild, along with other useful metrics such as OS and device. If you'd like to disable analytics, you can simply include the following global before including Video.js via the free CDN:

```html
<script>window.HELP_IMPROVE_VIDEOJS = false;</script>
```

Alternatively, you can include Video.js by getting it from [npm](https://videojs.com/getting-started/#install-via-npm), downloading from [GitHub releases](https://github.com/videojs/video.js/releases) or by including it via [unpkg](https://unpkg.com) or another JavaScript CDN like CDNjs. These releases _do not_ include Google Analytics tracking at all.

```html
<!-- unpkg : use the latest version of Video.js -->
<link href="https://unpkg.com/video.js/dist/video-js.min.css" rel="stylesheet">
<script src="https://unpkg.com/video.js/dist/video.min.js"></script>

<!-- unpkg : use a specific version of Video.js (change the version numbers as necessary) -->
<link href="https://unpkg.com/video.js@7.10.2/dist/video-js.min.css" rel="stylesheet">
<script src="https://unpkg.com/video.js@7.10.2/dist/video.min.js"></script>

<!-- cdnjs : use a specific version of Video.js (change the version numbers as necessary) -->
<link href="https://cdnjs.cloudflare.com/ajax/libs/video.js/7.10.2/video-js.min.css" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/video.js/7.10.2/video.min.js"></script>
```

Next, using Video.js is as simple as creating a `<video>` element, but with an additional `data-setup` attribute. At a minimum, this attribute must have a value of `'{}'`, but it can include any Video.js [options][options] - just make sure it contains valid JSON!

```html
<video
    id="my-player"
    class="video-js"
    controls
    preload="auto"
    poster="//vjs.zencdn.net/v/oceans.png"
    data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4"></source>
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm"></source>
  <source src="//vjs.zencdn.net/v/oceans.ogv" type="video/ogg"></source>
  <p class="vjs-no-js">
    To view this video please enable JavaScript, and consider upgrading to a
    web browser that
    <a href="https://videojs.com/html5-video-support/" target="_blank">
      supports HTML5 video
    </a>
  </p>
</video>
```

When the page loads, Video.js will find this element and automatically setup a player in its place.

If you don't want to use automatic setup, you can leave off the `data-setup` attribute and initialize a `<video>` element manually using the `videojs` function:

```js
var player = videojs('my-player');
```

The `videojs` function also accepts an `options` object and a callback to be invoked
 when the player is ready:

```js
var options = {};

var player = videojs('my-player', options, function onPlayerReady() {
  videojs.log('Your player is ready!');

  // In this context, `this` is the player that was created by Video.js.
  this.play();

  // How about an event listener?
  this.on('ended', function() {
    videojs.log('Awww...over so soon?!');
  });
});
```

If you're ready to dive in, the [Getting Started][getting-started] page and [documentation][docs] are the best places to go for more information. If you get stuck, head over to our [Slack channel][slack-link]!

## Contributing

Video.js is a free and open source library, and we appreciate any help you're willing to give - whether it's fixing bugs, improving documentation, or suggesting new features. Check out the [contributing guide][contributing] for more!

_Video.js uses [BrowserStack][browserstack] for compatibility testing._

## [Code of Conduct][coc]

Please note that this project is released with a [Contributor Code of Conduct][coc]. By participating in this project you agree to abide by its terms.

## [License][license]

Video.js is [licensed][license] under the Apache License, Version 2.0.

[browserstack]: https://browserstack.com

[builtwith]: https://trends.builtwith.com/media/VideoJS

[contributing]: CONTRIBUTING.md

[coveralls-icon]: https://coveralls.io/repos/github/videojs/video.js/badge.svg?branch=main

[coveralls-link]: https://coveralls.io/github/videojs/video.js?branch=main

[docs]: https://docs.videojs.com

[fastly]: https://www.fastly.com/

[getting-started]: https://videojs.com/getting-started/

[license]: LICENSE

[logo]: https://videojs.com/logo-white.png

[npm-icon]: https://nodei.co/npm/video.js.png?downloads=true&downloadRank=true

[npm-link]: https://nodei.co/npm/video.js/

[options]: docs/guides/options.md

[plugins]: https://videojs.com/plugins/

[slack-icon]: http://slack.videojs.com/badge.svg

[slack-link]: http://slack.videojs.com

[travis-icon]: https://travis-ci.org/videojs/video.js.svg?branch=main

[travis-link]: https://travis-ci.org/videojs/video.js

[vjs]: https://videojs.com

[coc]: CODE_OF_CONDUCT.md

	/*
		常用方法
		播放：myPlayer.play();
		暂停：myPlayer.pause();
		获取播放进度：var whereYouAt = myPlayer.currentTime();
		设置播放进度：myPlayer.currentTime(120);
		视频持续时间，加载完成视频才可以知道视频时长，且在flash情况下无效: var howLongIsThis = myPlayer.duration();
		缓冲，就是返回下载了多少: `var whatHasBeenBuffered = myPlayer.buffered();
		百分比的缓冲: var howMuchIsDownloaded = myPlayer.bufferedPercent();
		声音大小（0-1之间）: var howLoudIsIt = myPlayer.volume();
		设置声音大小: myPlayer.volume(0.5);
		取得视频的宽度: var howWideIsIt = myPlayer.width();
		设置宽度：myPlayer.width(640);
		获取高度: var howTallIsIt = myPlayer.height();
		设置高度：: myPlayer.height(480);
		一步到位的设置大小：myPlayer.size(640,480);
		全屏: myPlayer.enterFullScreen();
		离开全屏 : myPlayer.enterFullScreen();
		(4)、网络状态
		myPlayer.currentSrc; //返回当前资源的URL
		myPlayer.src = value; //返回或设置当前资源的URL
		myPlayer.canPlayType(type); //是否能播放某种格式的资源
		myPlayer.networkState; //0.此元素未初始化 1.正常但没有使用网络 2.正在下载数据 3.没有找到资源
		myPlayer.load(); //重新加载src指定的资源
		myPlayer.buffered; //返回已缓冲区域，TimeRanges
		myPlayer.preload; //none:不预载 metadata:预载资源信息 auto:立即加载视频
		(5)、播放状态
    myPlayer.currentTime = value; //当前播放的位置，赋值可改变位置
    myPlayer.startTime; //一般为0，如果为流媒体或者不从0开始的资源，则不为0
    myPlayer.duration; //当前资源长度 流返回无限
    myPlayer.paused; //是否暂停
    myPlayer.defaultPlaybackRate = value;//默认的回放速度，可以设置
    myPlayer.playbackRate = value;//当前播放速度，设置后马上改变
    myPlayer.played; //返回已经播放的区域，TimeRanges，关于此对象见下文
    myPlayer.seekable; //返回可以seek的区域 TimeRanges
    myPlayer.ended; //是否结束
    myPlayer.autoPlay; //是否自动播放
    myPlayer.loop; //是否循环播放
		(6)、视频控制
    myPlayer.controls;//是否有默认控制条
    myPlayer.volume = value; //音量
    myPlayer.muted = value; //静音
    TimeRanges(区域)对象
    TimeRanges.length; //区域段数
    TimeRanges.start(index) //第index段区域的开始位置
    TimeRanges.end(index) //第index段区域的结束位置
		*/
    
    createVideoplayer(){
				var player = videojs(document.getElementById('videoplayer'), {
				  controls: true, // 是否显示控制条
				  poster: 'https://qn.leadership.dv.zhizunweb.com/media/test.jpg', // 视频封面图地址
				  preload: 'auto',
				  autoplay: false,
				  fluid: true, // 自适应宽高
				  language: 'zh-CN', // 设置语言
				  muted: false, // 是否静音
				  inactivityTimeout: false,
				  controlBar: { // 设置控制条组件
				    /* 设置控制条里面组件的相关属性及显示与否
				    'currentTimeDisplay':true,
				    'timeDivider':true,
				    'durationDisplay':true,
				    'remainingTimeDisplay':false,
				    volumePanel: {
				      inline: false,
				    }
				    */
				    /* 使用children的形式可以控制每一个控件的位置，以及显示与否 * /
				    children: [
				      {name: 'playToggle'}, // 播放按钮
				      {name: 'currentTimeDisplay'}, // 当前已播放时间
				      {name: 'progressControl'}, // 播放进度条
				      {name: 'durationDisplay'}, // 总时间
				      { // 倍数播放
				        name: 'playbackRateMenuButton',
				        'playbackRates': playbackRates
				      },
				      {
				        name: 'volumePanel', // 音量控制
				        inline: false, // 不使用水平方式
				      },
				      {name: 'FullscreenToggle'} // 全屏
				    ]
				  },
				  sources:[ // 视频源
				      {
								type: 'video/mp4',
				        src: 'https://qn.leadership.dv.zhizunweb.com/media/test.mp4',
				        poster: 'https://qn.leadership.dv.zhizunweb.com/media/test.jpg'
				      }
				  ]
				}, function (){
				  console.log('视频可以播放了',this);
				});
			}
