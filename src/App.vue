<template>
  <div class="shoplist-container">
    <header class="header">
      <h1>NANAの拼车</h1>
    </header>

    <div class="card">
      <h2># 1. 节点交付 (单向流量)</h2>
      <div class="table-wrapper">
        <table>
          <thead>
            <tr>
              <th>套餐</th>
              <th>流量/带宽</th>
              <th>价格(月)</th>
              <th>价格(季)</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>GOMAMI</strong></td>
              <td>100G / 2Gbps</td>
              <td><strong>30/月</strong> <span class="status">(缺6)</span></td>
              <td><strong>75/季</strong> <span class="status">(缺6)</span></td>
            </tr>
            <tr>
              <td><strong>SeedNet</strong></td>
              <td>2T / 300Mbps</td>
              <td><strong>30/月</strong> <span class="status">(缺5)</span></td>
              <td><strong>75/季</strong> <span class="status">(缺5)</span></td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="warning-box">
        ⚠️ SeedNet: 05:00 换IP / 禁直连 / 仅落地
      </div>
    </div>

    <div class="card">
      <h2># 2. IX 线路 (自备落地) 500G 双向</h2>
      <div class="table-wrapper">
        <table>
          <thead>
            <tr>
              <th>套餐</th>
              <th>方案</th>
              <th>价格</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>套餐 A</strong></td>
              <td>前置G口 + IX + 内网</td>
              <td><strong>70/月</strong> <span class="status-ok">(长期有位)</span></td>
            </tr>
            <tr>
              <td><strong>套餐 B</strong></td>
              <td>前置G口 + IX</td>
              <td><strong>55/月</strong> <span class="status-ok">(长期有位)</span></td>
            </tr>
            <tr>
              <td><strong>套餐 C</strong></td>
              <td>IX + 内网</td>
              <td><strong>30/月</strong> <span class="status-ok">(长期有位)</span></td>
            </tr>
            <tr>
              <td><strong>套餐 D</strong></td>
              <td>仅IX (送阿里200M)</td>
              <td><strong>15/月</strong> <span class="status">(余5)</span></td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="warning-box">
        ⚠️ 落地仅允许协议: <code>SS 2022-blake3</code> / <code>vless+enc</code>
      </div>
      <p class="extra-note">注：ix通腾讯 华为 阿里 火山 百度等大厂</p>
    </div>

    <div class="card policy">
      <h3>📜 须知 & 政策</h3>
      <ul>
        <li><strong>严禁</strong>: 机场 / 车中车 (违者清退不退款)</li>
        <li><strong>退款</strong>: 跳车、个人问题不退；车主/商家问题按余值退</li>
        <li><strong>技术</strong>: 提供 TG 全方位支持</li>
      </ul>
      <p class="footer-msg">上车即代表同意上述政策</p>
    </div>
  </div>
</template>

<style scoped>
.shoplist-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 40px 20px;
}

.header {
  margin-bottom: 30px;
}

h1 {
  font-size: 1.8rem;
  font-weight: 700;
  color: #2c3e50;
}

.card {
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.4);
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 24px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

h2 {
  font-size: 1.2rem;
  margin-bottom: 15px;
  color: #333;
}

.table-wrapper {
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.95rem;
}

th, td {
  text-align: left;
  padding: 12px 8px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

th {
  color: #888;
  font-weight: 500;
  text-transform: uppercase;
  font-size: 0.8rem;
}

.warning-box {
  margin-top: 15px;
  padding: 10px 12px;
  background: rgba(255, 71, 87, 0.08);
  border-left: 4px solid #ff4757;
  font-size: 0.85rem;
  color: #444;
}

code {
  font-family: ui-monospace, monospace;
  background: rgba(0, 0, 0, 0.06);
  padding: 2px 5px;
  border-radius: 4px;
}

.status { color: #ff4757; margin-left: 4px; }
.status-ok { color: #2ed573; margin-left: 4px; }
.extra-note { font-size: 0.8rem; color: #999; margin-top: 10px; }

.policy h3 { margin-bottom: 12px; }
.policy ul { padding-left: 18px; margin: 0; }
.policy li { font-size: 0.9rem; margin-bottom: 6px; }
.footer-msg { 
  margin-top: 20px; 
  font-size: 0.8rem; 
  color: #bbb; 
  text-align: center;
}
</style>
