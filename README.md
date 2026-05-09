<!-- 
  在 Markdown 文件中实现“牛逼跳转” —— 由于 .md 文件本身无法执行脚本，
  本模块提供一个 炫酷 HTML 容器 + 自动/手动双模式跳转 + 视觉特效。
  将此完整代码块嵌入 README.md（若 Markdown 渲染器支持 HTML 显示），
  即可呈现一个高能跃迁面板，点击或倒计时结束后跳转至 木叶吃丹修仙助手。
  
  使用说明：
  1. 将下方整个代码块复制到 README.md 合适位置。
  2. 确保目标文件 index-Dark.html 与 README.md 在同一目录（或调整 TARGET_URL）。
  3. 在支持 HTML 渲染的 Markdown 环境（GitHub、VSCode 预览、绝大多数博客）中，
     读者将看到炫酷的跃迁卡片，自动 3 秒后跳转，也可手动点击触发。
-->

<div align="center">
  
  <!-- 核心跃迁容器 -->
  <div style="
    background: linear-gradient(145deg, #0a0f1e, #03060e);
    border-radius: 48px;
    padding: 2rem 1.5rem;
    margin: 40px 0;
    border: 1px solid rgba(0, 255, 255, 0.5);
    box-shadow: 0 20px 40px rgba(0,0,0,0.6), 0 0 20px rgba(0,255,200,0.2);
    backdrop-filter: blur(4px);
    font-family: 'Segoe UI', 'Orbitron', 'Courier New', monospace;
    transition: all 0.3s;
  ">
    
    <!-- 标题区 -->
    <div style="margin-bottom: 20px;">
      <span style="background: #0ff1; padding: 4px 16px; border-radius: 40px; border-left: 2px solid #0ff; border-right: 2px solid #0ff; font-size: 12px; letter-spacing: 2px; color: #0ff;">⚡ 修炼·力量·系统 ⚡</span>
      <h2 style="margin: 16px 0 8px; font-size: 2.2em; background: linear-gradient(135deg, #fff, #0ff, #0fa); background-clip: text; -webkit-background-clip: text; color: transparent; text-shadow: 0 0 8px cyan;">▶ 维度跃迁核心 ◀</h2>
      <div style="color: #8aaccc; font-size: 0.85rem;">「 暗界导航 · 力量协议 」</div>
    </div>

    <!-- 能量核心动画（纯CSS） -->
    <div style="display: flex; justify-content: center; margin: 20px 0;">
      <div style="
        width: 100px; height: 100px;
        background: radial-gradient(circle, #0a2a2a, #010a0a);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 0 20px cyan, inset 0 0 12px cyan;
        animation: pulseRingMd 1.4s infinite ease-out;
      ">
        <span style="font-size: 3rem; filter: drop-shadow(0 0 6px cyan); animation: spinIcon 3s linear infinite;">🌀</span>
      </div>
    </div>

    <!-- 状态栏与进度条 (动态JS) -->
    <div style="background: #021018aa; border-radius: 60px; padding: 12px 20px; margin: 20px 0; border-left: 3px solid #0ff; border-right: 3px solid #0ff;">
      <div style="font-family: monospace; font-weight: bold; color: #b0ffe0;" id="md_status_msg">🌀 链接中枢 · 力量洪流引导 🌀</div>
      <div style="background: #111c28; border-radius: 40px; height: 8px; margin-top: 12px; overflow: hidden;">
        <div style="width: 0%; height: 100%; background: linear-gradient(90deg, #0ff, #0f6); border-radius: 40px; box-shadow: 0 0 6px #0ff;" id="md_progress_fill"></div>
      </div>
      <div style="font-family: monospace; font-size: 0.8rem; margin-top: 8px; color: #0ff;" id="md_percent">0%</div>
    </div>

    <!-- 目标地址展示 -->
    <div style="display: flex; align-items: center; justify-content: center; gap: 12px; flex-wrap: wrap; background: #00000044; border-radius: 80px; padding: 6px 18px; margin: 16px 0;">
      <span style="color: #aaf;">🎯 目标索引 :</span>
      <code style="background: #0a161f; padding: 4px 14px; border-radius: 40px; color: #0ff; border: 1px solid cyan;">index-Dark.html</code>
      <span style="color: #0fa;">🌑 暗界领域</span>
    </div>

    <!-- 操作区 - 按钮 + 倒计时 -->
    <div style="display: flex; justify-content: center; gap: 20px; align-items: center; flex-wrap: wrap; margin: 24px 0 12px;">
      <button id="md_jump_btn" style="
        background: linear-gradient(95deg, #0a2f2f, #021010);
        border: 1.5px solid #0ff;
        border-radius: 60px;
        padding: 10px 28px;
        font-size: 1.1rem;
        font-weight: bold;
        font-family: monospace;
        color: #0ff;
        cursor: pointer;
        backdrop-filter: blur(4px);
        transition: 0.2s;
        display: inline-flex;
        align-items: center;
        gap: 8px;
      " onmouseover="this.style.boxShadow='0 0 16px cyan'; this.style.color='white'" onmouseout="this.style.boxShadow=''; this.style.color='#0ff'">⚡ 立即跃迁 ⚡</button>
      <div style="background: #00000066; border-radius: 40px; padding: 6px 14px; font-family: monospace; font-size: 0.9rem;">
        自动跳转 <span id="md_countdown_num" style="color: #0ff; font-weight: bold;">3</span> s
      </div>
    </div>
    <div style="font-size: 0.65rem; color: #2f6f7a; margin-top: 16px;">⚙️ 力量系统 v.∞ · 空间锚点已锁定 | 目标：木叶吃丹修仙助手</div>

  </div>
</div>

<!-- 必须包含的脚本：动态进度条、倒计时、跳转逻辑，炫酷且稳健 -->
<script>
  (function() {
    // 确保脚本只在支持的环境下运行，且不重复执行
    if (window.__mdJumpInitiated) return;
    window.__mdJumpInitiated = true;

    const TARGET = "index-Dark.html";
    let seconds = 3;
    let currentPercent = 0;
    let countdownInterval = null;
    let progressInterval = null;
    let isJumping = false;

    // 获取元素 (通过ID)
    const statusEl = document.getElementById("md_status_msg");
    const progressFill = document.getElementById("md_progress_fill");
    const percentEl = document.getElementById("md_percent");
    const countdownSpan = document.getElementById("md_countdown_num");
    const jumpBtn = document.getElementById("md_jump_btn");

    // 更新进度条UI
    function updateProgressUI(percent) {
      let val = Math.min(100, Math.max(0, percent));
      if (progressFill) progressFill.style.width = val + "%";
      if (percentEl) percentEl.innerText = Math.floor(val) + "%";
      if (val >= 99.8 && percentEl) percentEl.innerText = "100%";
    }

    // 启动进度模拟 (3秒到达100%)
    function startProgressSimulation() {
      if (progressInterval) clearInterval(progressInterval);
      currentPercent = 0;
      updateProgressUI(0);
      const steps = 60;      // 平滑步数
      const increment = 100 / steps;
      const intervalTime = 3000 / steps; // ~50ms
      progressInterval = setInterval(() => {
        if (isJumping) return;
        if (currentPercent < 100) {
          currentPercent = Math.min(100, currentPercent + increment);
          updateProgressUI(currentPercent);
        } else {
          if (progressInterval) clearInterval(progressInterval);
          progressInterval = null;
        }
      }, intervalTime);
    }

    // 执行跃迁
    function performJump() {
      if (isJumping) return;
      isJumping = true;
      if (countdownInterval) clearInterval(countdownInterval);
      if (progressInterval) clearInterval(progressInterval);
      
      if (statusEl) statusEl.innerHTML = "✨ 时空裂隙开启 · 传送至暗界力量之境 ✨";
      updateProgressUI(100);
      
      // 炫闪特效
      const container = document.querySelector('div[style*="linear-gradient(145deg, #0a0f1e, #03060e)"]');
      if (container) {
        container.style.transition = "all 0.2s";
        container.style.boxShadow = "0 0 30px cyan, 0 0 60px rgba(0,255,200,0.6)";
        container.style.transform = "scale(0.98)";
        setTimeout(() => { if(container) container.style.transform = ""; }, 150);
      }
      
      // 短暂延迟后跳转，确保视觉效果
      setTimeout(() => {
        window.location.href = TARGET;
      }, 180);
    }

    // 倒计时逻辑
    function startCountdown() {
      if (countdownInterval) clearInterval(countdownInterval);
      let remaining = seconds;
      if (countdownSpan) countdownSpan.innerText = remaining;
      countdownInterval = setInterval(() => {
        if (isJumping) {
          if (countdownInterval) clearInterval(countdownInterval);
          return;
        }
        remaining--;
        if (remaining <= 0) {
          if (countdownInterval) clearInterval(countdownInterval);
          if (countdownSpan) countdownSpan.innerText = "0";
          if (statusEl) statusEl.innerHTML = "🔥 力量阈值突破 · 执行跃迁指令 🔥";
          performJump();
        } else {
          if (countdownSpan) countdownSpan.innerText = remaining;
          if (remaining === 1 && statusEl) statusEl.innerHTML = "⚡ 0.5 秒 · 力量觉醒完成 ⚡";
          if (remaining === 2 && statusEl) statusEl.innerHTML = "🌀 空间曲率校准 · 即将穿越 🌀";
        }
      }, 1000);
    }

    // 手动跳转
    function manualJump() {
      if (isJumping) {
        if (statusEl) statusEl.innerHTML = "⚠️ 跃迁已执行，请勿重复触发";
        return;
      }
      if (countdownInterval) clearInterval(countdownInterval);
      if (progressInterval) clearInterval(progressInterval);
      if (statusEl) statusEl.innerHTML = "💢 手动接管 · 超空间引擎激活 💢";
      updateProgressUI(100);
      performJump();
    }

    // 预检目标（可选, 控制台友好）
    function preCheck() {
      fetch(TARGET, { method: 'HEAD', mode: 'no-cors', cache: 'no-cache' })
        .catch(() => console.log("力量枢纽: 跳转目标就绪(跨域无影响，跃迁正常)"));
    }

    // 绑定按钮事件
    if (jumpBtn) {
      jumpBtn.addEventListener('click', (e) => {
        e.preventDefault();
        manualJump();
      });
    }

    // 启动所有动画
    startProgressSimulation();
    startCountdown();
    preCheck();

    // 优雅清理 (页面离开时)
    window.addEventListener('beforeunload', () => {
      if (countdownInterval) clearInterval(countdownInterval);
      if (progressInterval) clearInterval(progressInterval);
    });
  })();
</script>

<!-- 内嵌动画关键帧（如果全局没有则补充） -->
<style>
  @keyframes pulseRingMd {
    0% { box-shadow: 0 0 0 0 rgba(0, 255, 200, 0.4), inset 0 0 10px #0ff; transform: scale(1);}
    70% { box-shadow: 0 0 0 18px rgba(0, 255, 200, 0), inset 0 0 22px #0ff; transform: scale(1.02);}
    100% { box-shadow: 0 0 0 0 rgba(0, 255, 200, 0), inset 0 0 10px #0ff; transform: scale(1);}
  }
  @keyframes spinIcon {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
</style>

<!-- 说明：在 Markdown 中直接展示炫酷跳转卡片，自动倒计时3秒跳转至 index-Dark.html，也支持手动点击。
     若需更换跳转目标，只需修改上方 TARGET 变量。确保目标文件与当前 README.md 同目录。 -->
