<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Evolution: Neural Nets are Lego Blocks!</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700;900&display=swap');
        
        body {
            font-family: 'Noto Sans JP', sans-serif;
            background-color: #101820; /* Dark Base */
            color: #ffffff;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }
        ::-webkit-scrollbar-track {
            background: #101820; 
        }
        ::-webkit-scrollbar-thumb {
            background: #FEE715; 
            border-radius: 5px;
        }

        /* Palette Classes */
        .text-neon-yellow { color: #FEE715; }
        .bg-neon-yellow { background-color: #FEE715; }
        .border-neon-yellow { border-color: #FEE715; }
        
        .text-neon-cyan { color: #00FFFF; }
        .bg-neon-cyan { background-color: #00FFFF; }
        .border-neon-cyan { border-color: #00FFFF; }

        .text-neon-magenta { color: #FF00FF; }
        .bg-neon-magenta { background-color: #FF00FF; }
        .border-neon-magenta { border-color: #FF00FF; }

        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }

        /* Lego Block CSS Shape */
        .lego-stud {
            height: 10px;
            width: 20px;
            margin: 0 4px;
            border-radius: 2px 2px 0 0;
            display: inline-block;
        }
    </style>
    <!-- 
        NARRATIVE PLAN:
        1. Intro: Hook the reader with the "Lego" metaphor.
        2. Era 1 (Stats): Show how limited counting was.
        3. Era 2 (RNN): Introduce memory but show the fading effect.
        4. Era 3 (Seq2Seq): Show the translation structure and the bottleneck.
        5. Era 4 (Attention): Visualize the "Focus" mechanism.
        6. Era 5 (Transformer): Show the massive scale and speed.
        7. Conclusion: Summary table.
    -->
    <!-- 
        CHART SELECTION JUSTIFICATION (NO SVG):
        1. Stats Era: Bar Chart (Chart.js) -> Compare probabilities.
        2. RNN Era: Line Chart (Chart.js) -> Change over time (memory loss).
        3. Seq2Seq: HTML/CSS Flow -> Organize process (Structure).
        4. Attention: Bubble Chart (Chart.js) -> Relationship (Matrix of focus).
        5. Transformer: Bar Chart (Chart.js) -> Comparison (Speed/Scale).
    -->
    <!-- NO MERMAID JS USED. NO SVG USED. -->
    <!-- COLOR PALETTE: "Cyber" - #101820 (Dark), #FEE715 (Yellow), #00FFFF (Cyan), #FF00FF (Magenta) -->
</head>
<body class="overflow-x-hidden">

    <!-- HERO SECTION -->
    <header class="min-h-screen flex flex-col justify-center items-center text-center p-6 bg-[url('https://images.unsplash.com/photo-1629814234563-7c30072b2609?q=80&w=2070&auto=format&fit=crop')] bg-cover bg-center relative">
        <div class="absolute inset-0 bg-black/80"></div> <!-- Overlay -->
        <div class="relative z-10 max-w-4xl animate-fade-in-up">
            <h2 class="text-neon-cyan font-bold tracking-widest mb-4">MIDDLE SCHOOL AI GUIDE</h2>
            <h1 class="text-5xl md:text-7xl font-black mb-6 leading-tight">
                AIの進化は<br>
                <span class="text-neon-yellow">レゴブロック</span>だ！
            </h1>
            <p class="text-xl md:text-2xl text-gray-300 mb-8 max-w-2xl mx-auto">
                言葉を操るAI「LLM」は、たった数年でどうしてこんなに賢くなったの？<br>
                その秘密を「レゴ」に例えて5つの時代で見ていこう！
            </p>
            <div class="flex justify-center gap-2 mb-8">
                <div class="w-8 h-4 bg-neon-magenta rounded-t-sm"></div>
                <div class="w-8 h-4 bg-neon-yellow rounded-t-sm"></div>
                <div class="w-8 h-4 bg-neon-cyan rounded-t-sm"></div>
            </div>
            <a href="#era1" class="inline-block bg-neon-yellow text-black font-bold py-3 px-8 rounded-full hover:bg-white transition duration-300 transform hover:scale-105 shadow-[0_0_20px_rgba(254,231,21,0.5)]">
                進化の歴史を見る 🚀
            </a>
        </div>
    </header>

    <!-- MAIN CONTENT GRID -->
    <main class="max-w-7xl mx-auto p-6 md:p-12 space-y-24">

        <!-- INTRO CONTEXT -->
        <section class="text-center max-w-3xl mx-auto">
            <div class="glass-card p-8 rounded-2xl shadow-xl border-l-4 border-neon-cyan">
                <h3 class="text-3xl font-bold mb-4">魔法じゃなくて「学習」なんだ</h3>
                <p class="text-gray-300 text-lg leading-relaxed">
                    昔のAIは、人間が作った「ルールブック」がないと動けませんでした。でも今のAIは、大量のデータという「レゴブロック」を使って、自分で組み立て方を学んでいます。どうやって「ただの計算」から「万能マスター」になったのか？歴史を紐解きましょう！
                </p>
            </div>
        </section>

        <!-- ERA 1: STATISTICAL MODELS -->
        <section id="era1" class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div class="order-2 md:order-1">
                <div class="chart-container glass-card p-4 rounded-xl">
                    <canvas id="statsChart"></canvas>
                </div>
            </div>
            <div class="order-1 md:order-2">
                <div class="flex items-center gap-4 mb-4">
                    <span class="text-4xl">🤖</span>
                    <h2 class="text-4xl font-black text-neon-yellow">1. 統計モデルの時代</h2>
                </div>
                <p class="text-sm text-gray-400 font-mono mb-4">〜2010年頃 | とにかく数を数える時代</p>
                <p class="text-lg text-gray-300 mb-6">
                    最初は単純な確率計算でした。「私は」の次にくる言葉は何かな？と、過去のデータから回数を数えていただけ。<br><br>
                    <strong class="text-white">何がうれしかった？</strong><br>
                    機械翻訳の基礎ができました。でも、文の意味は分かっていないから、長文になると会話がめちゃくちゃになりがちでした。
                </p>
                <div class="bg-gray-800 p-4 rounded-lg border border-gray-700">
                    <p class="text-neon-cyan font-bold">例：「あめ」の次は？</p>
                    <p class="text-gray-400">「降る」確率 70%、「甘い」確率 30%... 前後の文脈関係なし！</p>
                </div>
            </div>
        </section>

        <!-- ERA 2: RNN/LSTM -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div>
                <div class="flex items-center gap-4 mb-4">
                    <span class="text-4xl">🧠</span>
                    <h2 class="text-4xl font-black text-neon-magenta">2. RNN・LSTMの時代</h2>
                </div>
                <p class="text-sm text-gray-400 font-mono mb-4">2010年代前半 | 記憶力を手に入れた！</p>
                <p class="text-lg text-gray-300 mb-6">
                    人間の脳（ニューラルネット）を真似しました。ここでAIは「直前のブロックを覚える」という<strong class="text-neon-magenta">短期記憶</strong>を手に入れます。<br><br>
                    <strong class="text-white">何がうれしかった？</strong><br>
                    「昨日」という言葉を覚えていれば、文末が「食べた」になる、といった「文脈（流れ）」を理解できるようになりました。
                </p>
            </div>
            <div>
                <div class="chart-container glass-card p-4 rounded-xl">
                    <canvas id="rnnChart"></canvas>
                </div>
            </div>
        </section>

        <!-- ERA 3: Seq2Seq -->
        <section class="bg-[#1a2332] p-8 md:p-12 rounded-3xl border border-gray-700 relative overflow-hidden">
            <!-- Decorative BG -->
            <div class="absolute top-0 right-0 w-64 h-64 bg-neon-cyan opacity-5 rounded-full blur-3xl"></div>

            <div class="text-center mb-10">
                <div class="flex justify-center items-center gap-4 mb-4">
                    <span class="text-4xl">🔄</span>
                    <h2 class="text-4xl font-black text-neon-cyan">3. Seq2Seqの時代</h2>
                </div>
                <p class="text-sm text-gray-400 font-mono mb-4">2014年頃 | 入力と出力のプロ</p>
                <p class="text-xl text-gray-300 max-w-3xl mx-auto">
                    AIを「読む人（エンコーダー）」と「書く人（デコーダー）」の2人に分けました。
                    これで「翻訳」や「要約」ができるように！<br>
                    <span class="text-neon-magenta">でも弱点が…長い文章を「ひとつの塊」に詰め込むので、最初の方を忘れちゃうんです。</span>
                </p>
            </div>

            <!-- HTML Diagram for Seq2Seq Process (No Mermaid/SVG) -->
            <div class="flex flex-col md:flex-row justify-center items-center gap-4 max-w-4xl mx-auto font-mono">
                
                <!-- Input -->
                <div class="flex flex-col items-center animate-pulse">
                    <div class="bg-gray-700 text-white p-4 rounded-lg mb-2 w-48 text-center border-l-4 border-neon-yellow">
                        入力文<br>(日本語)
                    </div>
                    <div class="text-2xl">⬇️</div>
                </div>

                <!-- Encoder -->
                <div class="bg-blue-900/50 p-6 rounded-xl border border-blue-500 w-full md:w-auto text-center">
                    <h4 class="text-blue-300 font-bold mb-2">エンコーダー</h4>
                    <p class="text-xs text-gray-400">読み込んで...</p>
                    <div class="my-2 text-2xl">📦</div>
                    <p class="text-xs text-white bg-blue-600 px-2 py-1 rounded">意味の塊に圧縮</p>
                </div>

                <!-- Bottleneck Arrow -->
                <div class="flex flex-col items-center">
                    <div class="h-1 w-16 md:w-24 bg-gradient-to-r from-blue-500 to-pink-500"></div>
                    <p class="text-[10px] text-gray-400 mt-1 uppercase tracking-widest">ボトルネック</p>
                </div>

                <!-- Decoder -->
                <div class="bg-pink-900/50 p-6 rounded-xl border border-pink-500 w-full md:w-auto text-center">
                    <h4 class="text-pink-300 font-bold mb-2">デコーダー</h4>
                    <p class="text-xs text-gray-400">展開する！</p>
                    <div class="my-2 text-2xl">📝</div>
                    <p class="text-xs text-white bg-pink-600 px-2 py-1 rounded">新しい文を作成</p>
                </div>

                <!-- Output -->
                <div class="flex flex-col items-center">
                    <div class="text-2xl">⬇️</div>
                    <div class="bg-gray-700 text-white p-4 rounded-lg mt-2 w-48 text-center border-r-4 border-neon-cyan">
                        出力文<br>(英語)
                    </div>
                </div>
            </div>
        </section>

        <!-- ERA 4: ATTENTION -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div class="order-2 md:order-1">
                <div class="chart-container glass-card p-4 rounded-xl">
                    <!-- Explain visualization -->
                    <div class="absolute top-4 left-4 z-10 bg-black/60 px-2 py-1 rounded text-xs text-gray-300">
                        色の濃さ = 注目度 (Attention)
                    </div>
                    <canvas id="attentionChart"></canvas>
                </div>
            </div>
            <div class="order-1 md:order-2">
                <div class="flex items-center gap-4 mb-4">
                    <span class="text-4xl">🎯</span>
                    <h2 class="text-4xl font-black text-neon-yellow">4. Attentionの時代</h2>
                </div>
                <p class="text-sm text-gray-400 font-mono mb-4">2015年頃 | 大事なところだけ見る「集中力」</p>
                <p class="text-lg text-gray-300 mb-6">
                    「長いと忘れちゃう問題」を解決！<br>
                    AIは文全体をぼんやり見るのではなく、<strong class="text-neon-yellow">「今、どの単語に注目すべきか？」</strong>を判断できるようになりました。<br><br>
                    <strong class="text-white">何がうれしかった？</strong><br>
                    「I ate an apple」を作るとき、「I」の時は「私」を、「apple」の時は「リンゴ」をピンポイントでカンニングできるので、翻訳精度が爆上がりしました。
                </p>
            </div>
        </section>

        <!-- ERA 5: TRANSFORMER / LLM -->
        <section class="mb-20">
            <div class="text-center mb-12">
                <div class="flex justify-center items-center gap-4 mb-4">
                    <span class="text-4xl">🚀</span>
                    <h2 class="text-4xl md:text-5xl font-black text-white bg-clip-text text-transparent bg-gradient-to-r from-neon-cyan to-neon-magenta">
                        5. Transformer 〜 LLMの時代
                    </h2>
                </div>
                <p class="text-sm text-gray-400 font-mono mb-6">2017年〜現在 | 超巨大工場で一気に組み立てろ！</p>
                <p class="text-xl text-gray-300 max-w-4xl mx-auto">
                    Attentionの「集中力」を手に入れたAIを、超並列処理で動かす技術。それがTransformerです。<br>
                    今まで1つずつ積んでいたレゴを、<strong class="text-neon-cyan">何千本ものロボットアームで同時に</strong>組み立てるようなもの。これでAIは「万能」になりました。
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Stat Card 1 -->
                <div class="glass-card p-6 rounded-xl text-center border-t-4 border-neon-yellow hover:translate-y-[-10px] transition-transform">
                    <div class="text-5xl mb-2">📚</div>
                    <h4 class="text-xl font-bold text-white mb-2">学習量</h4>
                    <p class="text-gray-400 text-sm">インターネット上のほぼ全てのテキストを読破</p>
                </div>
                <!-- Stat Card 2 -->
                <div class="glass-card p-6 rounded-xl text-center border-t-4 border-neon-cyan hover:translate-y-[-10px] transition-transform">
                    <div class="text-5xl mb-2">⚡</div>
                    <h4 class="text-xl font-bold text-white mb-2">並列処理</h4>
                    <p class="text-gray-400 text-sm">逐次処理から同時処理へ。<br>爆速で学習が可能に</p>
                </div>
                <!-- Stat Card 3 -->
                <div class="glass-card p-6 rounded-xl text-center border-t-4 border-neon-magenta hover:translate-y-[-10px] transition-transform">
                    <div class="text-5xl mb-2">🧱</div>
                    <h4 class="text-xl font-bold text-white mb-2">汎用性</h4>
                    <p class="text-gray-400 text-sm">翻訳も、作文も、プログラミングも。これ1つで何でもできる</p>
                </div>
            </div>

            <div class="mt-12 chart-container glass-card p-4 rounded-xl">
                <canvas id="transformerChart"></canvas>
            </div>
        </section>

        <!-- CONCLUSION SUMMARY -->
        <section class="bg-white text-black rounded-3xl p-8 md:p-12 shadow-2xl mb-12">
            <h2 class="text-3xl font-black text-center mb-8">まとめ：AI進化の通信簿</h2>
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse">
                    <thead>
                        <tr class="border-b-4 border-black text-lg">
                            <th class="p-4">時代・モデル</th>
                            <th class="p-4">レゴで例えると？</th>
                            <th class="p-4">できるようになったこと</th>
                        </tr>
                    </thead>
                    <tbody class="text-lg">
                        <tr class="border-b border-gray-300">
                            <td class="p-4 font-bold text-blue-800">1. 統計モデル</td>
                            <td class="p-4">隣のブロックを数えるだけ</td>
                            <td class="p-4">簡単な翻訳</td>
                        </tr>
                        <tr class="border-b border-gray-300">
                            <td class="p-4 font-bold text-blue-800">2. RNN / LSTM</td>
                            <td class="p-4">使ったブロックを覚えている</td>
                            <td class="p-4">自然な文章の流れ</td>
                        </tr>
                        <tr class="border-b border-gray-300">
                            <td class="p-4 font-bold text-blue-800">3. Seq2Seq</td>
                            <td class="p-4">設計図を作って渡す</td>
                            <td class="p-4">翻訳・要約（タスク）</td>
                        </tr>
                        <tr class="border-b border-gray-300">
                            <td class="p-4 font-bold text-blue-800">4. Attention</td>
                            <td class="p-4">大事なブロックを凝視する</td>
                            <td class="p-4">長文の理解</td>
                        </tr>
                        <tr>
                            <td class="p-4 font-bold text-purple-600 text-xl">5. Transformer</td>
                            <td class="p-4 font-bold">巨大工場で一斉に組立！</td>
                            <td class="p-4 font-bold">万能AI (ChatGPTなど)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="text-center mt-8">
                <p class="text-xl font-bold">次回予告：「Attention（集中力）」の秘密をもっと詳しく！</p>
            </div>
        </section>

    </main>

    <footer class="text-center py-8 text-gray-500 text-sm">
        <p>Created for "Middle School LLM Guide" Note.com Series</p>
        <!-- PALETTE USED: #101820, #FEE715, #00FFFF, #FF00FF -->
        <!-- NO SVG, NO MERMAID JS USED. CONFIRMED. -->
    </footer>

    <!-- SCRIPTS -->
    <script>
        // --- 1. Label Wrapping Helper (Mandatory) ---
        function splitLabel(label, maxLength = 16) {
            if (label.length <= maxLength) return label;
            const words = label.split(' ');
            const lines = [];
            let currentLine = words[0];

            for (let i = 1; i < words.length; i++) {
                if ((currentLine + " " + words[i]).length <= maxLength) {
                    currentLine += " " + words[i];
                } else {
                    lines.push(currentLine);
                    currentLine = words[i];
                }
            }
            lines.push(currentLine);
            return lines;
        }

        // --- 2. Shared Tooltip Config (Mandatory) ---
        const commonTooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels ? item.chart.data.labels[item.dataIndex] : '';
                    // For Scatter/Bubble where labels might be stored differently or implied
                    if (!label && item.raw && item.raw.label) label = item.raw.label;

                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            },
            titleFont: { family: "'Noto Sans JP', sans-serif", size: 14 },
            bodyFont: { family: "'Noto Sans JP', sans-serif", size: 13 },
            padding: 10,
            backgroundColor: 'rgba(16, 24, 32, 0.9)',
            borderColor: '#00FFFF',
            borderWidth: 1
        };

        const commonChartOptions = {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: {
                    labels: { color: '#ffffff', font: { family: "'Noto Sans JP', sans-serif" } }
                },
                tooltip: commonTooltipConfig
            },
            scales: {
                y: {
                    ticks: { color: '#aaaaaa' },
                    grid: { color: 'rgba(255,255,255,0.1)' }
                },
                x: {
                    ticks: { color: '#aaaaaa' },
                    grid: { color: 'rgba(255,255,255,0.1)' }
                }
            }
        };

        // --- 3. ERA 1: Statistical Model (Bar Chart) ---
        const ctxStats = document.getElementById('statsChart').getContext('2d');
        new Chart(ctxStats, {
            type: 'bar',
            data: {
                // "What comes after 'I'?"
                labels: ['am (高確率)', 'eat (中確率)', 'run (中確率)', 'apple (低確率)', 'fly (低確率)'].map(l => splitLabel(l)),
                datasets: [{
                    label: '「私は」の次に来る確率 (%)',
                    data: [45, 20, 15, 5, 2],
                    backgroundColor: [
                        '#FEE715', // Highlight
                        'rgba(254, 231, 21, 0.5)',
                        'rgba(254, 231, 21, 0.5)',
                        'rgba(254, 231, 21, 0.2)',
                        'rgba(254, 231, 21, 0.2)'
                    ],
                    borderColor: '#FEE715',
                    borderWidth: 1
                }]
            },
            options: {
                ...commonChartOptions,
                indexAxis: 'y', // Horizontal bar for readability
            }
        });

        // --- 4. ERA 2: RNN/LSTM (Line Chart) ---
        const ctxRnn = document.getElementById('rnnChart').getContext('2d');
        new Chart(ctxRnn, {
            type: 'line',
            data: {
                labels: ['1単語前', '5単語前', '10単語前', '20単語前', '50単語前', '100単語前'].map(l => splitLabel(l)),
                datasets: [
                    {
                        label: '単純なRNN (すぐ忘れる)',
                        data: [100, 60, 20, 5, 0, 0],
                        borderColor: '#FEE715', // Yellow
                        backgroundColor: 'rgba(254, 231, 21, 0.1)',
                        tension: 0.4,
                        fill: true
                    },
                    {
                        label: 'LSTM (記憶力アップ)',
                        data: [100, 95, 85, 75, 50, 30],
                        borderColor: '#FF00FF', // Magenta
                        backgroundColor: 'rgba(255, 0, 255, 0.1)',
                        tension: 0.4,
                        fill: true
                    }
                ]
            },
            options: commonChartOptions
        });

        // --- 5. ERA 4: Attention (Bubble/Heatmap Simulation) ---
        // Showing correlations between Input (JP) and Output (EN) words
        const ctxAttention = document.getElementById('attentionChart').getContext('2d');
        
        // Data structure simulating a heatmap using bubbles
        const attentionData = [
            { x: 1, y: 1, r: 25, label: "私 -> I" },      // I - 私 (Strong)
            { x: 2, y: 1, r: 2, label: "ate -> 私" },
            { x: 3, y: 1, r: 2, label: "apple -> 私" },
            
            { x: 1, y: 2, r: 2, label: "I -> 食べた" },
            { x: 2, y: 2, r: 25, label: "ate -> 食べた" },  // ate - 食べた (Strong)
            { x: 3, y: 2, r: 5, label: "apple -> 食べた" },

            { x: 1, y: 3, r: 2, label: "I -> リンゴ" },
            { x: 2, y: 3, r: 5, label: "ate -> リンゴ" },
            { x: 3, y: 3, r: 25, label: "apple -> リンゴ" }, // apple - リンゴ (Strong)
        ];

        new Chart(ctxAttention, {
            type: 'bubble',
            data: {
                datasets: [{
                    label: 'Attention Weight (集中度)',
                    data: attentionData,
                    backgroundColor: (context) => {
                        const val = context.raw?.r;
                        // Stronger color for higher value
                        return val > 20 ? '#00FFFF' : 'rgba(0, 255, 255, 0.3)';
                    },
                    borderColor: '#00FFFF'
                }]
            },
            options: {
                ...commonChartOptions,
                scales: {
                    x: {
                        type: 'linear',
                        position: 'bottom',
                        min: 0.5,
                        max: 3.5,
                        ticks: {
                            stepSize: 1,
                            callback: function(val) {
                                const labels = ['', 'I (英語)', 'ate (英語)', 'apple (英語)'];
                                return labels[val] || '';
                            },
                            color: '#ffffff',
                            font: { size: 14, weight: 'bold' }
                        },
                        title: { display: true, text: '出力単語 (英語)', color: '#aaaaaa' }
                    },
                    y: {
                        type: 'linear',
                        min: 0.5,
                        max: 3.5,
                        ticks: {
                            stepSize: 1,
                            callback: function(val) {
                                const labels = ['', '私 (入力)', '食べた (入力)', 'リンゴ (入力)'];
                                return labels[val] || '';
                            },
                            color: '#ffffff',
                            font: { size: 14, weight: 'bold' }
                        },
                        title: { display: true, text: '入力単語 (日本語)', color: '#aaaaaa' }
                    }
                },
                plugins: {
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return context.raw.label + " (強さ: " + context.raw.r + ")";
                            }
                        }
                    },
                    legend: { display: false }
                }
            }
        });

        // --- 6. ERA 5: Transformer Growth (Bar Chart) ---
        const ctxTransformer = document.getElementById('transformerChart').getContext('2d');
        new Chart(ctxTransformer, {
            type: 'bar',
            data: {
                labels: ['RNN時代の学習可能量', 'Transformer (2017)', 'GPT-1', 'GPT-3 (LLM)'].map(l => splitLabel(l)),
                datasets: [{
                    label: 'パラメータ数 / 学習能力 (指数的増加のイメージ)',
                    data: [1, 5, 20, 100], // Normalized illustrative data
                    backgroundColor: [
                        '#666666',
                        '#FF00FF',
                        '#00FFFF',
                        '#FEE715'
                    ],
                    barPercentage: 0.6
                }]
            },
            options: {
                ...commonChartOptions,
                scales: {
                    y: {
                        display: false // Hide numbers to focus on the trend visualization
                    },
                    x: {
                        ticks: { color: '#ffffff', font: { size: 12 } }
                    }
                },
                plugins: {
                    ...commonChartOptions.plugins,
                    legend: { display: false },
                    tooltip: {
                         callbacks: {
                            title: commonTooltipConfig.callbacks.title,
                            label: function(context) {
                                const comments = [
                                    "すぐ限界が来る...",
                                    "並列処理で効率化！",
                                    "巨大化開始",
                                    "圧倒的。レゴマスター誕生"
                                ];
                                return comments[context.dataIndex];
                            }
                        }
                    }
                }
            }
        });

    </script>
</body>
</html>