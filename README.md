<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>力量觉醒 · 系统跳转中</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none; /* 提升科幻感，防止选中文字 */
        }

        body {
            min-height: 100vh;
            background: radial-gradient(circle at 20% 30%, #0a0f1e, #03050b);
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Segoe UI', 'Poppins', 'Orbitron', 'Courier New', monospace;
            overflow: hidden;
            position: relative;
            cursor: default;
        }

        /* 动态数据流背景 */
        .matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            opacity: 0.2;
            pointer-events: none;
            background: repeating-linear-gradient(0deg, 
                rgba(0, 255, 196, 0.08) 0px, 
                rgba(0, 255, 196, 0.08) 1px,
                transparent 1px,
                transparent 12px);
            animation: scanlines 8s linear infinite;
        }

        @keyframes scanlines {
            0% { background-position: 0 0; }
            100% { background-position: 0 20px; }
        }

        /* 核心跳转卡片 */
        .gateway-container {
            position: relative;
            z-index: 10;
            width: 90%;
            max-width: 700px;
            background: rgba(8, 12, 25, 0.65);
            backdrop-filter: blur(18px);
            border-radius: 48px;
            border: 1px solid rgba(0, 255, 255, 0.4);
            box-shadow: 0 25px 45px rgba(0,0,0,0.5), 0 0 0 2px rgba(0, 255, 255, 0.1) inset, 0 0 30px rgba(0, 210, 255, 0.3);
            padding: 2rem 2rem 2.8rem;
            transition: all 0.3s ease;
            animation: floatGlow 3s infinite alternate;
        }

        @keyframes floatGlow {
            0% {
                box-shadow: 0 25px 45px rgba(0,0,0,0.5), 0 0 0 2px rgba(0, 255, 255, 0.2) inset, 0 0 20px rgba(0, 210, 255, 0.2);
                transform: translateY(0px);
            }
            100% {
                box-shadow: 0 35px 55px rgba(0,0,0,0.7), 0 0 0 3px rgba(0, 255, 255, 0.6) inset, 0 0 40px rgba(0, 230, 255, 0.5);
                transform: translateY(-6px);
            }
        }

        /* 头标 + 力量系统 */
        .system-header {
            text-align: center;
            margin-bottom: 2rem;
        }
        .badge {
            display: inline-block;
            background: rgba(0, 20, 30, 0.7);
            backdrop-filter: blur(4px);
            padding: 0.3rem 1rem;
            border-radius: 60px;
            font-size: 0.75rem;
            letter-spacing: 3px;
            font-weight: 600;
            color: #0ff;
            border: 1px solid #0ff;
            text-transform: uppercase;
            font-family: 'Orbitron', monospace;
            box-shadow: 0 0 8px cyan;
            margin-bottom: 1rem;
        }
        h1 {
            font-size: 3.4rem;
            font-weight: 800;
            background: linear-gradient(135deg, #ffffff, #0fffc0, #00a6ff);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            text-shadow: 0 0 12px rgba(0,255,200,0.3);
            letter-spacing: 2px;
            word-break: keep-all;
        }
        .sub {
            color: #bbf0ff;
            font-family: monospace;
            font-size: 0.95rem;
            background: #00000040;
            display: inline-block;
            padding: 0.2rem 1rem;
            border-radius: 40px;
            backdrop-filter: blur(2px);
            margin-top: 0.5rem;
        }

        /* 中枢核心圆环 */
        .nexus-core {
            display: flex;
            justify-content: center;
            margin: 2rem 0;
            position: relative;
        }
        .energy-ring {
            width: 130px;
            height: 130px;
            border-radius: 50%;
            background: radial-gradient(circle, #0a2a2a, #021010);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            box-shadow: 0 0 30px rgba(0, 255, 200, 0.5), inset 0 0 20px rgba(0,255,200,0.3);
            animation: pulseRing 1.6s infinite ease-out;
        }
        .energy-ring::before {
            content: "";
            position: absolute;
            top: -8px;
            left: -8px;
            right: -8px;
            bottom: -8px;
            border-radius: 50%;
            border: 2px solid rgba(0, 255, 210, 0.5);
            animation: spin 3s linear infinite;
            pointer-events: none;
        }
        .energy-ring::after {
            content: "";
            position: absolute;
            top: -16px;
            left: -16px;
            right: -16px;
            bottom: -16px;
            border-radius: 50%;
            border: 1px dashed rgba(0, 255, 200, 0.4);
            animation: spin 5s reverse linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        @keyframes pulseRing {
            0% { box-shadow: 0 0 0 0 rgba(0, 255, 200, 0.4), inset 0 0 10px #0ff; transform: scale(1);}
            70% { box-shadow: 0 0 0 20px rgba(0, 255, 200, 0), inset 0 0 25px #0ff; transform: scale(1.02);}
            100% { box-shadow: 0 0 0 0 rgba(0, 255, 200, 0), inset 0 0 10px #0ff; transform: scale(1);}
        }
        .core-icon {
            font-size: 3.8rem;
            filter: drop-shadow(0 0 10px cyan);
            animation: iconBreathing 2s infinite alternate;
        }
        @keyframes iconBreathing {
            0% { transform: scale(0.92); opacity: 0.9; text-shadow: 0 0 2px cyan;}
            100% { transform: scale(1.08); opacity: 1; text-shadow: 0 0 20px cyan;}
        }

        /* 状态栏 */
        .transfer-status {
            background: #021018b3;
            border-radius: 60px;
            padding: 1rem 1.5rem;
            margin: 1.8rem 0 1rem;
            text-align: center;
            border-left: 5px solid #0ff;
            border-right: 5px solid #0ff;
            backdrop-filter: blur(8px);
        }
        .status-text {
            font-family: 'Courier New', monospace;
            font-weight: bold;
            font-size: 1.2rem;
            color: #b0ffe0;
            letter-spacing: 1px;
        }
        .loading-bar {
            margin-top: 12px;
            background: #111c28;
            border-radius: 40px;
            height: 6px;
            overflow: hidden;
            width: 100%;
            position: relative;
            box-shadow: inset 0 1px 3px #00000055;
        }
        .fill-bar {
            width: 0%;
            height: 100%;
            background: linear-gradient(90deg, #0ff, #0f6, #0ff);
            border-radius: 40px;
            box-shadow: 0 0 8px #0ff;
            transition: width 0.08s linear;
        }
        .progress-percent {
            font-size: 0.9rem;
            font-family: monospace;
            margin-top: 8px;
            color: #0ff;
            font-weight: bold;
        }

        /* 目标地址 */
        .target-hint {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            background: #00000055;
            border-radius: 80px;
            padding: 0.6rem 1.5rem;
            margin: 20px 0;
            font-size: 0.8rem;
            flex-wrap: wrap;
            border: 1px solid rgba(0, 255, 200, 0.3);
        }
        .target-label {
            color: #8aaec0;
        }
        .target-path {
            font-weight: bold;
            background: #0a161f;
            padding: 5px 15px;
            border-radius: 40px;
            color: #0ff;
            font-family: monospace;
            letter-spacing: 1px;
            word-break: break-all;
            border: 1px solid cyan;
        }
        .dest-badge {
            font-size: 1.2rem;
        }

        /* 倒计时/手动触发区 */
        .action-area {
            display: flex;
            justify-content: center;
            margin: 1.5rem 0 0.5rem;
        }
        .jump-button {
            background: linear-gradient(95deg, #0a2f2f, #021010);
            border: 1.5px solid #0ff;
            border-radius: 60px;
            padding: 12px 32px;
            font-size: 1.2rem;
            font-weight: bold;
            font-family: 'Orbitron', monospace;
            color: #0ff;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 0 10px rgba(0,255,255,0.3);
            backdrop-filter: blur(8px);
            letter-spacing: 2px;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .jump-button:hover {
            background: radial-gradient(circle, #0ff3, #000);
            color: white;
            box-shadow: 0 0 20px cyan;
            transform: scale(1.02);
            border-color: white;
        }
        .jump-button:active {
            transform: scale(0.98);
        }
        .countdown-tip {
            font-family: monospace;
            background: #00000080;
            border-radius: 30px;
            padding: 5px 12px;
            font-size: 1rem;
        }
        .force-link {
            margin-left: 20px;
            background: transparent;
            border: 1px solid cyan;
            padding: 5px 12px;
            border-radius: 40px;
            font-size: 0.7rem;
            cursor: pointer;
            transition: 0.2s;
        }
        .force-link:hover {
            background: cyan;
            color: black;
        }

        footer {
            text-align: center;
            margin-top: 2rem;
            font-size: 0.7rem;
            color: #3f6f7f;
            font-family: monospace;
        }

        /* 闪烁光晕 */
        .glow-text {
            animation: textPulse 1.2s infinite;
        }
        @keyframes textPulse {
            0% { text-shadow: 0 0 2px cyan; opacity: 0.8;}
            100% { text-shadow: 0 0 12px cyan; opacity: 1;}
        }

        @media (max-width: 550px) {
            .gateway-container { padding: 1.2rem; }
            h1 { font-size: 2rem; }
            .energy-ring { width: 90px; height: 90px; }
            .core-icon { font-size: 2.6rem; }
        }
    </style>
</head>
<body>
<div class="matrix-bg"></div>

<div class="gateway-container">
    <div class="system-header">
        <div class="badge">⚡ 修炼 · 力量 · 系统 ⚡</div>
        <h1>▶ 维度跃迁 ◀</h1>
        <div class="sub">「 核心协议 · 暗界导航 」</div>
    </div>

    <div class="nexus-core">
        <div class="energy-ring">
            <div class="core-icon">🌀</div>
        </div>
    </div>

    <div class="transfer-status">
        <div class="status-text" id="statusMessage">⚡ 链接中枢 · 引导力量洪流 ⚡</div>
        <div class="loading-bar">
            <div class="fill-bar" id="progressFill"></div>
        </div>
        <div class="progress-percent" id="percentDisplay">0%</div>
    </div>

    <div class="target-hint">
        <span class="target-label">🎯 目标锚点 :</span>
        <span class="target-path" id="targetDisplay">index-Dark.html</span>
        <span class="dest-badge">🌑 暗界领域</span>
    </div>

    <div class="action-area">
        <button class="jump-button" id="manualJumpBtn">
            <span>⚡</span> 立即跃迁 <span>⚡</span>
        </button>
        <div class="countdown-tip" id="countdownArea">自动跳转 <span id="countdownNum">3</span>s</div>
    </div>
    <footer>
        ⚙️ 力量系统 v.∞ · 空间协议已激活 | 执行索引重定向
    </footer>
</div>

<script>
    (function() {
        // ============================================================
        // 牛逼跳转逻辑: 目标 index-Dark.html (根据需求 从README跳转到index-Dark.html)
        // 同时增加预加载探测、动画模拟进度条、超酷倒计时、手动干预、异常优雅处理
        // ============================================================
        const TARGET_URL = "index-Dark.html";      // 最终跳转目标牛逼文件
        let countdownSeconds = 3;                  // 倒计时秒数
        let countdownInterval = null;
        let progressInterval = null;
        let isJumping = false;                     // 防止重复跃迁
        let jumpTimeout = null;

        // DOM 元素
        const statusMsgEl = document.getElementById("statusMessage");
        const progressFill = document.getElementById("progressFill");
        const percentDisplay = document.getElementById("percentDisplay");
        const countdownSpan = document.getElementById("countdownNum");
        const manualBtn = document.getElementById("manualJumpBtn");
        const countdownArea = document.getElementById("countdownArea");

        // 模拟进度递增 (平滑到达100%)
        let currentPercent = 0;
        const PROGRESS_STEP_TIME = 35;   // ms
        const TOTAL_PROGRESS_TIME = 3000; // 与倒计时3秒对齐 (3秒达到100%)
        let progressSteps = TOTAL_PROGRESS_TIME / PROGRESS_STEP_TIME;  // 约85步
        let incrementPerStep = 100 / progressSteps;

        // 更新UI 进度条
        function updateProgressUI(percent) {
            let val = Math.min(100, Math.max(0, percent));
            progressFill.style.width = val + "%";
            percentDisplay.innerText = Math.floor(val) + "%";
            if (val >= 99.5) {
                percentDisplay.innerText = "100%";
                progressFill.style.width = "100%";
            }
        }

        // 开始进度模拟 (线性增长)
        function startProgressSimulation() {
            if (progressInterval) clearInterval(progressInterval);
            currentPercent = 0;
            updateProgressUI(0);
            progressInterval = setInterval(() => {
                if (isJumping) return; // 如果跳转过程中避免混乱
                if (currentPercent < 100) {
                    let newPercent = currentPercent + incrementPerStep;
                    if (newPercent >= 100) {
                        newPercent = 100;
                        updateProgressUI(100);
                        // 注意！不要在这里跳转，需等待倒计时归零或100%完成时触发跳转检查
                        if (progressInterval) clearInterval(progressInterval);
                        progressInterval = null;
                        // 进度满了但可能还有倒计时边界，不过倒计时结束会调用jump,进度满也不主动跳避免双重
                    } else {
                        currentPercent = newPercent;
                        updateProgressUI(currentPercent);
                    }
                } else {
                    if (progressInterval) clearInterval(progressInterval);
                    progressInterval = null;
                }
            }, PROGRESS_STEP_TIME);
        }

        // 执行跃迁（真正的牛逼跳转，带特效闪避）
        function performJump() {
            if (isJumping) return;
            isJumping = true;

            // 停止所有计时器
            if (countdownInterval) clearInterval(countdownInterval);
            if (progressInterval) clearInterval(progressInterval);
            
            // 炫酷最终状态变化
            statusMsgEl.innerHTML = "✨ 时空裂隙开启 · 传送至暗界力量之境 ✨";
            progressFill.style.transition = "width 0.2s cubic-bezier(0.87, 0, 0.13, 1)";
            updateProgressUI(100);
            percentDisplay.innerHTML = "100% · 跃迁就绪";

            // 增加屏幕闪烁效果
            const overlay = document.createElement('div');
            overlay.style.position = 'fixed';
            overlay.style.top = 0;
            overlay.style.left = 0;
            overlay.style.width = '100%';
            overlay.style.height = '100%';
            overlay.style.backgroundColor = 'rgba(0, 255, 200, 0.2)';
            overlay.style.zIndex = 9999;
            overlay.style.pointerEvents = 'none';
            overlay.style.animation = 'flashFade 0.5s forwards';
            const styleAnim = document.createElement('style');
            styleAnim.textContent = `
                @keyframes flashFade {
                    0% { background-color: rgba(0, 255, 210, 0.9); backdrop-filter: blur(8px);}
                    100% { background-color: rgba(0, 255, 210, 0); backdrop-filter: blur(0px); visibility: hidden;}
                }
            `;
            document.head.appendChild(styleAnim);
            document.body.appendChild(overlay);

            // 附加音感震动（可选无声音，只是视觉震撼）
            const gateContainer = document.querySelector('.gateway-container');
            if(gateContainer) {
                gateContainer.style.transform = "scale(0.98)";
                gateContainer.style.transition = "transform 0.15s";
                setTimeout(() => { if(gateContainer) gateContainer.style.transform = ""; }, 160);
            }

            // 牛逼语句追踪
            console.log(`⚡[力量系统] 开始跃迁 => ${TARGET_URL}`);
            
            // 设置超时保险，确保跳转，如果location.href失败（极少情况）则fallback
            setTimeout(() => {
                if (!window.location.pathname.includes(TARGET_URL)) {
                    window.location.href = TARGET_URL;
                }
            }, 80);
            
            // 主跃迁
            try {
                // 尝试使用window.location 跳转
                window.location.href = TARGET_URL;
            } catch(e) {
                console.warn("跳转异常, 启动后备", e);
                window.location.assign(TARGET_URL);
            }
        }

        // 倒计时逻辑并自动触发跃迁
        function startCountdown() {
            if (countdownInterval) clearInterval(countdownInterval);
            let remaining = countdownSeconds;
            countdownSpan.innerText = remaining;
            countdownInterval = setInterval(() => {
                if (isJumping) {
                    if (countdownInterval) clearInterval(countdownInterval);
                    return;
                }
                remaining--;
                if (remaining <= 0) {
                    if (countdownInterval) clearInterval(countdownInterval);
                    countdownSpan.innerText = "0";
                    // 倒计时结束立刻执行跃迁
                    if (!isJumping) {
                        // 强制进度满
                        if (progressInterval) clearInterval(progressInterval);
                        updateProgressUI(100);
                        statusMsgEl.innerHTML = "🔥 力量阈值突破 · 执行跃迁指令 🔥";
                        performJump();
                    }
                } else {
                    countdownSpan.innerText = remaining;
                    // 动态状态消息
                    if (remaining === 2) statusMsgEl.innerHTML = "🌀 空间曲率校准 · 即将穿越 🌀";
                    if (remaining === 1) statusMsgEl.innerHTML = "⚡ 0.5 秒 · 力量觉醒完成 ⚡";
                }
            }, 1000);
        }

        // 手动强制立即跃迁 (牛逼plus)
        function manualJump() {
            if (isJumping) {
                statusMsgEl.innerHTML = "⚠️ 跃迁已在执行中，请勿重复触发 ⚠️";
                return;
            }
            // 停止倒计时和相关进程
            if (countdownInterval) clearInterval(countdownInterval);
            if (progressInterval) clearInterval(progressInterval);
            statusMsgEl.innerHTML = "💢 手动接管 · 超空间引擎激活 💢";
            // 瞬间拉满进度条
            updateProgressUI(100);
            percentDisplay.innerHTML = "100% · 强制传送";
            // 特效比自动更炸
            const flashLayer = document.createElement('div');
            flashLayer.style.position = 'fixed';
            flashLayer.style.top = 0;
            flashLayer.style.left = 0;
            flashLayer.style.width = '100%';
            flashLayer.style.height = '100%';
            flashLayer.style.background = 'radial-gradient(circle, rgba(0,255,200,0.5), transparent)';
            flashLayer.style.pointerEvents = 'none';
            flashLayer.style.zIndex = 9998;
            flashLayer.style.animation = 'manualFlash 0.3s forwards';
            const manualStyle = document.createElement('style');
            manualStyle.textContent = `
                @keyframes manualFlash {
                    0% { opacity: 1; transform: scale(1);}
                    100% { opacity: 0; transform: scale(2); visibility: hidden;}
                }
            `;
            document.head.appendChild(manualStyle);
            document.body.appendChild(flashLayer);
            
            setTimeout(() => {
                performJump();
            }, 60);
        }

        // 异步检查目标文件是否存在 （增加可选项 如果不存控制台优雅，但不影响跳转）
        function preflightCheck() {
            // 使用fetch轻探测目标文件 (不影响跳转，只是控制台留个牛逼日志)
            fetch(TARGET_URL, { method: 'HEAD', cache: 'no-cache', mode: 'no-cors' })  // no-cors 模式限制但至少不报跨域错
                .then(() => {
                    console.log(`✅ 力量枢纽侦测到目标[${TARGET_URL}] | 通道稳定`);
                    statusMsgEl.innerHTML = "✅ 通道稳定 · 暗界之力响应 ✅";
                })
                .catch(() => {
                    console.warn(`⚠️ 目标[${TARGET_URL}]未探测到，但跃迁指令将强制执行，若不存在会有力量反噬🤟`);
                    statusMsgEl.innerHTML = "⚠️ 目标坐标未知 · 依旧跃迁 (存在即力量) ⚠️";
                });
        }

        // 增加额外牛逼: 页面展示时 炫酷背景音感（无音频，视觉模拟）
        function addSubAtomicRipple() {
            const container = document.querySelector('.gateway-container');
            let mouseX = 0, mouseY = 0;
            document.body.addEventListener('mousemove', (e) => {
                mouseX = e.clientX;
                mouseY = e.clientY;
                if(container) {
                    let rect = container.getBoundingClientRect();
                    let dx = (mouseX - rect.left - rect.width/2) / 30;
                    let dy = (mouseY - rect.top - rect.height/2) / 30;
                    container.style.transform = `perspective(800px) rotateY(${dx * 0.5}deg) rotateX(${-dy * 0.3}deg)`;
                    container.style.transition = 'transform 0.1s ease-out';
                }
            });
            document.body.addEventListener('mouseleave', () => {
                if(container) container.style.transform = '';
            });
        }

        // 当用户点击强制链接文本或者随意操作，增加自由感
        function initialize() {
            startProgressSimulation();
            startCountdown();
            preflightCheck();
            addSubAtomicRipple();

            // 绑定手动跃迁按钮事件
            manualBtn.addEventListener('click', (e) => {
                e.preventDefault();
                manualJump();
            });
            
            // 额外牛逼：如果用户点击目标地址区域也可以提前触发(彩蛋)
            const targetElem = document.querySelector('.target-path');
            if(targetElem) {
                targetElem.style.cursor = 'pointer';
                targetElem.addEventListener('click', () => {
                    if(!isJumping){
                        statusMsgEl.innerHTML = "⚡ 触碰锚点 · 启动超感传送 ⚡";
                        manualJump();
                    }
                });
            }
            
            // 预加载悬停光效
            const btn = manualBtn;
            btn.addEventListener('mouseenter', () => {
                if(!isJumping) statusMsgEl.innerHTML = "🕹️ 手动跃迁就绪 · 点击撕裂空间 🕹️";
            });
            btn.addEventListener('mouseleave', () => {
                if(!isJumping && countdownInterval) statusMsgEl.innerHTML = "🌀 自动牵引倒计时中 · 力量涌动 🌀";
            });
        }

        // 页面关闭/跳转前清理
        window.addEventListener('beforeunload', () => {
            if (countdownInterval) clearInterval(countdownInterval);
            if (progressInterval) clearInterval(progressInterval);
        });

        initialize();
    })();
</script>
</body>
</html>
