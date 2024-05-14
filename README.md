源代码
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Play/Pause Button</title>
<style>
    /* 播放/暂停按钮的样式 */
    #playPauseButton {
        position: fixed; /* 固定在页面上 */
        bottom: 20px; /* 距离底部20px */
        right: 20px; /* 距离右侧20px */
        width: 60px; /* 宽度60px */
        height: 60px; /* 高度60px */
        border-radius: 50%; /* 边框圆角50%（使按钮呈现圆形） */
        background-color: transparent; /* 背景透明 */
        border: 2px solid #fff; /* 边框白色，2px粗细 */
        cursor: pointer; /* 鼠标指针样式为手型 */
        transition: transform 0.3s ease; /* 按钮变换效果，0.3秒 */
        overflow: hidden; /* 内容溢出时隐藏 */
        z-index: 9999; /* 层级置顶 */
    }
    /* 播放/暂停按钮内部图片的样式 */
    #playPauseButton img {
        width: 100%; /* 图片宽度100% */
        height: 100%; /* 图片高度100% */
        object-fit: cover; /* 图片适应容器，保持宽高比，不留空白 */
        /* 图片旋转动画，2秒完成一次旋转，线性动画，无限循环，初始状态为暂停 */
        animation: rotateAlbum 2s linear infinite paused;
    }
    /* 当按钮处于播放状态时，激活旋转动画 */
    #playPauseButton.playing img {
        animation-play-state: running;
    }
    /* 图片旋转动画定义 */
    @keyframes rotateAlbum {
        to {
            transform: rotate(360deg); /* 图片从0度旋转到360度 */
        }
    }
</style>
</head>
<body>

<!-- 音频元素，自动播放 -->
<audio id="myAudio" autoplay>
    <source src="music.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>

<!-- 播放/暂停按钮，初始状态为播放 -->
<button id="playPauseButton" class="playing" onclick="togglePlayPause()">
    <img src="album_cover.jpg" alt="Album Cover"> <!-- 按钮内部图片，显示专辑封面 -->
</button>

<!-- JavaScript代码 -->
<script>
    // 获取音频元素和按钮元素
    var audio = document.getElementById("myAudio");
    var playPauseButton = document.getElementById("playPauseButton");

    // 播放/暂停切换函数
    function togglePlayPause() {
        if (audio.paused) { // 如果音频暂停
            audio.play(); // 播放音频
            playPauseButton.classList.add("playing"); // 按钮状态改为播放
        } else { // 如果音频正在播放
            audio.pause(); // 暂停音频
            playPauseButton.classList.remove("playing"); // 按钮状态改为暂停
        }
    }
</script>

</body>
</html>
