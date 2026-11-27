<!doctype html>
<html lang="bn">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#07110b">
<title>FN Telecom </title>
<style>
:root{--bg:#07110b;--panel:#102219;--green:#19c463;--line:#294936;--text:#f5fff8;--muted:#a8b9ad}
*{box-sizing:border-box}body{margin:0;background:linear-gradient(160deg,#07110b,#10251a);color:var(--text);font-family:system-ui,"Noto Sans Bengali",sans-serif}
.wrap{max-width:560px;margin:auto;min-height:100vh;padding:16px}
header{display:flex;align-items:center;justify-content:space-between;gap:10px;margin:8px 0 18px}
.brand{display:flex;align-items:center;gap:10px}.logo{width:46px;height:46px;border-radius:14px;background:var(--green);color:#062111;display:grid;place-items:center;font-weight:900}
h1{font-size:21px;margin:0}header small{color:var(--muted)}
button,input,select{font:inherit}.btn{border:0;border-radius:10px;background:var(--green);color:#062111;font-weight:750;padding:10px 13px;cursor:pointer}
.btn.secondary{background:#1b3827;color:var(--text);border:1px solid var(--line)}
.hero{background:linear-gradient(120deg,#126b3b,#0d2b1a);border:1px solid #237b4a;border-radius:18px;padding:17px;margin-bottom:16px}
.hero strong{font-size:19px}.hero p{margin:5px 0 0;color:#d7f5e2;font-size:13px}
h2{font-size:16px;margin:18px 0 10px}
.operators{display:grid;grid-template-columns:repeat(5,1fr);gap:7px}
.operator{border:1px solid var(--line);background:var(--panel);border-radius:12px;padding:10px 2px;text-align:center;color:var(--text);font-size:12px;cursor:pointer}
.operator b{display:block;font-size:17px;color:var(--green);margin-bottom:3px}.operator.active{border:2px solid var(--green);background:#173b27}
.tabs{display:flex;gap:7px;margin:10px 0}.tab{flex:1;padding:9px 3px;border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:10px}.tab.active{background:var(--green);color:#062111;font-weight:700}
.card{background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:13px;margin:9px 0;display:flex;justify-content:space-between;align-items:center;gap:10px}
.card h3{font-size:14px;margin:0 0 4px}.muted{font-size:12px;color:var(--muted);margin:0}
.price{color:#7af0a8;font-weight:800;font-size:17px;text-align:right}
.panel{background:var(--panel);border:1px solid var(--line);border-radius:16px;padding:14px;margin:12px 0}
label{display:block;font-size:13px;color:#d7e9dc;margin:10px 0 5px}
input,select{width:100%;padding:11px;border-radius:10px;border:1px solid #42614c;background:#08170e;color:var(--text)}
.formgrid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.actions{display:flex;gap:7px;flex-wrap:wrap;margin-top:9px}
.hidden{display:none!important}.notice{font-size:12px;color:#c4d5c9;line-height:1.6;background:#0b1b12;padding:11px;border-radius:10px;margin:12px 0}
footer{text-align:center;color:#7f9888;font-size:11px;padding:22px 0}
</style></head>
<body><div class="wrap">
<header><div class="brand"><div class="logo">FN</div><div><h1>FN Telecom</h1><small>সব অপারেটরের অফার এক জায়গায়</small></div></div><button class="btn secondary" id="adminToggle">অ্যাডমিন</button></header>
<section id="customer">
<div class="hero"><strong>আপনার পছন্দের প্যাকেজ বেছে নিন</strong><p>ইন্টারনেট • মিনিট • কম্বো অফার</p></div>
<h2>অপারেটর নির্বাচন করুন</h2><div class="operators" id="operators"></div>
<h2>প্যাকেজের ধরন</h2><div class="tabs" id="tabs"></div>
<h2 id="offerHeading">অফারসমূহ</h2><div id="offerList"></div>
<div class="notice"></div>
</section>
<section id="admin" class="hidden">
<div class="hero"><strong>অ্যাডমিন প্যানেল</strong><p>অফার যোগ, পরিবর্তন ও মুছে ফেলুন</p></div>
<div class="notice">ডেমো PIN: <b>87563399</b>।  এই ফাইলে যোগ করা অফার এই ফোনের ব্রাউজারেই সংরক্ষিত হবে।</div>
<div id="loginBox" class="panel"><label>অ্যাডমিন PIN</label><input id="pin" inputmode="numeric" type="password" placeholder="ডেমো PIN লিখুন"><div class="actions"><button class="btn" id="loginBtn">লগইন</button><button class="btn secondary" id="backBtn">গ্রাহক পেজ</button></div></div>
<div id="adminArea" class="hidden">
<div class="panel">
<h2 style="margin-top:0">নতুন অফার যোগ করুন</h2>
<label>অপারেটর</label><select id="newOp"><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select>
<label>প্যাকেজের ধরন</label><select id="newType"><option>ইন্টারনেট</option><option>মিনিট</option><option>কম্বো</option></select>
<label>অফারের নাম</label><input id="newName" placeholder="যেমন: ১০ GB ইন্টারনেট">
<div class="formgrid"><div><label>দাম (টাকা)</label><input id="newPrice" type="number" min="0" placeholder="যেমন: ১৯৯"></div><div><label>মেয়াদ/বিবরণ</label><input id="newDetail" placeholder="যেমন: ৩০ দিন"></div></div>
<button class="btn" id="addBtn" style="width:100%;margin-top:13px">অফার যোগ করুন</button>
</div>
<h2>বর্তমান অফার পরিচালনা</h2><div id="manageList"></div>
<div class="actions"><button class="btn secondary" id="logoutBtn">লগআউট</button><button class="btn secondary" id="resetBtn">নমুনা অফার ফিরিয়ে আনুন</button><button class="btn secondary" id="customerBtn">গ্রাহক পেজ</button></div>
</div></section>
<footer>© FN Telecom • version</footer></div>
<script>
const operators=['GP','Banglalink','Robi','Airtel','Teletalk'], types=['ইন্টারনেট','মিনিট','কম্বো'];
const defaults=[];
operators.forEach(op=>{
 defaults.push({op,type:'ইন্টারনেট',name:'৫ GB ইন্টারনেট',price:99,detail:'নমুনা ৭ দিন'});
 defaults.push({op,type:'ইন্টারনেট',name:'১০ GB ইন্টারনেট',price:199,detail:'নমুনা ৩০ দিন'});
 defaults.push({op,type:'মিনিট',name:'১০০ মিনিট',price:79,detail:'নমুনা ৭ দিন'});
 defaults.push({op,type:'কম্বো',name:'৫ GB + ১০০ মিনিট',price:249,detail:'নমুনা ৩০ দিন'});
});
let offers=JSON.parse(localStorage.getItem('fnOffers')||'null')||defaults;
let currentOp='GP',currentType='ইন্টারনেট',logged=false;
const save=()=>localStorage.setItem('fnOffers',JSON.stringify(offers));
function renderSelectors(){
 document.getElementById('operators').innerHTML=operators.map(o=>`<button class="operator ${o===currentOp?'active':''}" data-op="${o}"><b>${o==='Banglalink'?'BL':o[0]}</b>${o}</button>`).join('');
 document.querySelectorAll('[data-op]').forEach(b=>b.onclick=()=>{currentOp=b.dataset.op;render()});
 document.getElementById('tabs').innerHTML=types.map(t=>`<button class="tab ${t===currentType?'active':''}" data-type="${t}">${t}</button>`).join('');
 document.querySelectorAll('[data-type]').forEach(b=>b.onclick=()=>{currentType=b.dataset.type;render()});
}
function renderCustomer(){
 const found=offers.filter(x=>x.op===currentOp&&x.type===currentType);
 document.getElementById('offerHeading').textContent=currentOp+' — '+currentType+' অফার';
 document.getElementById('offerList').innerHTML=found.length?found.map(x=>`<div class="card"><div><h3>${esc(x.name)}</h3><p class="muted">${esc(x.detail||'')}</p></div><div><div class="price">৳ ${Number(x.price).toLocaleString('bn-BD')}</div><button class="btn" onclick="orderDemo('${escJs(x.name)}')">অর্ডার</button></div></div>`).join(''):'<p class="muted">এই বিভাগে এখনো কোনো অফার যোগ করা হয়নি।</p>';
}
function renderManage(){
 document.getElementById('manageList').innerHTML=offers.length?offers.map((x,i)=>`<div class="card"><div><h3>${esc(x.op)} • ${esc(x.name)}</h3><p class="muted">${esc(x.type)} | ৳ ${x.price} | ${esc(x.detail||'')}</p></div><div class="actions"><button class="btn secondary" onclick="editOffer(${i})">এডিট</button><button class="btn secondary" onclick="deleteOffer(${i})">মুছুন</button></div></div>`).join(''):'<p class="muted">কোনো অফার নেই।</p>';
}
function render(){renderSelectors();renderCustomer();if(logged)renderManage()}
function esc(s){return String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function escJs(s){return String(s).replace(/\\/g,'\\\\').replace(/'/g,"\\'")}
function order(name){const phone=prompt('যে নম্বরে অফার নিতে চান, সেই নম্বর লিখুন:');if(phone)alert(''+currentOp+' / '+name+' / '+phone+'. )}
window.orderDemo=order;
window.deleteOffer=i=>{if(confirm('এই অফারটি মুছে ফেলবেন?')){offers.splice(i,1);save();render()}};
window.editOffer=i=>{let x=offers[i];let n=prompt('অফারের নাম',x.name);if(n===null)return;let p=prompt('দাম (টাকা)',x.price);if(p===null)return;if(!n.trim()||p.trim()===''||isNaN(Number(p))||Number(p)<0){alert('সঠিক নাম ও দাম লিখুন।');return}let d=prompt('মেয়াদ/বিবরণ',x.detail||'');if(d===null)return;offers[i]={...x,name:n.trim(),price:Number(p),detail:d.trim()};save();render()};
document.getElementById('adminToggle').onclick=()=>{document.getElementById('customer').classList.add('hidden');document.getElementById('admin').classList.remove('hidden');document.getElementById('adminArea').classList.add('hidden');document.getElementById('loginBox').classList.remove('hidden');document.getElementById('pin').value='';logged=false};
document.getElementById('loginBtn').onclick=()=>{if(document.getElementById('pin').value==='1234'){logged=true;document.getElementById('loginBox').classList.add('hidden');document.getElementById('adminArea').classList.remove('hidden');renderManage()}else alert('PIN সঠিক নয়। ডেমো PIN: 87563399')};
function showCustomer(){document.getElementById('admin').classList.add('hidden');document.getElementById('customer').classList.remove('hidden')}
document.getElementById('backBtn').onclick=showCustomer;document.getElementById('customerBtn').onclick=showCustomer;
document.getElementById('logoutBtn').onclick=()=>{logged=false;document.getElementById('adminArea').classList.add('hidden');document.getElementById('loginBox').classList.remove('hidden')};
document.getElementById('addBtn').onclick=()=>{let name=document.getElementById('newName').value.trim(),price=document.getElementById('newPrice').value,detail=document.getElementById('newDetail').value.trim();if(!name||price===''||!Number.isFinite(Number(price))||Number(price)<0){alert('অফারের নাম ও সঠিক দাম দিন।');return}offers.push({op:document.getElementById('newOp').value,type:document.getElementById('newType').value,name,price:Number(price),detail});save();document.getElementById('newName').value='';document.getElementById('newPrice').value='';document.getElementById('newDetail').value='';render();alert('অফার যোগ হয়েছে।')};
document.getElementById('resetBtn').onclick=()=>{if(confirm('সব পরিবর্তন মুছে নমুনা অফার ফিরিয়ে আনবেন?')){offers=defaults.map(x=>({...x}));save();render()}};
render();
</script><!doctype html>
<html lang="bn">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#07110b"><title>FN Telecom — Payment UI Demo</title>
<style>
:root{--bg:#07110b;--panel:#102219;--green:#19c463;--line:#294936;--text:#f5fff8;--muted:#a8b9ad}
*{box-sizing:border-box}body{margin:0;background:linear-gradient(160deg,#07110b,#10251a);color:var(--text);font-family:system-ui,"Noto Sans Bengali",sans-serif}
.wrap{max-width:570px;margin:auto;min-height:100vh;padding:16px}header{display:flex;justify-content:space-between;align-items:center;margin:8px 0 18px;gap:8px}
.brand{display:flex;align-items:center;gap:10px}.logo{width:45px;height:45px;border-radius:14px;background:var(--green);color:#062111;display:grid;place-items:center;font-weight:900}
h1{font-size:21px;margin:0}small,.muted{color:var(--muted)}.btn{border:0;border-radius:10px;background:var(--green);color:#062111;font-weight:750;padding:10px 13px;cursor:pointer}
.secondary{background:#1b3827;color:var(--text);border:1px solid var(--line)}
.hero{background:linear-gradient(120deg,#126b3b,#0d2b1a);border:1px solid #237b4a;border-radius:18px;padding:16px;margin-bottom:16px}
h2{font-size:16px;margin:18px 0 10px}.operators{display:grid;grid-template-columns:repeat(5,1fr);gap:7px}
.operator,.tab{border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:11px;padding:10px 2px;text-align:center;cursor:pointer;font-size:12px}
.operator b{display:block;color:var(--green);font-size:17px}.active{border:2px solid var(--green)!important;background:#173b27!important}
.tabs{display:flex;gap:7px;margin:10px 0}.tab{flex:1}.card,.panel{background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:13px;margin:9px 0}
.card{display:flex;justify-content:space-between;align-items:center;gap:9px}.card h3{font-size:14px;margin:0 0 4px}.muted{font-size:12px;margin:0}.price{color:#7af0a8;font-weight:800}
label{display:block;font-size:13px;margin:10px 0 5px}input{width:100%;padding:11px;border-radius:10px;border:1px solid #42614c;background:#08170e;color:var(--text);font:inherit}
.actions{display:flex;gap:7px;flex-wrap:wrap;margin-top:10px}.notice{font-size:12px;color:#c4d5c9;line-height:1.6;background:#0b1b12;padding:11px;border-radius:10px;margin:12px 0}
.hidden{display:none!important}.row{display:flex;gap:8px}.row>*{flex:1}
.paygrid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:12px 0}
.paychoice{min-height:92px;border:2px solid var(--line);border-radius:16px;background:#0b1b12;color:white;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:5px;cursor:pointer}
.paychoice.selected{border-color:var(--green);box-shadow:0 0 0 2px #19c46333}
.paymark{font-size:24px;font-weight:900;letter-spacing:-1px}.bkash .paymark{color:#e84b83}.nagad .paymark{color:#f28b28}
.paychoice small{font-size:11px}.modal{position:fixed;inset:0;background:#000a;display:flex;align-items:center;justify-content:center;padding:16px;z-index:5}
.modalbox{width:min(100%,420px);background:#102219;border:1px solid #42614c;border-radius:18px;padding:18px;max-height:90vh;overflow:auto}
footer{text-align:center;color:#7f9888;font-size:11px;padding:22px 0}
</style></head>
<body><div class="wrap">
<header><div class="brand"><div class="logo">FN</div><div><h1>FN Telecom</h1><small>ইন্টারনেট • মিনিট • কম্বো</small></div></div><button class="btn secondary" id="adminBtn">অ্যাডমিন</button></header>
<section id="customer">
<div class="hero"><b>আপনার পছন্দের প্যাকেজ বেছে নিন</b><p class="muted">সব অপারেটরের অফার এক জায়গায়</p></div>
<h2>অপারেটর</h2><div class="operators" id="ops"></div>
<h2>প্যাকেজের ধরন</h2><div class="tabs" id="tabs"></div>
<h2 id="heading">অফারসমূহ</h2><div id="offerList"></div>
<div class="notice"></div>
</section>
<section id="admin" রclass="hidden">
<div class="hero"><b>অ্যাডমিন প্যানেল</b><p class="muted">অফার ও অর্ডার পরিচালনা</p></div>
<div class="notice">পরীক্ষার PIN: <b>1234</b>। এটি নিরাপদ লগইন নয়। তথ্য এই ডিভাইস/ব্রাউজারে থাকে।</div>
<div id="login" class="panel"><label>অ্যাডমিন PIN</label><input id="pin" type="password" inputmode="numeric" placeholder="1234"><div class="actions"><button class="btn" id="loginBtn">লগইন</button><button class="btn secondary" id="backBtn">গ্রাহক পেজ</button></div></div>
<div id="adminArea" class="hidden">
<div class="panel"><h2 style="margin-top:0">নতুন অফার যোগ</h2>
<label>অপারেটর</label><select id="opNew"><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select>
<label>প্যাকেজের ধরন</label><select id="typeNew"><option>ইন্টারনেট</option><option>মিনিট</option><option>কম্বো</option></select>
<label>অফারের নাম</label><input id="nameNew" placeholder="যেমন ১০ GB ইন্টারনেট">
<div class="row"><div><label>দাম (টাকা)</label><input id="priceNew" type="number" min="0"></div><div><label>মেয়াদ/বিবরণ</label><input id="detailNew" placeholder="৩০ দিন"></div></div>
<button class="btn" id="addBtn" style="width:100%;margin-top:12px">অফার যোগ করুন</button></div>
<h2>অফার পরিচালনা</h2><div id="manageOffers"></div>
<h2>গ্রাহকের ডেমো অর্ডার</h2><div id="orders"></div>
<div class="actions"><button class="btn secondary" id="logoutBtn">লগআউট</button><button class="btn secondary" id="resetBtn">নমুনা অফার ফিরিয়ে আনুন</button><button class="btn secondary" id="customerBtn">গ্রাহক পেজ</button></div>
</div></section><footer>© FN Telecom • Demo only</footer></div>
<div id="orderModal" class="modal hidden"><div class="modalbox">
<h2 style="margin-top:0">অর্ডার নিশ্চিত করুন</h2><p id="chosenOffer" class="muted"></p>
<label>যে নম্বরে অফার নিতে চান</label><input id="orderPhone" inputmode="tel" placeholder="01XXXXXXXXX">
<h2>পেমেন্ট পদ্ধতি নির্বাচন করুন</h2>
<div class="paygrid">
<button class="paychoice bkash" data-pay="বিকাশ"><span class="paymark">bKash</span><small>বিকাশ</small></button>
<button class="paychoice nagad" data-pay="নগদ"><span class="paymark">নগদ</span><small>Nagad</small></button>
</div>
<p class="muted" id="payHint">পেমেন্ট পদ্ধতির লোগোতে চাপ দিন।</p>
<div class="actions"><button class="btn" id="confirmOrder" disabled>ডেমো অর্ডার করুন</button><button class="btn secondary" id="cancelOrder">বাতিল</button></div>
<p class="notice">এটি শুধু ডেমো। আসল পেমেন্ট করতে হলে অনুমোদিত bKash/Nagad মার্চেন্ট বা পেমেন্ট গেটওয়ে ইন্টিগ্রেশন প্রয়োজন।</p>
</div></div>
<script>
const ops=['GP','Banglalink','Robi','Airtel','Teletalk'],types=['ইন্টারনেট','মিনিট','কম্বো'];
const seed=[];ops.forEach(op=>{seed.push({op,type:'ইন্টারনেট',name:'৫ GB ইন্টারনেট',price:99,detail:'নমুনা ৭ দিন'},{op,type:'মিনিট',name:'১০০ মিনিট',price:79,detail:'নমুনা ৭ দিন'},{op,type:'কম্বো',name:'৫ GB + ১০০ মিনিট',price:249,detail:'নমুনা ৩০ দিন'})});
let offers=JSON.parse(localStorage.getItem('fn4_offers')||'null')||seed;
let orders=JSON.parse(localStorage.getItem('fn4_orders')||'[]'),opNow='GP',typeNow='ইন্টারনেট',logged=false,pendingOffer=null,selectedPay='';
const save=()=>{localStorage.setItem('fn4_offers',JSON.stringify(offers));localStorage.setItem('fn4_orders',JSON.stringify(orders))};
const esc=s=>String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
function render(){
 document.getElementById('ops').innerHTML=ops.map(o=>`<button class="operator ${o===opNow?'active':''}" data-op="${o}"><b>${o==='Banglalink'?'BL':o[0]}</b>${o}</button>`).join('');
 document.querySelectorAll('[data-op]').forEach(b=>b.onclick=()=>{opNow=b.dataset.op;render()});
 document.getElementById('tabs').innerHTML=types.map(t=>`<button class="tab ${t===typeNow?'active':''}" data-type="${t}">${t}</button>`).join('');
 document.querySelectorAll('[data-type]').forEach(b=>b.onclick=()=>{typeNow=b.dataset.type;render()});
 document.getElementById('heading').textContent=opNow+' — '+typeNow+' অফার';
 const list=offers.map((x,i)=>({...x,i})).filter(x=>x.op===opNow&&x.type===typeNow);
 document.getElementById('offerList').innerHTML=list.length?list.map(x=>`<div class="card"><div><h3>${esc(x.name)}</h3><p class="muted">${esc(x.detail)}</p></div><div style="text-align:right"><div class="price">৳ ${x.price}</div><button class="btn" onclick="startOrder(${x.i})">অর্ডার</button></div></div>`).join(''):'<p class="muted">এই বিভাগে অফার নেই।</p>';
 if(logged){renderManage();renderOrders()}
}
function startOrder(i){pendingOffer=offers[i];if(!pendingOffer)return;selectedPay='';document.getElementById('chosenOffer').textContent=pendingOffer.op+' • '+pendingOffer.name+' • ৳'+pendingOffer.price;document.getElementById('orderPhone').value='';document.querySelectorAll('.paychoice').forEach(b=>b.classList.remove('selected'));document.getElementById('confirmOrder').disabled=true;document.getElementById('payHint').textContent='পেমেন্ট পদ্ধতির লোগোতে চাপ দিন।';document.getElementById('orderModal').classList.remove('hidden')}
window.startOrder=startOrder;
document.querySelectorAll('.paychoice').forEach(b=>b.onclick=()=>{selectedPay=b.dataset.pay;document.querySelectorAll('.paychoice').forEach(x=>x.classList.toggle('selected',x===b));document.getElementById('payHint').textContent=selectedPay+' নির্বাচন করা হয়েছে (ডেমো)';document.getElementById('confirmOrder').disabled=false});
document.getElementById('cancelOrder').onclick=()=>document.getElementById('orderModal').classList.add('hidden');
document.getElementById('confirmOrder').onclick=()=>{let phone=document.getElementById('orderPhone').value.trim();if(!/^01[0-9]{9}$/.test(phone)){alert('সঠিক ১১ সংখ্যার বাংলাদেশি মোবাইল নম্বর লিখুন।');return}orders.unshift({id:Date.now(),op:pendingOffer.op,name:pendingOffer.name,price:pendingOffer.price,phone,pay:selectedPay,status:'অপেক্ষমাণ'});save();document.getElementById('orderModal').classList.add('hidden');alert('ডেমো অর্ডার তৈরি হয়েছে। কোনো টাকা কাটা হয়নি। অ্যাডমিন প্যানেলে অর্ডারটি দেখতে পাবেন।')};
function renderManage(){document.getElementById('manageOffers').innerHTML=offers.map((x,i)=>`<div class="card"><div><h3>${esc(x.op)} • ${esc(x.name)}</h3><p class="muted">${esc(x.type)} | ৳${x.price} | ${esc(x.detail)}</p></div><div class="actions"><button class="btn secondary" onclick="editOffer(${i})">এডিট</button><button class="btn secondary" onclick="delOffer(${i})">মুছুন</button></div></div>`).join('')||'<p class="muted">কোনো অফার নেই।</p>'}
function renderOrders(){document.getElementById('orders').innerHTML=orders.map((o,i)=>`<div class="card" style="display:block"><h3>#${String(o.id).slice(-6)} • ${esc(o.op)} — ${esc(o.name)}</h3><p class="muted">নম্বর: ${esc(o.phone)} | পদ্ধতি: ${esc(o.pay)} | ৳${o.price}</p><p class="muted">অবস্থা: <b>${esc(o.status)}</b></p><div class="actions"><button class="btn secondary" onclick="setStatus(${i},'সম্পন্ন')">সম্পন্ন</button><button class="btn secondary" onclick="setStatus(${i},'বাতিল')">বাতিল</button><button class="btn secondary" onclick="delOrder(${i})">মুছুন</button></div></div>`).join('')||'<p class="muted">এখনো কোনো ডেমো অর্ডার আসেনি।</p>'}
window.setStatus=(i,s)=>{orders[i].status=s;save();renderOrders()};window.delOrder=i=>{if(confirm('অর্ডার মুছবেন?')){orders.splice(i,1);save();renderOrders()}};
window.delOffer=i=>{if(confirm('অফার মুছবেন?')){offers.splice(i,1);save();render()}};
window.editOffer=i=>{let x=offers[i],n=prompt('অফারের নাম',x.name);if(n===null)return;let p=prompt('দাম',x.price);if(p===null||!n.trim()||p.trim()===''||isNaN(+p)||+p<0)return alert('সঠিক নাম ও দাম দিন।');let d=prompt('মেয়াদ/বিবরণ',x.detail);if(d===null)return;offers[i]={...x,name:n.trim(),price:+p,detail:d};save();render()};
document.getElementById('adminBtn').onclick=()=>{document.getElementById('customer').classList.add('hidden');document.getElementById('admin').classList.remove('hidden');document.getElementById('login').classList.remove('hidden');document.getElementById('adminArea').classList.add('hidden');document.getElementById('pin').value='';logged=false};
function customerPage(){document.getElementById('admin').classList.add('hidden');document.getElementById('customer').classList.remove('hidden')}
document.getElementById('backBtn').onclick=customerPage;document.getElementById('customerBtn').onclick=customerPage;
document.getElementById('loginBtn').onclick=()=>{if(document.getElementById('pin').value==='1234'){logged=true;document.getElementById('login').classList.add('hidden');document.getElementById('adminArea').classList.remove('hidden');render()}else alert('PIN ভুল। ডেমো PIN 1234')};
document.getElementById('logoutBtn').onclick=()=>{logged=false;document.getElementById('adminArea').classList.add('hidden');document.getElementById('login').classList.remove('hidden')};
document.getElementById('addBtn').onclick=()=>{let name=document.getElementById('nameNew').value.trim(),price=document.getElementById('priceNew').value;if(!name||price===''||isNaN(+price)||+price<0)return alert('অফারের নাম ও সঠিক দাম দিন।');offers.push({op:document.getElementById('opNew').value,type:document.getElementById('typeNew').value,name,price:+price,detail:document.getElementById('detailNew').value.trim()});save();document.getElementById('nameNew').value='';document.getElementById('priceNew').value='';document.getElementById('detailNew').value='';render();alert('অফার যোগ হয়েছে।')};
document.getElementById('resetBtn').onclick=()=>{if(confirm('নমুনা অফার ফিরিয়ে আনবেন?')){offers=seed.map(x=>({...x}));save();render()}};
render();
</script></body></html>
</body></html># index.html
