<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sunday Kerygma — 보컬 음향 운영 매뉴얼 v3</title>
<style>
  :root {
    --primary:#1F4E79; --secondary:#2E75B6; --accent:#4472C4;
    --light-blue:#D6E4F0; --light-gray:#F5F7FA; --mid-gray:#DDE3ED;
    --text:#1a2236; --text-muted:#5a6a82;
    --tag-green:#e8f5e9; --tag-green-text:#2e7d32;
    --tag-orange:#fff3e0; --tag-orange-text:#e65100;
    --tag-purple:#f3e5f5; --tag-purple-text:#6a1b9a;
    --tag-red:#fdecea; --tag-red-text:#b71c1c;
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  body{font-family:'Malgun Gothic','Apple SD Gothic Neo','Noto Sans KR',sans-serif;background:#eef2f7;color:var(--text);font-size:15px;line-height:1.7;}
  .sidebar{position:fixed;top:0;left:0;width:260px;height:100vh;background:var(--primary);overflow-y:auto;z-index:100;display:flex;flex-direction:column;}
  .sidebar-brand{padding:28px 20px 20px;border-bottom:1px solid rgba(255,255,255,0.15);}
  .sidebar-brand h1{font-size:18px;font-weight:700;color:#fff;}
  .sidebar-brand p{font-size:11px;color:rgba(255,255,255,0.55);margin-top:4px;}
  .sidebar nav{padding:16px 0;flex:1;}
  .nav-item{display:flex;align-items:center;gap:10px;padding:10px 20px;color:rgba(255,255,255,0.72);text-decoration:none;font-size:13.5px;transition:all 0.15s;border-left:3px solid transparent;cursor:pointer;}
  .nav-item:hover,.nav-item.active{color:#fff;background:rgba(255,255,255,0.1);border-left-color:#7EC8F4;}
  .nav-item .icon{font-size:16px;width:22px;text-align:center;flex-shrink:0;}
  .nav-num{font-size:11px;background:rgba(255,255,255,0.15);border-radius:10px;padding:1px 7px;margin-left:auto;color:rgba(255,255,255,0.6);}
  .main{margin-left:260px;min-height:100vh;}
  .hero{background:linear-gradient(135deg,var(--primary) 0%,#2563a8 60%,var(--accent) 100%);padding:64px 60px 56px;color:#fff;}
  .hero-tag{display:inline-block;background:rgba(255,255,255,0.18);border-radius:20px;padding:4px 14px;font-size:12px;letter-spacing:1px;text-transform:uppercase;margin-bottom:18px;}
  .hero h1{font-size:42px;font-weight:800;letter-spacing:-0.5px;margin-bottom:10px;}
  .hero p{font-size:17px;color:rgba(255,255,255,0.8);max-width:600px;}
  .hero-flow{display:flex;flex-wrap:wrap;gap:6px;margin-top:32px;align-items:center;}
  .flow-step{background:rgba(255,255,255,0.15);border:1px solid rgba(255,255,255,0.25);border-radius:20px;padding:5px 14px;font-size:12.5px;color:rgba(255,255,255,0.9);}
  .flow-arrow{color:rgba(255,255,255,0.45);font-size:14px;}
  .content{padding:0 48px 80px;}
  .section{margin-top:52px;scroll-margin-top:24px;}
  .section-header{display:flex;align-items:center;gap:14px;margin-bottom:28px;padding-bottom:14px;border-bottom:2px solid var(--mid-gray);}
  .section-icon{width:44px;height:44px;background:linear-gradient(135deg,var(--primary),var(--accent));border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0;box-shadow:0 4px 12px rgba(31,78,121,0.25);}
  .section-header h2{font-size:24px;font-weight:700;color:var(--primary);}
  .section-num{font-size:13px;color:var(--text-muted);font-weight:400;}
  .card-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:16px;margin-bottom:24px;}
  .card{background:#fff;border-radius:14px;padding:20px 22px;box-shadow:0 2px 10px rgba(31,78,121,0.08);border:1px solid var(--mid-gray);transition:transform 0.15s,box-shadow 0.15s;}
  .card:hover{transform:translateY(-2px);box-shadow:0 6px 20px rgba(31,78,121,0.14);}
  .card-title{font-size:14px;font-weight:700;color:var(--secondary);margin-bottom:8px;display:flex;align-items:center;gap:8px;}
  .card-title .dot{width:8px;height:8px;background:var(--secondary);border-radius:50%;flex-shrink:0;}
  .card p{font-size:13.5px;color:var(--text-muted);line-height:1.6;}
  .card ul{padding-left:18px;}
  .card li{font-size:13.5px;color:var(--text-muted);margin-bottom:4px;}
  .subheading{font-size:17px;font-weight:700;color:var(--primary);margin:28px 0 12px;padding-left:12px;border-left:4px solid var(--secondary);}
  .info-box{background:var(--light-blue);border-left:4px solid var(--secondary);border-radius:0 10px 10px 0;padding:14px 18px;margin:14px 0;font-size:14px;color:var(--primary);}
  .info-box .label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--secondary);margin-bottom:4px;}
  .tip-box{background:#FFF8E1;border-left:4px solid #F9A825;border-radius:0 10px 10px 0;padding:14px 18px;margin:14px 0;font-size:14px;color:#5d4037;}
  .warn-box{background:#fdecea;border-left:4px solid #e53935;border-radius:0 10px 10px 0;padding:14px 18px;margin:14px 0;font-size:14px;color:#b71c1c;}
  .pro2c-box{background:#1a1a2e;border-left:4px solid #7c4dff;border-radius:0 10px 10px 0;padding:14px 18px;margin:14px 0;font-size:14px;color:#e8d5ff;}
  .pro2c-box .label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:#b39ddb;margin-bottom:4px;}
  .table-wrap{overflow-x:auto;border-radius:12px;box-shadow:0 2px 10px rgba(31,78,121,0.08);margin:16px 0;}
  table{width:100%;border-collapse:collapse;background:#fff;font-size:13.5px;}
  thead tr{background:var(--primary);}
  thead th{padding:12px 16px;text-align:left;color:#fff;font-size:13px;font-weight:600;letter-spacing:0.3px;white-space:nowrap;}
  thead th:first-child{border-radius:12px 0 0 0;}
  thead th:last-child{border-radius:0 12px 0 0;}
  tbody tr{border-bottom:1px solid #EEF2F7;transition:background 0.1s;}
  tbody tr:hover{background:var(--light-blue);}
  tbody tr:last-child{border-bottom:none;}
  tbody tr:nth-child(even){background:var(--light-gray);}
  tbody tr:nth-child(even):hover{background:var(--light-blue);}
  tbody td{padding:10px 16px;color:var(--text);vertical-align:top;}
  tbody td:first-child{font-weight:600;color:var(--primary);}
  .param-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:12px;margin:16px 0;}
  .param-card{background:#fff;border-radius:10px;padding:16px;border:1px solid var(--mid-gray);box-shadow:0 1px 6px rgba(31,78,121,0.07);}
  .param-name{font-size:13px;font-weight:700;color:var(--secondary);margin-bottom:4px;}
  .param-q{font-size:12px;color:var(--text-muted);margin-bottom:6px;font-style:italic;}
  .param-desc{font-size:13px;color:var(--text);}
  .tag{display:inline-block;padding:2px 10px;border-radius:12px;font-size:12px;font-weight:600;margin:2px;}
  .tag-blue{background:var(--light-blue);color:var(--primary);}
  .tag-green{background:var(--tag-green);color:var(--tag-green-text);}
  .tag-orange{background:var(--tag-orange);color:var(--tag-orange-text);}
  .tag-purple{background:var(--tag-purple);color:var(--tag-purple-text);}
  .tag-red{background:var(--tag-red);color:var(--tag-red-text);}
  .tag-dark{background:#1a1a2e;color:#b39ddb;}
  .flow-chart{display:flex;flex-direction:column;gap:0;margin:20px 0;max-width:500px;}
  .flow-node{display:flex;align-items:center;gap:16px;background:#fff;border:1px solid var(--mid-gray);border-radius:10px;padding:12px 18px;box-shadow:0 1px 6px rgba(31,78,121,0.07);}
  .flow-node-num{width:28px;height:28px;background:var(--primary);border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;font-size:12px;font-weight:700;flex-shrink:0;}
  .flow-node-label{font-weight:700;color:var(--primary);font-size:14px;}
  .flow-node-desc{font-size:13px;color:var(--text-muted);}
  .flow-connector{width:2px;height:20px;background:linear-gradient(to bottom,var(--secondary),var(--accent));margin-left:33px;opacity:0.5;}
  .hl-blue{background:#e8f0fe;border:2px solid #4472C4;border-radius:12px;padding:16px 20px;margin:8px 0;}
  .hl-green{background:#e8f5e9;border:2px solid #2e7d32;border-radius:12px;padding:16px 20px;margin:8px 0;}
  .hl-dark{background:#1a1a2e;border:2px solid #7c4dff;border-radius:12px;padding:16px 20px;margin:8px 0;color:#e8d5ff;}
  .hl-title{font-size:15px;font-weight:800;color:var(--primary);margin-bottom:4px;}
  .hl-title-green{font-size:15px;font-weight:800;color:#1b5e20;margin-bottom:4px;}
  .hl-title-dark{font-size:15px;font-weight:800;color:#ce93d8;margin-bottom:4px;}
  .hl-sub{font-size:12px;color:var(--text-muted);margin-bottom:10px;}
  .hl-sub-dark{font-size:12px;color:#b39ddb;margin-bottom:10px;}
  .two-col{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
  .three-stat{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin:16px 0;}
  .stat-box{background:#fff;border-radius:12px;padding:18px;text-align:center;border:1px solid var(--mid-gray);box-shadow:0 2px 8px rgba(31,78,121,0.06);}
  .stat-label{font-size:11px;color:var(--text-muted);font-weight:700;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px;}
  .stat-value{font-size:22px;font-weight:800;color:#e65100;}
  .stat-desc{font-size:12px;color:var(--text-muted);margin-top:4px;}
  /* EQ 트러블슈팅 플로우 */
  .ts-flow{display:flex;flex-direction:column;gap:0;max-width:420px;margin:16px 0;}
  .ts-node{background:#fff;border-radius:10px;padding:14px 18px;border:1px solid var(--mid-gray);box-shadow:0 1px 6px rgba(31,78,121,0.07);}
  .ts-node-q{font-weight:800;color:var(--primary);font-size:14px;margin-bottom:4px;}
  .ts-node-desc{font-size:12.5px;color:var(--text-muted);}
  .ts-connector{width:2px;height:24px;background:var(--secondary);margin-left:20px;opacity:0.4;}
  .ts-num{display:inline-flex;width:24px;height:24px;background:var(--primary);color:#fff;border-radius:50%;align-items:center;justify-content:center;font-size:11px;font-weight:700;margin-right:8px;flex-shrink:0;}
  /* Pro2C 모드 카드 */
  .mode-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:12px;margin:16px 0;}
  .mode-card{border-radius:12px;padding:16px 18px;border:2px solid;transition:transform 0.15s;}
  .mode-card:hover{transform:translateY(-2px);}
  .mode-1{background:#fdecea;border-color:#e53935;}
  .mode-2{background:#e8f5e9;border-color:#2e7d32;}
  .mode-3{background:#e8f0fe;border-color:#4472C4;}
  .mode-4{background:#fff8e1;border-color:#f9a825;}
  .mode-5{background:#f3e5f5;border-color:#8e24aa;}
  .mode-num{font-size:11px;font-weight:800;letter-spacing:1px;margin-bottom:6px;}
  .mode-name{font-size:14px;font-weight:800;margin-bottom:2px;}
  .mode-eng{font-size:11px;color:var(--text-muted);margin-bottom:8px;}
  .mode-char{font-size:12.5px;color:var(--text-muted);line-height:1.6;margin-bottom:8px;}
  .mode-apply{font-size:12px;font-weight:700;padding:4px 10px;border-radius:8px;display:inline-block;}
  @media(max-width:900px){.sidebar{display:none;}.main{margin-left:0;}.hero{padding:40px 24px;}.content{padding:0 20px 60px;}.hero h1{font-size:28px;}.two-col,.three-stat{grid-template-columns:1fr;}}
  .sidebar::-webkit-scrollbar{width:4px;}.sidebar::-webkit-scrollbar-thumb{background:rgba(255,255,255,0.2);border-radius:4px;}

  /* ===== Rotation Cases ===== */

  :root {
    --primary:#1F4E79; --secondary:#2E75B6; --accent:#4472C4;
    --light-blue:#D6E4F0; --mid-gray:#DDE3ED; --text:#1a2236; --text-muted:#5a6a82;
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  body{font-family:'Malgun Gothic','Apple SD Gothic Neo','Noto Sans KR',sans-serif;background:#eef2f7;color:var(--text);font-size:14px;line-height:1.6;padding:24px 16px 48px;}
  h1{text-align:center;font-size:1.4rem;font-weight:800;color:var(--primary);margin-bottom:6px;}
  .subtitle{text-align:center;font-size:0.82rem;color:#888;margin-bottom:28px;}

  .tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:24px;justify-content:center;}
  .tab{padding:8px 18px;border-radius:20px;border:2px solid var(--mid-gray);background:#fff;font-size:0.82rem;font-weight:700;cursor:pointer;transition:all 0.15s;color:var(--text-muted);}
  .tab.active{background:var(--primary);color:#fff;border-color:var(--primary);}
  .tab:hover:not(.active){border-color:var(--secondary);color:var(--secondary);}

  .case-panel{display:none;}
  .case-panel.active{display:block;}

  .case-header{background:linear-gradient(135deg,var(--primary),var(--accent));border-radius:14px;padding:18px 24px;color:#fff;margin-bottom:20px;}
  .case-header h2{font-size:1.15rem;font-weight:800;margin-bottom:4px;}
  .case-header p{font-size:0.82rem;color:rgba(255,255,255,0.8);}
  .case-roles{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;}
  .role-badge{padding:4px 12px;border-radius:20px;font-size:0.75rem;font-weight:700;}
  .role-main{background:rgba(255,255,255,0.25);color:#fff;}
  .role-sub{background:#fbbf24;color:#1a1a1a;}
  .role-bv{background:rgba(255,255,255,0.15);color:rgba(255,255,255,0.9);}
  .role-fixed{background:#34d399;color:#1a1a1a;}

  .week-card{background:#fff;border-radius:14px;box-shadow:0 2px 10px rgba(31,78,121,0.08);border:1px solid var(--mid-gray);margin-bottom:18px;overflow:hidden;}
  .week-header{display:flex;align-items:center;gap:10px;padding:12px 18px;background:linear-gradient(90deg,#3b4cca,#6c7fe8);color:#fff;flex-wrap:wrap;}
  .week-badge{font-size:1rem;font-weight:800;background:rgba(255,255,255,0.2);border-radius:8px;padding:2px 10px;}
  .week-db{font-size:0.8rem;}
  .week-note{font-size:0.75rem;margin-left:auto;background:rgba(255,255,255,0.15);border-radius:20px;padding:2px 10px;}

  .stage{display:flex;gap:8px;padding:14px;align-items:stretch;}
  .side{flex:1;background:#f7f8ff;border-radius:10px;padding:12px;border:1.5px solid #e0e4ff;}
  .side-label{font-size:0.65rem;font-weight:700;color:#3b4cca;margin-bottom:8px;letter-spacing:1px;}
  .side-total{font-size:0.68rem;color:#888;margin-top:8px;text-align:right;}
  .center-col{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:4px;min-width:44px;}
  .mic-icon{font-size:1.6rem;}
  .mic-label{font-size:0.6rem;color:#aaa;font-weight:600;text-align:center;line-height:1.3;}
  .sub-col{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:4px;min-width:60px;}
  .sub-box{background:#fef3c7;border:2px solid #f59e0b;border-radius:10px;padding:8px 10px;text-align:center;}
  .sub-name{font-size:0.85rem;font-weight:800;color:#92400e;}
  .sub-tag{font-size:0.6rem;color:#b45309;font-weight:700;margin-bottom:2px;}

  .member{display:flex;align-items:center;gap:6px;background:#fff;border-radius:7px;padding:6px 9px;margin-bottom:5px;border:1px solid #e8eaff;box-shadow:0 1px 3px rgba(0,0,0,0.04);}
  .member:last-child{margin-bottom:0;}
  .gbadge{font-size:0.6rem;font-weight:700;border-radius:3px;padding:1px 5px;flex-shrink:0;}
  .male{background:#dbeafe;color:#1d4ed8;}
  .female{background:#fce7f3;color:#be185d;}
  .mname{font-size:0.85rem;font-weight:700;flex:1;}
  .db15{background:#3b4cca;color:#fff;border-radius:20px;padding:1px 7px;font-size:0.65rem;font-weight:700;flex-shrink:0;}
  .db10{background:#94a3b8;color:#fff;border-radius:20px;padding:1px 7px;font-size:0.65rem;font-weight:700;flex-shrink:0;}
  .fixed-badge{background:#34d399;color:#065f46;border-radius:4px;padding:1px 6px;font-size:0.6rem;font-weight:700;flex-shrink:0;}

  .note-warn{margin:0 14px 12px;padding:8px 12px;background:#fff7ed;color:#92400e;border-left:3px solid #f59e0b;border-radius:6px;font-size:0.75rem;}
  .note-good{margin:0 14px 12px;padding:8px 12px;background:#f0fdf4;color:#166534;border-left:3px solid #22c55e;border-radius:6px;font-size:0.75rem;}

  .summary-card{background:#fff;border-radius:14px;box-shadow:0 2px 10px rgba(31,78,121,0.08);overflow:hidden;margin-top:8px;}
  .summary-header{padding:12px 18px;background:linear-gradient(90deg,#1e293b,#334155);color:#fff;font-weight:800;font-size:0.9rem;}
  .sum-table{width:100%;border-collapse:collapse;font-size:0.78rem;}
  .sum-table th{background:#f8fafc;color:#64748b;font-weight:700;padding:9px 12px;text-align:center;border-bottom:1px solid #e2e8f0;}
  .sum-table td{padding:9px 12px;text-align:center;border-bottom:1px solid #f1f5f9;}
  .sum-table tr:last-child td{border-bottom:none;}
  .sum-table tr:hover td{background:#f8fafc;}
  .pos-l{background:#dbeafe;color:#1e40af;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;display:inline-block;}
  .pos-r{background:#fce7f3;color:#9d174d;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;display:inline-block;}
  .pos-s{background:#fef3c7;color:#92400e;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;display:inline-block;}
  .tip-box{background:#fffbeb;border-radius:10px;padding:12px 16px;font-size:0.78rem;color:#78350f;line-height:1.8;border:1px solid #fde68a;margin-top:16px;}

  @media(max-width:600px){.stage{flex-wrap:wrap;}.side{min-width:calc(50% - 8px);}}

  /* 케이스 탭 */
  .tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:24px;justify-content:center;}
  .tab{padding:8px 18px;border-radius:20px;border:2px solid var(--mid-gray);background:#fff;font-size:0.82rem;font-weight:700;cursor:pointer;transition:all 0.15s;color:var(--text-muted);}
  .tab.active{background:var(--primary);color:#fff;border-color:var(--primary);}
  .tab:hover:not(.active){border-color:var(--secondary);color:var(--secondary);}

  /* 케이스 패널 */
  .case-panel{display:none;}
  .case-panel.active{display:block;}

  .case-header{background:linear-gradient(135deg,var(--primary),var(--accent));border-radius:14px;padding:18px 24px;color:#fff;margin-bottom:20px;}
  .case-header h2{font-size:1.15rem;font-weight:800;margin-bottom:4px;}
  .case-header p{font-size:0.82rem;color:rgba(255,255,255,0.8);}
  .case-roles{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;}
  .role-badge{padding:4px 12px;border-radius:20px;font-size:0.75rem;font-weight:700;}
  .role-main{background:rgba(255,255,255,0.25);color:#fff;}
  .role-sub{background:#fbbf24;color:#1a1a1a;}
  .role-bv{background:rgba(255,255,255,0.15);color:rgba(255,255,255,0.9);}
  .role-fixed{background:#34d399;color:#1a1a1a;}

  /* 주차 카드 */
  .week-card{background:#fff;border-radius:14px;box-shadow:0 2px 10px rgba(31,78,121,0.08);border:1px solid var(--mid-gray);margin-bottom:18px;overflow:hidden;}
  .week-header{display:flex;align-items:center;gap:10px;padding:12px 18px;background:linear-gradient(90deg,#3b4cca,#6c7fe8);color:#fff;flex-wrap:wrap;}
  .week-badge{font-size:1rem;font-weight:800;background:rgba(255,255,255,0.2);border-radius:8px;padding:2px 10px;}
  .week-db{font-size:0.8rem;}
  .week-note{font-size:0.75rem;margin-left:auto;background:rgba(255,255,255,0.15);border-radius:20px;padding:2px 10px;}

  /* 무대 */
  .stage{display:flex;gap:8px;padding:14px;align-items:stretch;overflow-x:auto;}
  .side{flex:1;min-width:100px;background:#f7f8ff;border-radius:10px;padding:12px;border:1.5px solid #e0e4ff;}
  .side-label{font-size:0.65rem;font-weight:700;color:#3b4cca;margin-bottom:8px;letter-spacing:1px;}
  .side-total{font-size:0.68rem;color:#888;margin-top:8px;text-align:right;}
  .center-col{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:4px;min-width:44px;}
  .mic-icon{font-size:1.6rem;}
  .mic-label{font-size:0.6rem;color:#aaa;font-weight:600;text-align:center;line-height:1.3;}

  /* 보조인도자 칸 */
  .sub-col{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:4px;min-width:56px;}
  .sub-box{background:#fef3c7;border:2px solid #f59e0b;border-radius:10px;padding:8px 10px;text-align:center;}
  .sub-name{font-size:0.85rem;font-weight:800;color:#92400e;}
  .sub-tag{font-size:0.6rem;color:#b45309;font-weight:700;}

  /* 멤버 카드 */
  .member{display:flex;align-items:center;gap:6px;background:#fff;border-radius:7px;padding:6px 9px;margin-bottom:5px;border:1px solid #e8eaff;box-shadow:0 1px 3px rgba(0,0,0,0.04);}
  .member:last-child{margin-bottom:0;}
  .gbadge{font-size:0.6rem;font-weight:700;border-radius:3px;padding:1px 5px;flex-shrink:0;}
  .male{background:#dbeafe;color:#1d4ed8;}
  .female{background:#fce7f3;color:#be185d;}
  .mname{font-size:0.85rem;font-weight:700;flex:1;}
  .db15{background:#3b4cca;color:#fff;border-radius:20px;padding:1px 7px;font-size:0.65rem;font-weight:700;flex-shrink:0;}
  .db10{background:#94a3b8;color:#fff;border-radius:20px;padding:1px 7px;font-size:0.65rem;font-weight:700;flex-shrink:0;}
  .fixed-badge{background:#34d399;color:#065f46;border-radius:4px;padding:1px 6px;font-size:0.6rem;font-weight:700;flex-shrink:0;}

  .note-warn{margin:0 14px 12px;padding:8px 12px;background:#fff7ed;color:#92400e;border-left:3px solid #f59e0b;border-radius:6px;font-size:0.75rem;}
  .note-good{margin:0 14px 12px;padding:8px 12px;background:#f0fdf4;color:#166534;border-left:3px solid #22c55e;border-radius:6px;font-size:0.75rem;}

  /* 요약 테이블 */
  .summary-card{background:#fff;border-radius:14px;box-shadow:0 2px 10px rgba(31,78,121,0.08);overflow:hidden;margin-top:8px;}
  .summary-header{padding:12px 18px;background:linear-gradient(90deg,#1e293b,#334155);color:#fff;font-weight:800;font-size:0.9rem;}
  .sum-table{width:100%;border-collapse:collapse;font-size:0.78rem;}
  .sum-table th{background:#f8fafc;color:#64748b;font-weight:700;padding:9px 12px;text-align:center;border-bottom:1px solid #e2e8f0;}
  .sum-table td{padding:9px 12px;text-align:center;border-bottom:1px solid #f1f5f9;}
  .sum-table tr:last-child td{border-bottom:none;}
  .sum-table tr:hover td{background:#f8fafc;}
  .pos-l{background:#dbeafe;color:#1e40af;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;}
  .pos-r{background:#fce7f3;color:#9d174d;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;}
  .pos-s{background:#fef3c7;color:#92400e;border-radius:4px;padding:2px 8px;font-weight:700;font-size:0.75rem;}

  .tip-box{background:#fffbeb;border-radius:10px;padding:12px 16px;font-size:0.78rem;color:#78350f;line-height:1.8;border:1px solid #fde68a;margin-top:16px;}

  @media(max-width:600px){
    .stage{flex-direction:column;}
    .center-col,.sub-col{flex-direction:row;min-width:unset;justify-content:center;}
  }

  /* 모바일 햄버거 */
  .mobile-header {
    display: none;
    position: fixed; top: 0; left: 0; right: 0; z-index: 200;
    background: var(--primary);
    padding: 14px 20px;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 2px 12px rgba(0,0,0,0.2);
  }
  .mobile-header h2 { font-size: 15px; font-weight: 700; color: #fff; }
  .hamburger {
    background: none; border: none; cursor: pointer;
    display: flex; flex-direction: column; gap: 5px; padding: 4px;
  }
  .hamburger span {
    display: block; width: 24px; height: 2px;
    background: #fff; border-radius: 2px;
    transition: all 0.3s;
  }
  .hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
  .hamburger.open span:nth-child(2) { opacity: 0; }
  .hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }
  .mobile-overlay {
    display: none; position: fixed; inset: 0; z-index: 150;
    background: rgba(0,0,0,0.5);
  }
  .mobile-overlay.show { display: block; }
  .mobile-nav {
    position: fixed; top: 0; left: -280px; width: 260px; height: 100vh;
    background: var(--primary); z-index: 160;
    overflow-y: auto; transition: left 0.3s ease;
    display: flex; flex-direction: column;
    padding-top: 60px;
  }
  .mobile-nav.open { left: 0; }

  @media (max-width: 900px) {
    .sidebar { display: none !important; }
    .main { margin-left: 0; padding-top: 56px; }
    .mobile-header { display: flex; }
    .hero { padding: 32px 20px 28px; }
    .hero h1 { font-size: 26px; }
    .content { padding: 0 16px 60px; }
    .two-col { grid-template-columns: 1fr; }
    .three-stat { grid-template-columns: 1fr; }
    .mode-grid { grid-template-columns: 1fr; }
    .card-grid { grid-template-columns: 1fr; }
    .param-grid { grid-template-columns: 1fr 1fr; }
  }
  @media (max-width: 480px) {
    .param-grid { grid-template-columns: 1fr; }
    .hero h1 { font-size: 22px; }
  }

</style>
</head>
<body>


<!-- 모바일 헤더 -->
<div class="mobile-header">
  <h2>Sunday Kerygma</h2>
  <button class="hamburger" id="hamburger" onclick="toggleMenu()" aria-label="메뉴">
    <span></span><span></span><span></span>
  </button>
</div>

<!-- 모바일 오버레이 -->
<div class="mobile-overlay" id="overlay" onclick="closeMenu()"></div>

<!-- 모바일 사이드 네비 -->
<div class="mobile-nav" id="mobileNav">
  <a class="nav-item" href="#signal-flow" onclick="closeMenu()"><span class="icon">🔄</span>신호 흐름 개요<span class="nav-num">01</span></a>
  <a class="nav-item" href="#microphone" onclick="closeMenu()"><span class="icon">🎤</span>Microphone<span class="nav-num">02</span></a>
  <a class="nav-item" href="#preamp" onclick="closeMenu()"><span class="icon">🎚️</span>PreAMP & HPF<span class="nav-num">03</span></a>
  <a class="nav-item" href="#gate" onclick="closeMenu()"><span class="icon">🚪</span>Gate<span class="nav-num">04</span></a>
  <a class="nav-item" href="#compressor" onclick="closeMenu()"><span class="icon">🎛️</span>Compressor<span class="nav-num">06</span></a>
  <a class="nav-item" href="#equalizer" onclick="closeMenu()"><span class="icon">📊</span>Equalizer<span class="nav-num">07</span></a>
  <a class="nav-item" href="#bus" onclick="closeMenu()"><span class="icon">🔀</span>Bus (Aux)<span class="nav-num">08</span></a>
  <a class="nav-item" href="#paning" onclick="closeMenu()"><span class="icon">↔️</span>Paning<span class="nav-num">09</span></a>
  <a class="nav-item" href="#reverb" onclick="closeMenu()"><span class="icon">🌊</span>Reverb<span class="nav-num">10</span></a>
  <a class="nav-item" href="#vocal-setting" onclick="closeMenu()"><span class="icon">👤</span>Vocal Setting<span class="nav-num">10</span></a>
  <a class="nav-item" href="#rotation-cases" onclick="closeMenu()"><span class="icon">🎭</span>Rotation Cases<span class="nav-num">11</span></a>
</div>

<nav class="sidebar">
  <div class="sidebar-brand">
    <h1>Sunday Kerygma</h1>
    <p>보컬 음향 운영 매뉴얼 v3</p>
  </div>
  <nav>
    <a class="nav-item" href="#signal-flow"><span class="icon">🔄</span>신호 흐름 개요<span class="nav-num">01</span></a>
    <a class="nav-item" href="#microphone"><span class="icon">🎤</span>Microphone<span class="nav-num">02</span></a>
    <a class="nav-item" href="#preamp"><span class="icon">🎚️</span>PreAMP & HPF<span class="nav-num">03</span></a>
    <a class="nav-item" href="#gate"><span class="icon">🚪</span>Gate<span class="nav-num">04</span></a>
    <a class="nav-item" href="#compressor"><span class="icon">🎛️</span>Compressor<span class="nav-num">05</span></a>
    <a class="nav-item" href="#equalizer"><span class="icon">📊</span>Equalizer<span class="nav-num">06</span></a>
    <a class="nav-item" href="#bus"><span class="icon">🔀</span>Bus (Aux)<span class="nav-num">07</span></a>
    <a class="nav-item" href="#paning"><span class="icon">↔️</span>Paning<span class="nav-num">08</span></a>
    <a class="nav-item" href="#reverb"><span class="icon">🌊</span>Reverb<span class="nav-num">09</span></a>
    <a class="nav-item" href="#vocal-setting"><span class="icon">👤</span>Vocal Setting<span class="nav-num">10</span></a>
    <a class="nav-item" href="#rotation-cases"><span class="icon">🎭</span>Rotation Cases<span class="nav-num">11</span></a>
  </nav>
</nav>

<div class="main">
<div class="hero">
  <div class="hero-tag">Audio Engineering Guide v3 · Midas Pro2C</div>
  <h1>Sunday Kerygma</h1>
  <p>보컬 음향 운영 완전 가이드 — Midas Pro2C 기준으로 최적화된 세팅값 포함</p>
  <div class="hero-flow">
    <span class="flow-step">🎤 MIC</span><span class="flow-arrow">→</span>
    <span class="flow-step">PreAMP</span><span class="flow-arrow">→</span>
    <span class="flow-step">Gate</span><span class="flow-arrow">→</span>
    <span class="flow-step">Compressor</span><span class="flow-arrow">→</span>
    <span class="flow-step">EQ</span><span class="flow-arrow">→</span>
    <span class="flow-step">Bus</span><span class="flow-arrow">→</span>
    <span class="flow-step">Reverb</span><span class="flow-arrow">→</span>
    <span class="flow-step">Paning</span><span class="flow-arrow">→</span>
    <span class="flow-step">Fader</span><span class="flow-arrow">→</span>
    <span class="flow-step">🔊 Output</span>
  </div>
</div>

<div class="content">

<!-- 01 신호 흐름 -->
<div class="section" id="signal-flow">
  <div class="section-header">
    <div class="section-icon">🔄</div>
    <div><div class="section-num">Chapter 01</div><h2>신호 흐름 개요 (Signal Flow)</h2></div>
  </div>
  <div class="two-col">
    <div class="flow-chart">
      <div class="flow-node"><div class="flow-node-num">1</div><div><div class="flow-node-label">Microphone</div><div class="flow-node-desc">음성 신호 수음</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">2</div><div><div class="flow-node-label">PreAMP / Gain</div><div class="flow-node-desc">신호 증폭 — Pro2C 기준 -20~-22dBFS</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">3</div><div><div class="flow-node-label">Gate</div><div class="flow-node-desc">불필요한 노이즈 차단</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">4</div><div><div class="flow-node-label">Compressor</div><div class="flow-node-desc">Pro2C 모드 선택 → 다이나믹 제어</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">5</div><div><div class="flow-node-label">Equalizer (EQ)</div><div class="flow-node-desc">Cut 우선 → 문제 대역 제거</div></div></div>
    </div>
    <div class="flow-chart">
      <div class="flow-node"><div class="flow-node-num">6</div><div><div class="flow-node-label">Bus (Aux)</div><div class="flow-node-desc">모니터 / 이펙트 라우팅</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">7</div><div><div class="flow-node-label">Reverb</div><div class="flow-node-desc">빠른/느린 노래 구분 세팅</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">8</div><div><div class="flow-node-label">Paning</div><div class="flow-node-desc">좌우 공간 배치</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">9</div><div><div class="flow-node-label">Fader</div><div class="flow-node-desc">최종 볼륨 조절</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">10</div><div><div class="flow-node-label">DCA</div><div class="flow-node-desc">채널 그룹 컨트롤</div></div></div>
      <div class="flow-connector"></div>
      <div class="flow-node"><div class="flow-node-num">11</div><div><div class="flow-node-label">Graphic EQ (GEQ)</div><div class="flow-node-desc">출력 전 최종 보정</div></div></div>
    </div>
  </div>
</div>

<!-- 02 마이크 -->
<div class="section" id="microphone">
  <div class="section-header">
    <div class="section-icon">🎤</div>
    <div><div class="section-num">Chapter 02</div><h2>Microphone (마이크)</h2></div>
  </div>
  <div class="card-grid">
    <div class="card"><div class="card-title"><span class="dot"></span>Cardioid (단일지향성)</div><ul><li>앞에서 오는 소리를 가장 잘 받음</li><li>보컬, 설교 — 가장 일반적</li><li>옆·뒤 소리 자연스럽게 차단</li></ul></div>
    <div class="card"><div class="card-title"><span class="dot"></span>Super/Hyper Cardioid (초지향성)</div><ul><li>앞쪽 매우 좁은 범위만 수음</li><li>시끄러운 환경, 무대 보컬에 유리</li></ul></div>
    <div class="card"><div class="card-title"><span class="dot"></span>근접효과 (Proximity Effect)</div><ul><li>마이크 가까울수록 저음 강해짐</li><li>보컬 기준 <strong>10~15cm 거리 유지</strong></li><li>200~300Hz 뭉침 → EQ로 보정</li></ul></div>
  </div>
  <div style="display:flex;gap:12px;flex-wrap:wrap;margin-top:8px">
    <span class="tag tag-blue">Shure Beta 58A (다이나믹)</span>
    <span class="tag tag-blue">Shure Beta 87A (콘덴서)</span>
    <span class="tag tag-green">무선 (Wireless) 지원</span>
  </div>
</div>

<!-- 03 PreAMP & HPF -->
<div class="section" id="preamp">
  <div class="section-header">
    <div class="section-icon">🎚️</div>
    <div><div class="section-num">Chapter 03</div><h2>PreAMP & HPF (프리앰프 / 하이패스 필터)</h2></div>
  </div>

  <div class="subheading">3.1 Gain (게인) — Pro2C 기준</div>
  <div class="pro2c-box"><div class="label">⚙️ Midas Pro2C 기준</div>Pro2C는 헤드룸이 넉넉해 노이즈가 적습니다. 일반 기준(-18dBFS)보다 보수적으로 잡아도 충분합니다.<br><strong>권장 게인: -20~-22dBFS 부근</strong></div>
  <div class="three-stat">
    <div class="stat-box"><div class="stat-label">게인 너무 높으면</div><div class="stat-value" style="color:#e53935;font-size:16px">Clipping</div><div class="stat-desc">소리 찢어짐 발생</div></div>
    <div class="stat-box"><div class="stat-label">Pro2C 권장</div><div class="stat-value">-20~-22</div><div class="stat-desc">dBFS 부근</div></div>
    <div class="stat-box"><div class="stat-label">게인 너무 낮으면</div><div class="stat-value" style="color:#888;font-size:16px">Noise</div><div class="stat-desc">힘 없는 소리</div></div>
  </div>

  <div class="subheading">3.2 HPF — Pro2C 24dB/oct 기준</div>
  <div class="pro2c-box"><div class="label">⚙️ Midas Pro2C HPF 특성</div>Pro2C HPF 슬로프는 <strong>24dB/oct</strong>로 가파릅니다. X32/M32(12dB/oct)보다 훨씬 강하게 잘리므로 <strong>같은 주파수라도 10~20Hz 낮게</strong> 설정해야 자연스럽습니다.</div>
  <div class="two-col" style="margin-top:16px">
    <div class="card">
      <div class="card-title"><span class="dot"></span>소편성 / 보컬 위주</div>
      <p style="font-size:22px;font-weight:800;color:#e65100;margin:8px 0">80~150Hz</p>
      <p>남성 80~100Hz / 여성 120~150Hz</p>
    </div>
    <div class="card" style="border:2px solid var(--secondary)">
      <div class="card-title"><span class="dot"></span>풀밴드 (찬양팀) ★ Pro2C 보정값</div>
      <p style="font-size:22px;font-weight:800;color:#1F4E79;margin:8px 0">130~180Hz</p>
      <p>남성 <strong>130~170Hz</strong> / 여성 <strong>150~180Hz</strong><br><span style="font-size:12px;color:var(--text-muted)">※ 일반 기준(150~200Hz)보다 10~20Hz 낮게 설정</span></p>
    </div>
  </div>
  <div class="tip-box">💡 컷오프 = -3dB 지점. 그 아래가 전부 사라지는 게 아닙니다. 180Hz 설정 시 150~200Hz는 대부분 살아 있습니다. Pro2C는 기울기가 가파르므로 더욱 주의.</div>
</div>

<!-- 04 Gate -->
<div class="section" id="gate">
  <div class="section-header">
    <div class="section-icon">🚪</div>
    <div><div class="section-num">Chapter 04</div><h2>Gate (게이트)</h2></div>
  </div>
  <div class="info-box"><div class="label">정의</div>소리가 일정 크기 이상일 때만 문을 열어 주는 장치 — <strong>"소리 전용 자동문"</strong></div>
  <div class="param-grid">
    <div class="param-card"><div class="param-name">Threshold</div><div class="param-q">어느 크기부터 열릴까?</div><div class="param-desc">낮게 → 작은 소리도 열림 / 높게 → 큰 소리만 열림</div></div>
    <div class="param-card"><div class="param-name">Attack</div><div class="param-q">문이 얼마나 빨리 열릴까?</div><div class="param-desc">빠르면 정확 / 너무 느리면 앞부분 잘림</div></div>
    <div class="param-card"><div class="param-name">Hold</div><div class="param-q">문이 얼마나 유지될까?</div><div class="param-desc">너무 짧으면 뚝뚝 끊김</div></div>
    <div class="param-card"><div class="param-name">Release</div><div class="param-q">문이 얼마나 부드럽게 닫힐까?</div><div class="param-desc">빠르면 뚝 끊김 / 느리면 자연스럽게 사라짐</div></div>
  </div>
</div><!-- 06 Compressor -->
<div class="section" id="compressor">
  <div class="section-header">
    <div class="section-icon">🎛️</div>
    <div><div class="section-num">Chapter 05</div><h2>Compressor (컴프레서) — Midas Pro2C 모드</h2></div>
  </div>
  <div class="pro2c-box"><div class="label">⚙️ Midas Pro2C 내장 컴프레서</div>Pro2C는 아날로그 모델링 품질의 내장 컴프레서를 5가지 모드로 제공합니다. 외장 컴프 개념(CLA-76, dbx160)을 Pro2C 모드명으로 직접 매핑하여 사용합니다.</div>

  <div class="subheading">6.1 Pro2C 컴프레서 5가지 모드</div>
  <div style="display:flex;flex-direction:column;gap:16px;margin:16px 0;">

    <!-- MODE 1 -->
    <div class="mode-card mode-1" style="border-radius:14px;padding:20px 24px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="background:#e53935;color:#fff;border-radius:8px;padding:3px 12px;font-size:12px;font-weight:800;flex-shrink:0;">MODE 1</div>
        <div>
          <div style="font-size:16px;font-weight:800;color:#b71c1c;">Corrective mode</div>
          <div style="font-size:12px;color:#888;">Exponential Peak – Fast</div>
        </div>
        <span class="mode-apply" style="background:#b71c1c;color:#fff;margin-left:auto;padding:4px 12px;border-radius:8px;">→ 유직 (메인보컬) ★</span>
      </div>
      <p style="font-size:13.5px;color:#5a2020;line-height:1.8;">피크 감지 방식의 컴프레서로, 지수형(exponential) 어택과 릴리스를 사용합니다. 매우 빠른 어택으로 다이나믹 소재를 공격적으로 제어하며 트랜지언트를 잘 포착합니다. 저주파 신호에 컬러를 더할 수 있어 베이스 기타처럼 다이나믹 레인지가 넓은 악기에 이상적입니다. <strong>빠른 어택 설정으로 트랜지언트를 포착</strong>하고, 릴리스는 펌핑·왜곡을 조절하며 취향에 맞게 조정하세요.</p>
    </div>

    <!-- MODE 2 -->
    <div class="mode-card mode-2" style="border-radius:14px;padding:20px 24px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="background:#2e7d32;color:#fff;border-radius:8px;padding:3px 12px;font-size:12px;font-weight:800;flex-shrink:0;">MODE 2</div>
        <div>
          <div style="font-size:16px;font-weight:800;color:#1b5e20;">Adaptive mode</div>
          <div style="font-size:12px;color:#888;">Exponential RMS – Accurate</div>
        </div>
        <span class="mode-apply" style="background:#2e7d32;color:#fff;margin-left:auto;padding:4px 12px;border-radius:8px;">→ 선택적 사용</span>
      </div>
      <p style="font-size:13.5px;color:#1b3a1c;line-height:1.8;">RMS(실효값) 감지 방식으로, 지수형 어택·릴리스와 결합해 매우 적응적인 엔벨로프 특성을 만들어냅니다. 큰 신호(임계값 초과)에는 빠르게 반응하고 작은 신호에는 느리게 반응해 어택 타임 설정이 크게 중요하지 않습니다. 대부분의 소스에서 세팅이 매우 빠르고 간단하며, <strong>보컬과 다양한 소스에 소닉 정확도가 높고 자연스러운 압축</strong>을 제공합니다. 가장 자연스러운 사운드는 <em>soft knee</em> 설정에서 나옵니다.</p>
    </div>

    <!-- MODE 3 -->
    <div class="mode-card mode-3" style="border-radius:14px;padding:20px 24px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="background:#4472C4;color:#fff;border-radius:8px;padding:3px 12px;font-size:12px;font-weight:800;flex-shrink:0;">MODE 3</div>
        <div>
          <div style="font-size:16px;font-weight:800;color:#1F4E79;">Creative mode</div>
          <div style="font-size:12px;color:#888;">Linear Peak – Slow</div>
        </div>
        <span class="mode-apply" style="background:#1F4E79;color:#fff;margin-left:auto;padding:4px 12px;border-radius:8px;">→ 백보컬 전원 ★</span>
      </div>
      <p style="font-size:13.5px;color:#1a2236;line-height:1.8;">선형(dB율) 어택과 2차 릴리스를 사용하는 피크 감지 컴프레서입니다. <strong>매우 투명</strong>해서 소스 소재의 의도적인 다이나믹 콘텐츠를 크게 해치지 않으면서 압축을 제공합니다. 선형 어택은 일정한 압축 속도를 가져, 큰 신호 변화가 작은 변화보다 압축되는 데 더 오래 걸립니다. <em>Soft knee</em> 설정 시 어택이 더욱 지연되어 드럼의 트랜지언트를 살리면서 펀치감을 강조할 수 있습니다. 어쿠스틱 기타처럼 다루기 까다로운 악기에는 <strong>느린 어택 + 빠른 릴리스</strong>로 과도한 플러터나 왜곡 없이 균일한 음량을 유지할 수 있습니다.</p>
    </div>

    <!-- MODE 4 -->
    <div class="mode-card mode-4" style="border-radius:14px;padding:20px 24px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="background:#f9a825;color:#fff;border-radius:8px;padding:3px 12px;font-size:12px;font-weight:800;flex-shrink:0;">MODE 4</div>
        <div>
          <div style="font-size:16px;font-weight:800;color:#e65100;">Vintage mode</div>
          <div style="font-size:12px;color:#888;">Adaptive Peak – Bright</div>
        </div>
        <span class="mode-apply" style="background:#e65100;color:#fff;margin-left:auto;padding:4px 12px;border-radius:8px;">→ 특별한 컬러 원할 때</span>
      </div>
      <p style="font-size:13.5px;color:#4a2000;line-height:1.8;">부분적으로 적응형 특성을 가진 피크 감지 컴프레서로, 압축 시작 시 엔벨로프 설정에 독립적인 극히 미묘한 어택·릴리스 곡선을 만들어냅니다. 신호가 임계값을 크게 초과할수록 어택·릴리스가 더 공격적이 되고 점차 수동 제어로 복귀합니다. <strong>압축 중 하모닉 배음을 의도적으로 증가</strong>시켜 <em>밸브(진공관)</em>처럼 밝고 생동감 있는 소리를 더하며, 어쿠스틱 악기에 매우 자연스럽고 생동감 있는 압축을 제공합니다.</p>
    </div>

    <!-- MODE 5 -->
    <div class="mode-card mode-5" style="border-radius:14px;padding:20px 24px;">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="background:#8e24aa;color:#fff;border-radius:8px;padding:3px 12px;font-size:12px;font-weight:800;flex-shrink:0;">MODE 5</div>
        <div>
          <div style="font-size:16px;font-weight:800;color:#6a1b9a;">Shimmer mode</div>
          <div style="font-size:12px;color:#888;">Overshoot Peak – Slow · 출력 전용</div>
        </div>
        <span class="mode-apply" style="background:#6a1b9a;color:#fff;margin-left:auto;padding:4px 12px;border-radius:8px;">→ 버스 선택 적용</span>
      </div>
      <p style="font-size:13.5px;color:#2e0050;line-height:1.8;">지수형 릴리스와 독특한 2차 어택(overshoot) 특성을 가진 피크 감지 컴프레서입니다. 절제해서 사용하면 매우 부드럽고 자연스러우며, 이미 다이나믹 레인지가 낮은 소재에 추가적인 제어를 제공합니다. <strong>보컬에서 퍼포먼스의 생동감을 유지하면서도 투명하게 작동</strong>합니다. 높은 레이쇼와 느린 어택 + 빠른 릴리스 조합에서는 매우 부드럽고 바운시한 사운드를 만들어냅니다.</p>
    </div>

  </div>

  <div class="subheading">6.2 이 팀 컴프레서 적용 요약</div>
  <div class="two-col">
    <div class="hl-blue">
      <div class="hl-title">🎤 메인보컬 (유직) — Mode 1 Corrective</div>
      <div class="hl-sub">피크 감지 · 빠른 어택 · 선명한 존재감</div>
      <ul style="font-size:13.5px;color:var(--text-muted);padding-left:18px;line-height:2">
        <li>빠른 어택으로 <strong>다이나믹 피크 정확하게 제어</strong></li>
        <li>Pro2C 아날로그 모델링 → 5ms도 부드럽게 작동</li>
        <li>Attack: <strong>5~10ms</strong> / Ratio: 4:1 / Release: 200ms</li>
        <li>GR 목표: 크게 부르는 파트에서 <strong>-5dB 부근</strong></li>
      </ul>
    </div>
    <div class="hl-green">
      <div class="hl-title-green">🎙️ 백보컬 전원 — Mode 2 / Mode 3</div>
      <div class="hl-sub">투명하고 균일 · 메인보컬 방해 안 함</div>
      <ul style="font-size:13.5px;color:var(--text-muted);padding-left:18px;line-height:2">
        <li>백보컬 전원: <strong>Mode 3 Creative</strong> (Linear Peak – Slow · 투명하고 균일)</li>
        <li>Attack: <strong>10~15ms</strong> / Ratio: 4:1 / Release: 200ms</li>
        <li>GR 목표: <strong>-3~-5dB</strong> 부근</li>
      </ul>
    </div>
  </div>

  <div class="subheading">6.3 컴프레서 세팅 순서 (Pro2C 기준)</div>
  <div class="info-box"><div class="label">세팅 순서</div>
    ① Mode 선택 → ② Ratio 4:1로 시작 → ③ Threshold 내려서 GR 확인<br>
    → ④ 크게 부르는 파트에서 <strong>GR -5dB(메인) / -3~5dB(백보컬) 목표</strong><br>
    → ⑤ Makeup Gain으로 줄어든 게인 보충 → ⑥ Attack/Release 세부 조정<br>
    → ⑦ 예배 때 GR 양 재확인
  </div>
</div>

<!-- 07 EQ -->
<div class="section" id="equalizer">
  <div class="section-header">
    <div class="section-icon">📊</div>
    <div><div class="section-num">Chapter 06</div><h2>Equalizer (이퀄라이저)</h2></div>
  </div>

  <div class="subheading">7.1 EQ 기본 원칙 — Cut 우선</div>
  <div class="warn-box">⚠️ <strong>초보자가 가장 많이 하는 실수:</strong> "저음 줄이니 쏘고, 고음 줄이니 먹먹해요"<br>→ EQ를 과도하게 조작해서 생기는 왜곡 문제입니다. <strong>한 번에 -2~3dB씩, 반드시 전/후 비교하세요.</strong></div>
  <div class="pro2c-box"><div class="label">⚙️ Pro2C EQ 특성</div>Midas 계열 아날로그 감성 EQ — 같은 dB 수치라도 더 자연스럽게 들립니다. -2~3dB만 잘라도 충분히 효과가 납니다. 과도하게 자르면 오히려 너무 얇아질 수 있으니 주의.</div>

  <div class="subheading">7.2 주요 문제 대역 & Cut 기준</div>
  <div class="three-stat">
    <div class="stat-box">
      <div class="stat-label">뭉치는 소리</div>
      <div class="stat-value">200~500Hz</div>
      <div class="stat-desc">-2~4dB 컷 / 먹먹함의 원인</div>
    </div>
    <div class="stat-box">
      <div class="stat-label">코맹맹이 소리</div>
      <div class="stat-value">600Hz~1kHz</div>
      <div class="stat-desc">-2~3dB 컷 / 답답함의 원인</div>
    </div>
    <div class="stat-box">
      <div class="stat-label">날카로운 치찰음</div>
      <div class="stat-value">8~12kHz</div>
      <div class="stat-desc">-3~6dB 컷 / ㅅ·ㅊ 찌를 때</div>
    </div>
  </div>

  <div class="subheading">7.3 EQ 트러블슈팅 — 채널 EQ 많이 만지기 전에</div>
  <div class="two-col">
    <div>
      <div class="ts-flow">
        <div class="ts-node" style="background:#fdecea;border-color:#e53935">
          <div class="ts-node-q">EQ를 많이 만지고 있다?</div>
          <div class="ts-node-desc">채널 EQ 건드리기 전에 아래 순서로 먼저 확인</div>
        </div>
        <div class="ts-connector"></div>
        <div class="ts-node">
          <div class="ts-node-q"><span class="ts-num">1</span>공간(룸튜닝) 확인</div>
          <div class="ts-node-desc">흡음·반사 패널, 스피커 위치</div>
        </div>
        <div class="ts-connector"></div>
        <div class="ts-node">
          <div class="ts-node-q"><span class="ts-num">2</span>메인 스피커 GEQ 확인</div>
          <div class="ts-node-desc">시스템 EQ 세팅 먼저 점검</div>
        </div>
        <div class="ts-connector"></div>
        <div class="ts-node">
          <div class="ts-node-q"><span class="ts-num">3</span>채널 EQ</div>
          <div class="ts-node-desc">200~300Hz 저음 뭉침 (근접효과) 보정</div>
        </div>
      </div>
      <div class="tip-box" style="margin-top:8px">순서를 지키면 채널 EQ는 최소한으로 끝납니다</div>
    </div>
    <div>
      <div class="card" style="margin-bottom:12px">
        <div class="card-title"><span class="dot"></span>백보컬 여러 명일 때 EQ 팁</div>
        <p>보컬이 여러 명이면 <strong>미들하이(2~5kHz)</strong>를 보컬마다 분산 조절하세요. 동일 EQ를 일괄 적용하면 특정 대역이 뭉칩니다.</p>
      </div>
      <div class="card">
        <div class="card-title"><span class="dot"></span>저음 뭉침 (200~300Hz) 보정</div>
        <p>근접효과로 인한 뭉침 — 라이브에선 게인 확보를 위해 마이크를 붙이는 게 맞으니 EQ로 보정합니다.<br><strong>남성 200Hz / 여성 300Hz 부근 -3~6dB 컷</strong></p>
      </div>
    </div>
  </div>

  <div class="subheading">7.4 주파수 대역별 특성</div>
  <div class="table-wrap"><table>
    <thead><tr><th>대역</th><th>주파수</th><th>특징</th><th>대표 악기</th></tr></thead>
    <tbody>
      <tr><td>서브베이스</td><td>40~80Hz</td><td>파워풀한 저음</td><td>킥 드럼, 베이스 기타</td></tr>
      <tr><td>저음 (바디)</td><td>80~120Hz</td><td>저음의 몸통, 존재감</td><td>킥 펀치, 베이스 바디</td></tr>
      <tr><td>중저역</td><td>120~250Hz</td><td>따뜻한 느낌 / 혼탁함</td><td>일렉기타, 건반, 저음 보컬</td></tr>
      <tr><td>로우 미드</td><td>250~500Hz</td><td>충만감 / <strong>뭉치는 소리 주범</strong></td><td>기타, 보컬, 키보드</td></tr>
      <tr><td>미드</td><td>500Hz~1kHz</td><td>악기의 본질적 톤 / <strong>코맹맹이</strong></td><td>보컬 중역, 스네어</td></tr>
      <tr><td>하이 미드</td><td>1~2kHz</td><td>명확한 음색</td><td>기타, 보컬 선명도</td></tr>
      <tr><td>존재감 대역</td><td>2~4kHz</td><td>음의 핵심 / 청각 피로</td><td>보컬 어택, 스네어</td></tr>
      <tr><td>고역</td><td>4~8kHz</td><td>밝고 쏘는 소리</td><td>하이햇, 보컬 치찰음</td></tr>
      <tr><td>에어</td><td>8~16kHz+</td><td><strong>치찰음 · 공기감</strong></td><td>리버브 잔향, 보컬 숨소리</td></tr>
    </tbody>
  </table></div>
</div>

<!-- 08 Bus -->
<div class="section" id="bus">
  <div class="section-header">
    <div class="section-icon">🔀</div>
    <div><div class="section-num">Chapter 07</div><h2>Bus (Aux)</h2></div>
  </div>
  <div class="table-wrap"><table>
    <thead><tr><th>버스 종류</th><th>역할</th><th>Pre/Post</th><th>사용 예</th></tr></thead>
    <tbody>
      <tr><td>Monitor Bus</td><td>연주자·보컬 모니터 (인이어, 스테이지 스피커)</td><td><span class="tag tag-orange">Pre-Fader</span></td><td>보컬: 보컬 크게 / 기타: 기타 크게</td></tr>
      <tr><td>FX Bus (Aux)</td><td>리버브·딜레이 이펙트 전송</td><td><span class="tag tag-green">Post-Fader</span></td><td>여러 악기 → 공통 리버브</td></tr>
      <tr><td>Group Bus</td><td>여러 채널 묶어 함께 조절</td><td><span class="tag tag-green">Post-Fader</span></td><td>드럼 버스, 보컬 버스</td></tr>
      <tr><td>Matrix Bus</td><td>다른 공간 출력</td><td><span class="tag tag-green">Post-Fader</span></td><td>예배당/로비 스피커</td></tr>
    </tbody>
  </table></div>
  <div class="card-grid" style="margin-top:16px">
    <div class="card"><div class="card-title"><span class="dot"></span>Pre-Fader</div><p>원래 트랙 볼륨과 상관없이 Bus로 일정하게 보냄<br><strong>→ 연주자 모니터 Bus에 항상 사용</strong></p></div>
    <div class="card"><div class="card-title"><span class="dot"></span>Post-Fader</div><p>원래 트랙 볼륨 기준으로 Bus 양이 따라 변함<br><strong>→ 리버브·딜레이 FX Bus에 항상 사용</strong></p></div>
  </div>
</div>

<!-- 09 Paning -->
<div class="section" id="paning">
  <div class="section-header">
    <div class="section-icon">↔️</div>
    <div><div class="section-num">Chapter 08</div><h2>Paning (패닝)</h2></div>
  </div>
  <div class="warn-box">⚠️ <strong>핵심:</strong> 드럼(킥·베이스·스네어) 센터 점유 + 메인보컬 남성 → 남성 백보컬은 반드시 <strong>±50 이상</strong> 분리 필요</div>
  <div class="table-wrap"><table>
    <thead><tr><th>멤버</th><th>성별</th><th>패닝 (라이브)</th><th>이유</th></tr></thead>
    <tbody>
      <tr><td>유직 (리더·메인)</td><td>남</td><td><strong>CENTER</strong></td><td>항상 센터 고정</td></tr>
      <tr><td>상원 (15dB·IEM)</td><td>남</td><td><strong>R 50</strong></td><td>메인(남)과 음색 겹침 → ±50 충분히 분리</td></tr>
      <tr><td>영민 (10dB·SPK)</td><td>남</td><td><strong>L 50</strong></td><td>상원 대칭. 음량 약하므로 너무 멀지 않게</td></tr>
      <tr><td>상미 (15dB·IEM)</td><td>여</td><td><strong>L 20~25</strong></td><td>리더 좌측 근접 서포트</td></tr>
      <tr><td>은화 (10dB·IEM)</td><td>여</td><td><strong>R 20~25</strong></td><td>상미 대칭. 음량 약해 센터 가까이</td></tr>
      <tr><td>경하 (15dB·IEM)</td><td>여</td><td><strong>L 50</strong></td><td>중간 공간 채움</td></tr>
      <tr><td>지현 (15dB·IEM)</td><td>여</td><td><strong>R 50</strong></td><td>경하 대칭</td></tr>
      <tr><td>다원 (15dB·IEM)</td><td>여</td><td><strong>L 80~87</strong></td><td>가장 넓은 공간감 담당</td></tr>
    </tbody>
  </table></div>
  <div class="info-box"><div class="label">라이브 vs DAW</div><strong>라이브는 넓게 / DAW는 좁게</strong> — 라이브는 공간 반사로 패닝 효과가 희석되어 과감하게 벌려야 효과가 납니다. DAW 작업 시 위 수치보다 20~30% 좁게 설정하세요.</div>
</div>

<!-- 10 Reverb -->
<div class="section" id="reverb">
  <div class="section-header">
    <div class="section-icon">🌊</div>
    <div><div class="section-num">Chapter 09</div><h2>Reverb (리버브)</h2></div>
  </div>
  <div class="info-box"><div class="label">핵심</div>많이 넣으면 멋지지만 과하면 바로 뭉개집니다. <strong>Pre-Delay와 Decay가 핵심</strong> — 빠른 곡과 느린 곡을 나눠서 세팅해두고 사용하세요.</div>

  <div class="subheading">10.1 빠른 노래 vs 느린 노래 구분 세팅</div>
  <div class="two-col">
    <div class="card" style="border:2px solid #2E75B6">
      <div class="card-title"><span class="dot"></span>빠른 노래</div>
      <p style="font-size:24px;font-weight:800;color:#e65100;margin:8px 0">1.8~2.0s</p>
      <p>Pre-Delay: <strong>50~100ms</strong> / 명료도 높임</p>
    </div>
    <div class="card" style="border:2px solid #8e24aa">
      <div class="card-title"><span class="dot"></span>느린 노래</div>
      <p style="font-size:24px;font-weight:800;color:#8e24aa;margin:8px 0">2.3~3.0s</p>
      <p>Pre-Delay: <strong>25~100ms</strong> / 길고 풍성하게</p>
    </div>
  </div>

  <div class="subheading">10.2 이 팀의 실제 운영값</div>
  <div class="two-col">
    <div class="hl-blue">
      <div class="hl-title">🎤 메인보컬 (유직) — Plate Reverb</div>
      <div class="hl-sub">실제 운영 세팅값</div>
      <div class="table-wrap" style="margin-top:10px"><table style="font-size:13px">
        <thead><tr><th>파라미터</th><th>값</th></tr></thead>
        <tbody>
          <tr><td>Type</td><td>Plate</td></tr>
          <tr><td>Pre-Delay</td><td><strong>100ms</strong></td></tr>
          <tr><td>Decay (빠른 곡)</td><td><strong>2.0s</strong></td></tr>
          <tr><td>Decay (느린 곡)</td><td><strong>2.5s</strong></td></tr>
          <tr><td>Mix (Wet)</td><td>15~20%</td></tr>
          <tr><td>Bus</td><td>Post-Fader FX Bus</td></tr>
        </tbody>
      </table></div>
    </div>
    <div class="hl-green">
      <div class="hl-title-green">🎙️ 백보컬 전원 — Plate Reverb</div>
      <div class="hl-sub">메인보컬보다 짧게 · 공간 겹침 방지</div>
      <div class="table-wrap" style="margin-top:10px"><table style="font-size:13px">
        <thead><tr><th>파라미터</th><th>값</th></tr></thead>
        <tbody>
          <tr><td>Type</td><td>Plate</td></tr>
          <tr><td>Pre-Delay</td><td><strong>60~80ms</strong></td></tr>
          <tr><td>Decay (빠른 곡)</td><td><strong>1.2~1.5s</strong></td></tr>
          <tr><td>Decay (느린 곡)</td><td><strong>1.8s</strong></td></tr>
          <tr><td>Mix (Wet)</td><td>10~12%</td></tr>
          <tr><td>Bus</td><td>Post-Fader FX Bus (별도)</td></tr>
        </tbody>
      </table></div>
    </div>
  </div>

  <div class="subheading">10.3 Abbey Road Reverb Trick</div>
  <div class="card-grid">
    <div class="card">
      <div class="card-title"><span class="dot"></span>Send 버스 EQ</div>
      <p>리버브로 보내기 전에 <strong>로우컷 + 하이컷</strong>으로 불필요한 대역 제거. 리버브가 깔끔해짐.</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="dot"></span>FX 리턴 채널 EQ</div>
      <p>리버브가 돌아온 뒤 <strong>리버브 톤을 적극적으로 쉐이핑</strong>하여 믹스에 맞춤.</p>
    </div>
  </div>
  <div class="info-box"><div class="label">신호 흐름</div>입력 채널 → Send 버스 (EQ) → 리버브 → FX 리턴 채널 (EQ) → 메인 출력</div>
</div>

<!-- 11 Vocal Setting -->
<div class="section" id="vocal-setting">
  <div class="section-header">
    <div class="section-icon">👤</div>
    <div><div class="section-num">Chapter 10</div><h2>Vocal Setting (보컬별 세팅값)</h2></div>
  </div>

  <div class="subheading">11.1 컴프레서 세팅 — 주일 (Sunday)</div>
  <div class="table-wrap"><table>
    <thead><tr><th>보컬</th><th>역할</th><th>Pro2C 모드</th><th>Attack</th><th>Ratio</th><th>Threshold</th><th>Release</th><th>GR 목표</th></tr></thead>
    <tbody>
      <tr><td>유직</td><td><span class="tag tag-red">메인보컬</span></td><td><strong>Mode 1 Corrective</strong></td><td>5~10ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-5dB</td></tr>
      <tr><td>상원</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>영민</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>다원</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>지현</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>상미</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>은화</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
      <tr><td>경하</td><td><span class="tag tag-blue">백보컬</span></td><td><strong>Mode 3 Creative</strong></td><td>10~15ms</td><td>4:1</td><td>-3dB</td><td>200ms</td><td>-3~5dB</td></tr>
    </tbody>
  </table></div>

  <div class="subheading">11.2 EQ 세팅값 — 주일 (Sunday)</div>
  <div class="pro2c-box"><div class="label">⚙️ Pro2C EQ 적용 주의</div>Pro2C는 아날로그 감성 EQ로 수치 효과가 더 자연스럽게 적용됩니다. 아래 수치 적용 후 반드시 전/후 비교 청취하세요.</div>
  <div class="table-wrap"><table>
    <thead><tr><th>보컬</th><th>Gain</th><th>Low Cut (HPF)</th><th>LO (Hz/dB)</th><th>ML (Hz/dB)</th><th>MH (Hz/dB)</th><th>HI (Hz/dB)</th></tr></thead>
    <tbody>
      <tr><td>유직</td><td>22</td><td>95</td><td>240 / -10</td><td>470 / -8</td><td>1000 / -4</td><td>2300 / -2</td></tr>
      <tr><td>영민</td><td>10~12.5</td><td>95</td><td>200 / -10</td><td>470 / -8</td><td>1000 / -4</td><td>2100 / -2</td></tr>
      <tr><td>상원</td><td>10~12.5</td><td>95</td><td>200 / -10</td><td>470 / -8</td><td>1000 / -4</td><td>2100 / -2</td></tr>
      <tr><td>다원</td><td>15~17.5</td><td>100</td><td>250 / -12</td><td>500 / -8</td><td>1000 / -4</td><td>2300 / -1</td></tr>
      <tr><td>지현</td><td>15~17.5</td><td>90</td><td>220 / -11</td><td>490 / -7</td><td>950 / -4</td><td>2200 / -1</td></tr>
      <tr><td>상미</td><td>15~17.5</td><td>90</td><td>210 / -10</td><td>490 / -7</td><td>1100 / -4</td><td>2200 / -1</td></tr>
      <tr><td>은화</td><td>10~12.5</td><td>85</td><td>200 / -12</td><td>450 / -8</td><td>950 / -4</td><td>2000 / -1.5</td></tr>
      <tr><td>경하</td><td>15~17.5</td><td>100</td><td>230 / -11</td><td>500 / -8</td><td>1000 / -4</td><td>2200 / -1.5</td></tr>
    </tbody>
  </table></div>

  <div class="subheading">11.3 EQ 세팅값 — 금철 (Friday)</div>
  <div class="table-wrap"><table>
    <thead><tr><th>보컬</th><th>Low Cut</th><th>LO (Hz/dB)</th><th>ML (Hz/dB)</th><th>MH (Hz/dB)</th><th>HI (Hz/dB)</th></tr></thead>
    <tbody>
      <tr><td>신환</td><td>90</td><td>250 / -10</td><td>550 / -6</td><td>1000 / -3</td><td>2300 / -1</td></tr>
      <tr><td>동한</td><td>95</td><td>230 / -10</td><td>480 / -7</td><td>1000 / -4</td><td>2000 / -1</td></tr>
      <tr><td>희준</td><td>100</td><td>200 / -10</td><td>450 / -7</td><td>900 / -3</td><td>1800 / -1</td></tr>
      <tr><td>하은</td><td>90</td><td>210 / -11</td><td>430 / -8</td><td>900 / -4</td><td>1800 / -1</td></tr>
    </tbody>
  </table></div>

  <div class="subheading">11.4 모노 IEM 소스 레벨 믹스값 (공통 기준)</div>
  <div class="pro2c-box"><div class="label">📌 모노 IEM 기준</div>Vocal = <strong>0dB 기준점</strong> · 패닝 없음 · 레벨과 EQ로만 분리 · 소스는 최소한으로 · 전체 멤버 공통 적용</div>
  <div class="table-wrap"><table>
    <thead><tr><th>소스</th><th>레벨</th></tr></thead>
    <tbody>
      <tr><td><strong>Vocal</strong></td><td><strong style="color:#e65100;font-size:16px">0 dB</strong></td></tr>
      <tr><td>Leader</td><td><strong style="color:#1F4E79;font-size:15px">-3 dB</strong></td></tr>
      <tr><td>Drum (Kick)</td><td><strong style="color:#1F4E79;font-size:15px">-5 dB</strong></td></tr>
      <tr><td>Drum (Snare)</td><td><strong style="color:#1F4E79;font-size:15px">-5 dB</strong></td></tr>
      <tr><td>Bass</td><td><strong style="color:#2E75B6;font-size:15px">-6 dB</strong></td></tr>
      <tr><td>EG (일렉기타)</td><td><strong style="color:#2E75B6;font-size:15px">-8 dB</strong></td></tr>
      <tr><td>Nord</td><td><strong style="color:#2E75B6;font-size:15px">-7 dB</strong></td></tr>
      <tr><td>MODX7</td><td><strong style="color:#888;font-size:15px">-9 dB</strong></td></tr>
    </tbody>
  </table></div>
  <div class="tip-box">💡 <strong>우선순위:</strong> Vocal(0) → Leader(-3) → Kick·Snare(-5) → Bass(-6) → Nord(-7) → EG(-8) → MODX7(-9)<br>뭉개지면 <strong>MODX7부터 하나씩 제거</strong>하세요.</div>
  <div class="subheading">11.5 IEM 채널 구성</div>
  <div class="table-wrap"><table>
    <thead><tr><th>채널</th><th>믹스 구성</th><th>수신 멤버</th></tr></thead>
    <tbody>
      <tr><td><span class="tag tag-blue">CH A</span></td><td>여성 보컬 중심 믹스</td><td>은화 · 상미 · 지현 · 경하 · 다원</td></tr>
      <tr><td><span class="tag tag-green">CH B</span></td><td>남성 보컬 중심 믹스</td><td>상원</td></tr>
      <tr><td><span class="tag tag-orange">CH C</span></td><td>풀 믹스 (병행 멤버 보조용)</td><td>인이어+스피커 병행 멤버</td></tr>
    </tbody>
  </table></div>
  <div class="tip-box">🎧 영민은 인이어 미사용 — 좌우 모니터 스피커(모노 2채널)만 사용. 스피커 믹스에 영민 보컬을 충분히 올려주세요.</div>
</div>



<!-- Rotation Cases -->
<div class="section" id="rotation-cases">
  <div class="section-header">
    <div class="section-icon">🎭</div>
    <div><div class="section-num">Chapter 11</div><h2>Rotation Cases — 보조인도자 편성</h2></div>
  </div>
  <div class="info-box"><div class="label">원칙</div>
    영민·상원은 항상 백보컬 · <strong>영민 좌끝 / 상원 우끝 고정</strong><br>
    보조인도자(다원·지현·상미·은화 중 1명) → <strong>메인인도자 우측</strong> 배치<br>
    나머지 4명 → 좌 2명 / 우 2명 4주 로테이션
  </div>
<div class="tabs">
  <div class="tab active" onclick="showCase('A')">Case A — 다원 보조</div>
  <div class="tab" onclick="showCase('B')">Case B — 지현 보조</div>
  <div class="tab" onclick="showCase('C')">Case C — 상미 보조</div>
  <div class="tab" onclick="showCase('D')">Case D — 은화 보조</div>
  <div class="tab" onclick="showCase('E')">Case E — 영민 보조</div>
</div>

<!-- ===== CASE A : 다원 보조 ===== -->
<!-- 로테이션 멤버: 지현·상미·경하·은화 / 좌2 우2 -->
<div class="case-panel active" id="case-A">
  <div class="case-header">
    <h2>Case A — 다원 보조인도자</h2>
    <p>백보컬 6명: 영민(좌끝) · 상원(우끝) · 지현·상미·경하·은화 로테이션(좌2/우2)</p>
    <div class="case-roles">
      <span class="role-badge role-main">🎤 메인: 유직</span>
      <span class="role-badge role-sub">🎤 보조: 다원</span>
      <span class="role-badge role-fixed">📌 영민 좌끝</span>
      <span class="role-badge role-fixed">📌 상원 우끝</span>
      <span class="role-badge role-bv">로테이션: 지현·상미·경하·은화</span>
    </div>
  </div>

  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 1</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">다원</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 합산 동일 — 완벽한 균형입니다.</div>
  </div>

  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 2</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">다원</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>

  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 3</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">다원</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>

  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 4</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">다원</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 균형 — 완벽합니다.</div>
  </div>

  <div class="summary-card">
    <div class="summary-header">📊 Case A 포지션 요약</div>
    <table class="sum-table">
      <thead><tr><th style="text-align:left">멤버</th><th>W1</th><th>W2</th><th>W3</th><th>W4</th><th>좌</th><th>우</th></tr></thead>
      <tbody>
        <tr><td><strong>영민</strong> <span style="color:#888;font-size:0.7rem">남·10dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">4회</td><td>-</td></tr>
        <tr><td><strong>상원</strong> <span style="color:#888;font-size:0.7rem">남·15dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td>-</td><td style="color:#9d174d;font-weight:800">4회</td></tr>
        <tr><td><strong>다원</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td colspan="2" style="text-align:center;color:#92400e;font-weight:700">보조인도자</td></tr>
        <tr><td><strong>지현</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>상미</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>경하</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>은화</strong> <span style="color:#888;font-size:0.7rem">여·10dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
      </tbody>
    </table>
  </div>
  <div class="tip-box">🎚️ 경하가 추가되어 로테이션 4명이 좌2/우2로 고르게 배분됩니다. 보조인도자 다원 마이크는 별도 채널 또는 메인과 동일 버스 적용 권장.</div>
</div>

<!-- ===== CASE B : 지현 보조 ===== -->
<!-- 로테이션: 다원·상미·경하·은화 -->
<div class="case-panel" id="case-B">
  <div class="case-header">
    <h2>Case B — 지현 보조인도자</h2>
    <p>백보컬 6명: 영민(좌끝) · 상원(우끝) · 다원·상미·경하·은화 로테이션(좌2/우2)</p>
    <div class="case-roles">
      <span class="role-badge role-main">🎤 메인: 유직</span>
      <span class="role-badge role-sub">🎤 보조: 지현</span>
      <span class="role-badge role-fixed">📌 영민 좌끝</span>
      <span class="role-badge role-fixed">📌 상원 우끝</span>
      <span class="role-badge role-bv">로테이션: 다원·상미·경하·은화</span>
    </div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 1</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">지현</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 균형 완벽합니다.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 2</span><span class="week-db">좌 35dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">지현</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 3</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">지현</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 균형 완벽합니다.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 4</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">지현</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="summary-card">
    <div class="summary-header">📊 Case B 포지션 요약</div>
    <table class="sum-table">
      <thead><tr><th style="text-align:left">멤버</th><th>W1</th><th>W2</th><th>W3</th><th>W4</th><th>좌</th><th>우</th></tr></thead>
      <tbody>
        <tr><td><strong>영민</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">4회</td><td>-</td></tr>
        <tr><td><strong>상원</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td>-</td><td style="color:#9d174d;font-weight:800">4회</td></tr>
        <tr><td><strong>지현</strong></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td colspan="2" style="text-align:center;color:#92400e;font-weight:700">보조인도자</td></tr>
        <tr><td><strong>다원</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>상미</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>경하</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>은화</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
      </tbody>
    </table>
  </div>
</div>

<!-- ===== CASE C : 상미 보조 ===== -->
<!-- 로테이션: 다원·지현·경하·은화 -->
<div class="case-panel" id="case-C">
  <div class="case-header">
    <h2>Case C — 상미 보조인도자</h2>
    <p>백보컬 6명: 영민(좌끝) · 상원(우끝) · 다원·지현·경하·은화 로테이션(좌2/우2)</p>
    <div class="case-roles">
      <span class="role-badge role-main">🎤 메인: 유직</span>
      <span class="role-badge role-sub">🎤 보조: 상미</span>
      <span class="role-badge role-fixed">📌 영민 좌끝</span>
      <span class="role-badge role-fixed">📌 상원 우끝</span>
      <span class="role-badge role-bv">로테이션: 다원·지현·경하·은화</span>
    </div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 1</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">상미</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 균형 완벽합니다.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 2</span><span class="week-db">좌 35dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">상미</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 3</span><span class="week-db">좌 40dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">상미</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 균형 완벽합니다.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 4</span><span class="week-db">좌 35dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 35dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">상미</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="summary-card">
    <div class="summary-header">📊 Case C 포지션 요약</div>
    <table class="sum-table">
      <thead><tr><th style="text-align:left">멤버</th><th>W1</th><th>W2</th><th>W3</th><th>W4</th><th>좌</th><th>우</th></tr></thead>
      <tbody>
        <tr><td><strong>영민</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">4회</td><td>-</td></tr>
        <tr><td><strong>상원</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td>-</td><td style="color:#9d174d;font-weight:800">4회</td></tr>
        <tr><td><strong>상미</strong></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td colspan="2" style="text-align:center;color:#92400e;font-weight:700">보조인도자</td></tr>
        <tr><td><strong>다원</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>지현</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>경하</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>은화</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
      </tbody>
    </table>
  </div>
</div>

<!-- ===== CASE D : 은화 보조 ===== -->
<!-- 로테이션: 다원·지현·상미·경하 -->
<div class="case-panel" id="case-D">
  <div class="case-header">
    <h2>Case D — 은화 보조인도자</h2>
    <p>백보컬 6명: 영민(좌끝) · 상원(우끝) · 다원·지현·상미·경하 로테이션(좌2/우2)</p>
    <div class="case-roles">
      <span class="role-badge role-main">🎤 메인: 유직</span>
      <span class="role-badge role-sub">🎤 보조: 은화</span>
      <span class="role-badge role-fixed">📌 영민 좌끝</span>
      <span class="role-badge role-fixed">📌 상원 우끝</span>
      <span class="role-badge role-bv">로테이션: 다원·지현·상미·경하</span>
    </div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 1</span><span class="week-db">좌 40dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">은화</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 2</span><span class="week-db">좌 40dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">은화</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 3</span><span class="week-db">좌 40dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">은화</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 4</span><span class="week-db">좌 40dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">영민</span><span class="fixed-badge">끝고정</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">은화</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="summary-card">
    <div class="summary-header">📊 Case D 포지션 요약</div>
    <table class="sum-table">
      <thead><tr><th style="text-align:left">멤버</th><th>W1</th><th>W2</th><th>W3</th><th>W4</th><th>좌</th><th>우</th></tr></thead>
      <tbody>
        <tr><td><strong>영민</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">4회</td><td>-</td></tr>
        <tr><td><strong>상원</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td>-</td><td style="color:#9d174d;font-weight:800">4회</td></tr>
        <tr><td><strong>은화</strong></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td colspan="2" style="text-align:center;color:#92400e;font-weight:700">보조인도자</td></tr>
        <tr><td><strong>다원</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>지현</strong></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>상미</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>경하</strong></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
      </tbody>
    </table>
  </div>
  <div class="tip-box">🎚️ Case D는 은화(10dB)가 보조인도자로 나가므로 우측이 항상 15dB 3명으로 구성됩니다. 우측 게인 보정을 매 주차 반드시 적용하세요.</div>
</div>
</div>


<!-- ===== CASE E : 영민 보조 ===== -->
<div class="case-panel" id="case-E">
  <div class="case-header">
    <h2>Case E — 영민 보조인도자</h2>
    <p>백보컬 6명: 경하(좌끝·대체고정) · 상원(우끝) · 다원·지현·상미·은화 로테이션(좌2/우2)</p>
    <div class="case-roles">
      <span class="role-badge role-main">🎤 메인: 유직</span>
      <span class="role-badge role-sub">🎤 보조: 영민</span>
      <span class="role-badge role-fixed">📌 경하 좌끝 (영민 대체)</span>
      <span class="role-badge role-fixed">📌 상원 우끝</span>
      <span class="role-badge role-bv">로테이션: 다원·지현·상미·은화</span>
    </div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 1</span><span class="week-db">좌 45dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">영민</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 5dB 차이 — 미세 보정만으로 충분합니다.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 2</span><span class="week-db">좌 40dB · 우 45dB</span><span class="week-note">⚠️ 우측 게인 보정 필요</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">영민</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 3</span><span class="week-db">좌 45dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">영민</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
    </div>
    <div class="note-warn">💡 우측 마이크 게인을 2~3dB 낮게 설정하세요.</div>
  </div>
  <div class="week-card">
    <div class="week-header"><span class="week-badge">Week 4</span><span class="week-db">좌 45dB · 우 40dB</span><span class="week-note">✅ 균형</span></div>
    <div class="stage">
      <div class="side"><div class="side-label">◀ 좌측</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">경하</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">지현</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">상미</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 45dB</div>
      </div>
      <div class="center-col"><div class="mic-icon">🎤</div><div class="mic-label">메인<br>인도자</div></div>
      <div class="sub-col"><div class="sub-box"><div class="sub-tag">보조인도자</div><div class="sub-name">영민</div></div></div>
      <div class="side"><div class="side-label">우측 ▶</div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">다원</span><span class="db15">15dB</span></div>
        <div class="member"><span class="gbadge female">여</span><span class="mname">은화</span><span class="db10">10dB</span></div>
        <div class="member"><span class="gbadge male">남</span><span class="mname">상원</span><span class="fixed-badge">끝고정</span><span class="db15">15dB</span></div>
        <div class="side-total">합산 40dB</div>
      </div>
    </div>
    <div class="note-good">✅ 좌우 5dB 차이 — 미세 보정만으로 충분합니다.</div>
  </div>

  <div class="summary-card">
    <div class="summary-header">📊 Case E 포지션 요약</div>
    <table class="sum-table">
      <thead><tr><th style="text-align:left">멤버</th><th>W1</th><th>W2</th><th>W3</th><th>W4</th><th>좌</th><th>우</th></tr></thead>
      <tbody>
        <tr><td><strong>영민</strong> <span style="color:#888;font-size:0.7rem">남·10dB</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td><span class="pos-s">보조</span></td><td colspan="2" style="text-align:center;color:#92400e;font-weight:700">보조인도자</td></tr>
        <tr><td><strong>상원</strong> <span style="color:#888;font-size:0.7rem">남·15dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td>-</td><td style="color:#9d174d;font-weight:800">4회</td></tr>
        <tr><td><strong>경하</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">4회</td><td>-</td></tr>
        <tr><td><strong>다원</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>지현</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>상미</strong> <span style="color:#888;font-size:0.7rem">여·15dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
        <tr><td><strong>은화</strong> <span style="color:#888;font-size:0.7rem">여·10dB</span></td><td><span class="pos-r">우</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-l">좌</span></td><td><span class="pos-r">우</span></td><td style="color:#1e40af;font-weight:800">2회</td><td style="color:#9d174d;font-weight:800">2회</td></tr>
      </tbody>
    </table>
  </div>
  <div class="tip-box">🎚️ <strong>사운드 팁</strong><br>
    · 영민(10dB)이 보조로 나가고 경하(15dB)가 좌끝 대체 — 좌우 음량이 더 균등해집니다.<br>
    · W1·W3·W4는 좌우 5dB 차이로 미세 보정만으로 충분합니다.<br>
    · 영민 보조인도자 마이크는 메인 버스와 동일하게 처리 권장.
  </div>
</div>

<!-- FOOTER -->
<div style="margin-top:64px;padding:32px;background:#fff;border-radius:16px;text-align:center;color:var(--text-muted);border:1px solid var(--mid-gray)">
  <div style="font-size:22px;font-weight:800;color:var(--primary);margin-bottom:8px">Sunday Kerygma</div>
  <div style="font-size:14px;margin-bottom:4px">보컬 음향 운영 매뉴얼 <strong>v3</strong> — Midas Pro2C 기준 최적화</div>
  <div style="font-size:12px;color:#94a3b8">Mode 1 Corrective (메인) · Mode 2/3 Adaptive/Creative (백보컬) · HPF 24dB/oct 보정 적용</div>
</div>

</div>
</div>

<script>
  // 햄버거 메뉴
  function toggleMenu() {
    const nav = document.getElementById('mobileNav');
    const overlay = document.getElementById('overlay');
    const btn = document.getElementById('hamburger');
    nav.classList.toggle('open');
    overlay.classList.toggle('show');
    btn.classList.toggle('open');
  }
  function showCase(id) {
    document.querySelectorAll('.case-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.getElementById('case-' + id).classList.add('active');
    event.target.classList.add('active');
  }
  function closeMenu() {
    document.getElementById('mobileNav').classList.remove('open');
    document.getElementById('overlay').classList.remove('show');
    document.getElementById('hamburger').classList.remove('open');
  }

  // 활성 네비 하이라이트 (사이드바 + 모바일 모두)
  const sections = document.querySelectorAll('.section');
  const navLinks = document.querySelectorAll('.nav-item');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        navLinks.forEach(l => l.classList.remove('active'));
        const id = entry.target.id;
        document.querySelectorAll(`.nav-item[href="#${id}"]`).forEach(el => el.classList.add('active'));
      }
    });
  }, { threshold: 0.3 });
  sections.forEach(s => observer.observe(s));
</script>
</body>
</html>
