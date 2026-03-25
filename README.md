# [시트롯_댓글소통_에이전트 (5).html](https://github.com/user-attachments/files/26235536/_._.5.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>시트롯 댓글 소통 에이전트</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@300;400;600;700&family=Noto+Sans+KR:wght@300;400;500&display=swap');

  :root {
    --ink: #1a1209;
    --paper: #f5f0e8;
    --paper-dark: #ede6d6;
    --gold: #b8860b;
    --gold-light: #d4a017;
    --red: #8b1a1a;
    --muted: #7a6f5e;
    --border: #c8b89a;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background-color: var(--paper);
    color: var(--ink);
    font-family: 'Noto Sans KR', sans-serif;
    min-height: 100vh;
    background-image:
      repeating-linear-gradient(
        0deg,
        transparent,
        transparent 31px,
        rgba(180,160,120,0.15) 31px,
        rgba(180,160,120,0.15) 32px
      );
  }

  header {
    background: var(--ink);
    color: var(--paper);
    padding: 28px 32px 24px;
    position: relative;
    overflow: hidden;
  }

  header::before {
    content: '詩';
    position: absolute;
    right: 32px;
    top: 50%;
    transform: translateY(-50%);
    font-family: 'Noto Serif KR', serif;
    font-size: 80px;
    color: rgba(255,255,255,0.06);
    font-weight: 700;
    pointer-events: none;
  }

  .header-top {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 6px;
  }

  .badge {
    background: var(--gold);
    color: var(--ink);
    font-size: 11px;
    font-weight: 500;
    padding: 3px 10px;
    border-radius: 2px;
    letter-spacing: 0.05em;
  }

  header h1 {
    font-family: 'Noto Serif KR', serif;
    font-size: 22px;
    font-weight: 600;
    letter-spacing: -0.02em;
  }

  header p {
    font-size: 13px;
    color: rgba(245,240,232,0.55);
    font-weight: 300;
  }

  .main {
    max-width: 780px;
    margin: 0 auto;
    padding: 32px 20px 60px;
  }

  /* 설정 패널 */
  .settings-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 24px;
    margin-bottom: 28px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  }

  .settings-title {
    font-family: 'Noto Serif KR', serif;
    font-size: 14px;
    font-weight: 600;
    color: var(--gold);
    letter-spacing: 0.05em;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .settings-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .settings-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
  }

  @media (max-width: 560px) {
    .settings-grid { grid-template-columns: 1fr; }
  }

  .setting-item label {
    display: block;
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 6px;
    font-weight: 500;
    letter-spacing: 0.03em;
  }

  .setting-item select,
  .setting-item input[type="text"] {
    width: 100%;
    padding: 9px 12px;
    border: 1px solid var(--border);
    border-radius: 3px;
    font-family: 'Noto Sans KR', sans-serif;
    font-size: 13px;
    background: var(--paper);
    color: var(--ink);
    appearance: none;
    -webkit-appearance: none;
  }

  .setting-item select:focus,
  .setting-item input:focus {
    outline: none;
    border-color: var(--gold);
  }

  /* 댓글 입력 */
  .comment-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 24px;
    margin-bottom: 20px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  }

  .section-title {
    font-family: 'Noto Serif KR', serif;
    font-size: 14px;
    font-weight: 600;
    color: var(--red);
    letter-spacing: 0.05em;
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  textarea {
    width: 100%;
    min-height: 110px;
    padding: 14px;
    border: 1px solid var(--border);
    border-radius: 3px;
    font-family: 'Noto Sans KR', sans-serif;
    font-size: 14px;
    line-height: 1.7;
    background: var(--paper);
    color: var(--ink);
    resize: vertical;
  }

  textarea:focus {
    outline: none;
    border-color: var(--gold);
    background: #fffef9;
  }

  textarea::placeholder { color: #b0a58a; }

  /* 예시 댓글 버튼 */
  .examples {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 12px;
  }

  .example-btn {
    background: var(--paper-dark);
    border: 1px solid var(--border);
    color: var(--muted);
    font-size: 12px;
    padding: 5px 12px;
    border-radius: 20px;
    cursor: pointer;
    font-family: 'Noto Sans KR', sans-serif;
    transition: all 0.2s;
  }

  .example-btn:hover {
    background: var(--gold);
    color: white;
    border-color: var(--gold);
  }

  /* 버튼 */
  .generate-btn {
    width: 100%;
    padding: 15px;
    background: var(--ink);
    color: var(--paper);
    border: none;
    border-radius: 3px;
    font-family: 'Noto Serif KR', serif;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    letter-spacing: 0.08em;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }

  .generate-btn:hover {
    background: var(--red);
  }

  .generate-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  /* 로딩 */
  .loading {
    display: none;
    text-align: center;
    padding: 36px;
    color: var(--muted);
    font-size: 14px;
  }

  .loading.show { display: block; }

  .loading-dots span {
    display: inline-block;
    width: 6px; height: 6px;
    background: var(--gold);
    border-radius: 50%;
    margin: 0 3px;
    animation: bounce 1.2s infinite;
  }

  .loading-dots span:nth-child(2) { animation-delay: 0.2s; }
  .loading-dots span:nth-child(3) { animation-delay: 0.4s; }

  @keyframes bounce {
    0%, 80%, 100% { transform: scale(0.7); opacity: 0.5; }
    40% { transform: scale(1); opacity: 1; }
  }

  /* 결과 */
  .results-card {
    display: none;
    background: white;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 24px;
    margin-top: 20px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
    animation: fadeIn 0.4s ease;
  }

  .results-card.show { display: block; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .result-item {
    padding: 18px;
    background: var(--paper);
    border-left: 3px solid var(--gold);
    border-radius: 0 3px 3px 0;
    margin-bottom: 14px;
    position: relative;
  }

  .result-label {
    font-size: 11px;
    color: var(--gold);
    font-weight: 500;
    letter-spacing: 0.08em;
    margin-bottom: 8px;
    text-transform: uppercase;
  }

  .result-text {
    font-size: 14px;
    line-height: 1.85;
    color: var(--ink);
    white-space: pre-wrap;
    font-family: 'Noto Serif KR', serif;
  }

  .copy-btn {
    position: absolute;
    top: 14px;
    right: 14px;
    background: transparent;
    border: 1px solid var(--border);
    color: var(--muted);
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 2px;
    cursor: pointer;
    font-family: 'Noto Sans KR', sans-serif;
    transition: all 0.2s;
  }

  .copy-btn:hover {
    background: var(--ink);
    color: white;
    border-color: var(--ink);
  }

  .copy-btn.copied {
    background: var(--gold);
    color: white;
    border-color: var(--gold);
  }

  /* 구분선 장식 */
  .divider {
    text-align: center;
    color: var(--border);
    font-size: 18px;
    letter-spacing: 8px;
    margin: 8px 0 20px;
  }
</style>
</head>
<body>

<header>
  <div class="header-top">
    <span class="badge">AI 에이전트</span>
  </div>
  <h1>시트롯 댓글 소통 에이전트</h1>
  <p>이갑노 시인의 감성으로 팬들의 댓글에 답변을 드립니다</p>
</header>

<div class="main">

  <!-- 설정 -->
  <div class="settings-card">
    <div class="settings-title">응답 스타일 설정</div>
    <div class="settings-grid">
      <div class="setting-item">
        <label>감성 톤</label>
        <select id="tone">
          <option value="따뜻하고 시적인">따뜻하고 시적인</option>
          <option value="유머러스하고 친근한">유머러스하고 친근한</option>
          <option value="깊고 진중한">깊고 진중한</option>
          <option value="활기차고 트롯다운">활기차고 트롯다운</option>
        </select>
      </div>
      <div class="setting-item">
        <label>응답 길이</label>
        <select id="length">
          <option value="짧게 (1~2줄)">짧게 (1~2줄)</option>
          <option value="보통 (3~4줄)" selected>보통 (3~4줄)</option>
          <option value="길게 (5줄 이상)">길게 (5줄 이상)</option>
        </select>
      </div>
      <div class="setting-item">
        <label>채널 이름</label>
        <input type="text" id="channelName" value="이갑노 시인의 시트롯" placeholder="채널 이름 입력">
      </div>
      <div class="setting-item">
        <label>응답 개수</label>
        <select id="count">
          <option value="1개">1개</option>
          <option value="2개" selected>2개 (선택용)</option>
          <option value="3개">3개 (선택용)</option>
        </select>
      </div>
    </div>
  </div>

  <!-- 댓글 입력 -->
  <div class="comment-card">
    <div class="section-title">팬 댓글 붙여넣기</div>
    <textarea id="commentInput" placeholder="유튜브 댓글을 여기에 붙여넣으세요...

예: 선생님 목소리가 너무 좋아요. 오늘도 위로받고 갑니다 ㅠㅠ"></textarea>

    <div class="examples">
      <span style="font-size:12px; color:var(--muted); align-self:center;">예시:</span>
      <button class="example-btn" onclick="setExample(this)">목소리가 너무 좋아요 😭</button>
      <button class="example-btn" onclick="setExample(this)">이 노래 듣고 많이 울었어요</button>
      <button class="example-btn" onclick="setExample(this)">다음 노래는 언제 나와요?</button>
      <button class="example-btn" onclick="setExample(this)">구독하고 갑니다!</button>
      <button class="example-btn" onclick="setExample(this)">어머니 생각이 나서...</button>
    </div>
  </div>

  <div class="divider">· · ·</div>

  <button class="generate-btn" id="generateBtn" onclick="generateResponse()">
    ✦ 답글 생성하기
  </button>

  <!-- 로딩 -->
  <div class="loading" id="loading">
    <div class="loading-dots">
      <span></span><span></span><span></span>
    </div>
    <p style="margin-top:12px; font-size:13px;">시인의 마음으로 답글을 쓰고 있습니다...</p>
  </div>

  <!-- 결과 -->
  <div class="results-card" id="results">
    <div class="section-title">생성된 답글</div>
    <div id="resultsContent"></div>
    <p style="font-size:12px; color:var(--muted); margin-top:8px; text-align:center;">
      마음에 드는 답글을 복사해서 유튜브에 바로 붙여넣으세요
    </p>
  </div>

</div>

<script>
function setExample(btn) {
  document.getElementById('commentInput').value = btn.textContent.trim();
}

async function generateResponse() {
  const comment = document.getElementById('commentInput').value.trim();
  if (!comment) {
    alert('댓글을 입력해주세요.');
    return;
  }

  const tone = document.getElementById('tone').value;
  const length = document.getElementById('length').value;
  const channelName = document.getElementById('channelName').value || '이갑노 시인의 시트롯';
  const count = document.getElementById('count').value;

  const btn = document.getElementById('generateBtn');
  const loading = document.getElementById('loading');
  const results = document.getElementById('results');

  btn.disabled = true;
  loading.classList.add('show');
  results.classList.remove('show');

  const prompt = `당신은 유튜브 채널 "${channelName}"을 운영하는 이갑노 시인입니다.
시와 트롯을 결합한 독창적인 장르 "시트롯"을 창시하셨으며, 노년의 깊은 삶의 경험과 시인의 감성으로 팬들과 소통합니다.

팬이 남긴 댓글: "${comment}"

위 댓글에 대한 유튜브 답글을 ${count} 작성해주세요.

조건:
- 톤: ${tone}
- 길이: ${length}
- 시인답게 아름다운 언어를 사용하되 너무 어렵지 않게
- 팬의 감정에 진심으로 공감하는 느낌
- 트롯의 흥과 시의 감성이 자연스럽게 담기게
- 이모지를 1~2개 자연스럽게 포함
- 여러 개인 경우 각 답글 앞에 [답글 1], [답글 2] 형식으로 구분

답글만 작성하고 다른 설명은 하지 마세요.`;

  try {
    const GEMINI_API_KEY = "AIzaSyAz3UZ7SnD5vVDgjPY1ZqJ05MpClZYNkF4";
    const response = await fetch(
      `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${GEMINI_API_KEY}`,
      {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          contents: [{ parts: [{ text: prompt }] }],
          generationConfig: { maxOutputTokens: 1000 }
        })
      }
    );

    if (!response.ok) {
      const errData = await response.json();
      const errMsg = errData?.error?.message || response.status;
      throw new Error(errMsg);
    }

    const data = await response.json();
    const text = data.candidates?.[0]?.content?.parts?.[0]?.text;
    if (!text) throw new Error("응답이 비어있습니다.");

    displayResults(text, count);
  } catch (err) {
    document.getElementById('resultsContent').innerHTML = `<p style="color:red; font-size:13px;">오류: ${err.message}</p><p style="color:#888; font-size:12px; margin-top:6px;">F12 → Console 탭에서 자세한 내용을 확인하실 수 있어요.</p>`;
    results.classList.add('show');
  }

  btn.disabled = false;
  loading.classList.remove('show');
}

function displayResults(text, count) {
  const resultsContent = document.getElementById('resultsContent');
  const results = document.getElementById('results');

  let html = '';

  if (count === '1개') {
    html = createResultItem('답글', text.trim(), 0);
  } else {
    // 여러 개 파싱
    const parts = text.split(/\[답글\s*\d+\]/).filter(p => p.trim());
    if (parts.length > 1) {
      parts.forEach((part, i) => {
        html += createResultItem(`답글 ${i + 1}`, part.trim(), i);
      });
    } else {
      // 파싱 실패시 전체 표시
      html = createResultItem('답글', text.trim(), 0);
    }
  }

  resultsContent.innerHTML = html;
  results.classList.add('show');
  results.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
}

function createResultItem(label, text, index) {
  return `
    <div class="result-item" id="result-${index}">
      <div class="result-label">${label}</div>
      <div class="result-text">${escapeHtml(text)}</div>
      <button class="copy-btn" onclick="copyText(${index}, '${escapeAttr(text)}')">복사</button>
    </div>
  `;
}

function copyText(index, text) {
  navigator.clipboard.writeText(text).then(() => {
    const btn = document.querySelector(`#result-${index} .copy-btn`);
    btn.textContent = '복사됨 ✓';
    btn.classList.add('copied');
    setTimeout(() => {
      btn.textContent = '복사';
      btn.classList.remove('copied');
    }, 2000);
  });
}

function escapeHtml(text) {
  return text.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/\n/g,'<br>');
}

function escapeAttr(text) {
  return text.replace(/'/g, "\\'").replace(/\n/g, '\\n');
}
</script>
</body>
</html>
