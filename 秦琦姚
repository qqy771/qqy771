<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>运动康复专业发展查询系统</title>
<link rel="stylesheet" href="https://cdn.bootcdn.net/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<script src="https://cdn.bootcdn.net/ajax/libs/Chart.js/4.4.8/chart.umd.min.js"></script>
<style>
*{margin:0;padding:0;box-sizing:border-box;user-select:none;}
body{font-family:"Microsoft YaHei",Arial,sans-serif;}
/* 页面切换基础 */
.page{
    width:100%;min-height:100vh;position:absolute;top:0;left:0;display:none;opacity:0;
    transition:opacity 0.55s ease-in-out;padding:2rem;
    /* 全局背景图 - 铺满+固定+半透明遮罩保证内容可读性 */
    background:url('https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/90552264cb81413eaa88f3963f53c1bd.jpg~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603182016FBFDD6637C36F20D90E0&rrcfp=8a172a1a&x-expires=1781086816&x-signature=jxXt%2B5H5F1W12Q%2BKkdMljL%2B14JY%3D') center/cover fixed;
    /* 深色半透明遮罩，保证文字清晰+风格严肃 */
    background-color:rgba(0,0,0,0.15);
    background-blend-mode:overlay;
}
.page.active{display:block;opacity:1;}

/* ==========第一页样式（封面）========== */
#page1{display:flex;justify-content:center;align-items:center;}
.main-card{
    width:420px;background:rgba(255,255,255,0.9);
    border-radius:12px;padding:45px 30px;text-align:center;
    box-shadow:0 8px 30px rgba(0,0,0,0.2);cursor:pointer;
    transition:all 0.3s ease;
}
.main-card:hover{transform:scale(1.02);box-shadow:0 12px 40px rgba(0,0,0,0.25);}
.main-card i{font-size:3.5rem;color:#2c5898;margin-bottom:20px;}
.main-title{font-size:2rem;color:#1a365d;font-weight:600;margin-bottom:15px;}
.main-desc{font-size:1rem;color:#4a5568;line-height:1.5;}

/* ==========第二页（主页）========== */
#page2{
    /* 新增：让第二页内容整体垂直+水平居中 */
    display: flex;
    justify-content: center;
    align-items: center;
}
.content-container{
    width:85%;max-width:1200px;margin:0 auto;background:rgba(255,255,255,0.92);
    border-radius:12px;padding:40px;box-shadow:0 8px 30px rgba(0,0,0,0.15);
    /* 移除原有的margin-top:3rem，避免居中偏移 */
}
.page-title{font-size:1.8rem;color:#1a365d;margin-bottom:30px;padding-bottom:15px;
    border-bottom:2px solid #e2e8f0;
    /* 新增：标题也居中 */
    text-align: center;
}
.nav-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:25px;margin-top:20px;}
.nav-item{
    background:rgba(247,250,252,1);padding:30px;text-align:center;
    border-radius:8px;cursor:pointer;transition:all 0.2s ease;
    border:1px solid #e2e8f0;
}
.nav-item:hover{
    background:#2c5898;color:white;transform:translateY(-5px);
    box-shadow:0 8px 16px rgba(44,88,152,0.2);
}
.nav-item i{font-size:2.5rem;margin-bottom:15px;color:#2c5898;}
.nav-item:hover i{color:white;}
.nav-item-text{font-size:1.2rem;font-weight:500;color:#2d3748;}
.nav-item:hover .nav-item-text{color:white;}

/* ==========三四五页通用样式========== */
.back-btn{
    position:fixed;left:30px;bottom:30px;width:50px;height:50px;border-radius:50%;
    background:rgba(255,255,255,0.9);display:flex;align-items:center;justify-content:center;
    font-size:1.5rem;color:#2c5898;cursor:pointer;box-shadow:0 4px 12px rgba(0,0,0,0.15);
    transition:all 0.2s ease;z-index:99;
}
.back-btn:hover{background:#2c5898;color:white;}

/* ==========第三页（就业岗位）========== */
#page3{}
.search-panel{
    background:#f7fafc;padding:20px;border-radius:8px;margin-bottom:25px;
    display:flex;align-items:center;gap:15px;
}
.search-panel input{
    flex:1;padding:12px 15px;border:1px solid #e2e8f0;border-radius:6px;
    outline:none;font-size:1rem;
}
.search-panel input:focus{border-color:#2c5898;box-shadow:0 0 0 3px rgba(44,88,152,0.1);}
.search-panel button{
    padding:12px 25px;background:#2c5898;color:white;border:none;border-radius:6px;
    cursor:pointer;font-size:1rem;transition:all 0.2s ease;
}
.search-panel button:hover{background:#1a365d;}
.data-table{width:100%;border-collapse:collapse;margin:20px 0;background:white;
    border-radius:8px;overflow:hidden;box-shadow:0 4px 12px rgba(0,0,0,0.05);
}
.data-table th{
    background:#2c5898;color:white;padding:15px;text-align:left;font-weight:500;
}
.data-table td{
    padding:15px;border-bottom:1px solid #e2e8f0;color:#2d3748;
}
.data-table tr:hover{background:#f7fafc;}
.chart-container{
    background:white;padding:20px;border-radius:8px;margin-top:25px;
    box-shadow:0 4px 12px rgba(0,0,0,0.05);
}
/* 新增：就业可视化图片容器样式 */
.visualization-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(400px,1fr));
    gap:20px;margin-top:25px;
}
.visual-item{
    background:white;padding:15px;border-radius:8px;box-shadow:0 4px 12px rgba(0,0,0,0.05);
    text-align:center;
}
.visual-item img{
    width:100%;height:auto;border-radius:4px;max-height:500px;object-fit:contain;
}
.visual-title{
    font-size:1rem;color:#2c5898;margin-bottom:10px;padding-bottom:8px;
    border-bottom:1px solid #e2e8f0;
}

/* ==========第四页（考研院校）========== */
#page4{}

/* ==========第五页（分工）========== */
#page5{}
.team-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
    gap:20px;margin-top:20px;
}
.team-card{
    background:#f7fafc;padding:25px;border-radius:8px;border:1px solid #e2e8f0;
    transition:all 0.2s ease;
}
.team-card:hover{transform:translateY(-5px);box-shadow:0 8px 16px rgba(0,0,0,0.08);}
.team-card h3{
    color:#2c5898;margin-bottom:10px;padding-bottom:10px;
    border-bottom:1px solid #e2e8f0;
}
.team-card p{color:#4a5568;margin-bottom:8px;font-weight:500;}
.team-card small{color:#718096;line-height:1.6;}
</style>
</head>
<body>

<!-- 第一页：封面 -->
<div id="page1" class="page active">
    <div class="main-card" id="goPage2">
        <i class="fas fa-clipboard-list"></i>
        <div class="main-title">运动康复专业发展查询系统</div>
        <div class="main-desc">专业的就业、升学信息查询与数据分析平台</div>
    </div>
</div>

<!-- 第二页：主页 -->
<div id="page2" class="page">
    <div class="content-container">
        <div class="page-title">功能导航</div>
        <div class="nav-grid">
            <div class="nav-item" data-target="page3">
                <i class="fas fa-briefcase"></i>
                <div class="nav-item-text">就业岗位查询</div>
            </div>
            <div class="nav-item" data-target="page4">
                <i class="fas fa-graduation-cap"></i>
                <div class="nav-item-text">考研院校筛选</div>
            </div>
            <div class="nav-item" data-target="page5">
                <i class="fas fa-users"></i>
                <div class="nav-item-text">项目分工说明</div>
            </div>
        </div>
    </div>
</div>

<!-- 第三页：就业岗位 -->
<div id="page3" class="page">
    <div class="content-container">
        <div class="page-title">运动康复岗位信息查询</div>
        <div class="search-panel">
            <input id="jobSearchInp" placeholder="输入岗位名称/城市/薪资范围查询">
            <button id="searchJobBtn">查询</button>
        </div>
        <table class="data-table">
            <thead>
                <tr>
                    <th>岗位名称</th>
                    <th>工作城市</th>
                    <th>月薪范围</th>
                    <th>就职单位</th>
                </tr>
            </thead>
            <tbody id="jobTbody"></tbody>
        </table>
        <div class="chart-container">
            <canvas id="jobCanvas" height="300"></canvas>
        </div>
        
        <!-- 新增：就业相关可视化图表 -->
        <h3 class="visual-title" style="margin-top:30px;">就业深度分析可视化</h3>
        <div class="visualization-grid">
            <div class="visual-item">
                <div class="visual-title">工作地点分析</div>
                <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/310924276f244a159b5d6b5a0a69a080.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=RK0y2bXQqoPyCQV4CR95ygqFzN4%3D" alt="工作地点分析">
            </div>
            <div class="visual-item">
                <div class="visual-title">学历要求分析</div>
                <img src="https://p26-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/427029becffc454a81d3a8ce4425666c.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=vJ9cdK40anqeGzOIefUKMvjgUxI%3D" alt="学历要求分析">
            </div>
            <div class="visual-item">
                <div class="visual-title">经验要求分析</div>
                <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/3c098eed91814b1999f08fea19ea766e.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=F2o%2FGo1vaOlkwvzcqPsEiOwOc%2FA%3D" alt="经验要求分析">
            </div>
            <div class="visual-item">
                <div class="visual-title">薪资分析</div>
                <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/c47350d07b844d3a9e89896f0f56f04e.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=lNLzx8Qu4ByCE70LEgXUGCvP1%2Fk%3D" alt="薪资分析">
            </div>
        </div>
    </div>
    <div class="back-btn" data-back="page2"><i class="fas fa-arrow-left"></i></div>
</div>

<!-- 第四页：考研院校 -->
<div id="page4" class="page">
    <div class="content-container">
        <div class="page-title">运动康复考研院校筛选</div>
        <div class="search-panel">
            <input id="uniSearchInp" placeholder="输入院校名称/城市/专业方向筛选">
            <button id="searchUniBtn">筛选</button>
        </div>
        <table class="data-table">
            <thead>
                <tr>
                    <th>院校名称</th>
                    <th>报考专业</th>
                    <th>所在城市</th>
                    <th>培养特色</th>
                </tr>
            </thead>
            <tbody id="uniTbody"></tbody>
        </table>
        <div class="chart-container">
            <canvas id="uniCanvas" height="300"></canvas>
        </div>
        
        <!-- 新增：考研相关可视化图表 -->
        <h3 class="visual-title" style="margin-top:30px;">考研院校深度分析可视化</h3>
        <div class="visualization-grid">
            <div class="visual-item">
                <div class="visual-title">院校招生人数</div>
                <img src="https://p11-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/53199e4f3cb4469aa42c64010feeaa9b.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=AVzHDknZ1i0Mq3JqXJYdd0xgdvc%3D" alt="院校招生人数">
            </div>
            <div class="visual-item">
                <div class="visual-title">院校地点分析</div>
                <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/5e01cb08f8e5418cb434bc18431aa62b.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=Mq463%2B5rkIVm%2BqPAaKXqLGfd%2FDI%3D" alt="院校地点分析">
            </div>
            <div class="visual-item">
                <div class="visual-title">院校名称分析</div>
                <img src="https://p3-flow-imagex-download-sign.byteimg.com/tos-cn-i-a9rns2rl98/77b091e8071341348aac44caf158ba68.png~tplv-a9rns2rl98-24:720:720.jpg?lk3s=8e244e95&rcl=20260603183454EC045296EFEB9D20885A&rrcfp=8a172a1a&x-expires=1781087694&x-signature=Wvk0vZjMwnMcI2TmSXceAsBCwbA%3D" alt="院校名称分析">
            </div>
        </div>
    </div>
    <div class="back-btn" data-back="page2"><i class="fas fa-arrow-left"></i></div>
</div>

<!-- 第五页：分工 -->
<div id="page5" class="page">
    <div class="content-container">
        <div class="page-title">项目团队分工说明</div>
        <div class="team-grid">
            <div class="team-card">
                <h3><i class="fas fa-database"></i> 数据采集</h3>
                <p>负责人：夏怡然、李洁怡</p>
                <small>夏怡然自主基于八爪鱼RPA编写自动化数据采集流程，定制爬虫脚本，完成考研院校相关数据的批量爬取与Excel格式导出；李洁怡协助完成就业岗位数据的整理与校验工作。</small>
            </div>
            <div class="team-card">
                <h3><i class="fas fa-chart-pie"></i> 数据可视化</h3>
                <p>负责人：谢琴</p>
                <small>负责就业岗位薪资分布、考研院校地域分布等图表的设计与制作，完成数据可视化呈现逻辑的搭建与优化。</small>
            </div>
            <div class="team-card">
                <h3><i class="fas fa-code"></i> 系统开发</h3>
                <p>负责人：秦琦姚、郝弈雯</p>
                <small>秦琦姚负责整体页面架构设计与交互逻辑开发；郝弈雯负责数据查询功能实现与界面适配优化，共同完成系统的前端开发工作。</small>
            </div>
        </div>
    </div>
    <div class="back-btn" data-back="page2"><i class="fas fa-arrow-left"></i></div>
</div>

<script>
//页面集合
const pageDom={
    page1:document.getElementById('page1'),
    page2:document.getElementById('page2'),
    page3:document.getElementById('page3'),
    page4:document.getElementById('page4'),
    page5:document.getElementById('page5')
}

//页面切换函数
function switchPage(id){
    Object.values(pageDom).forEach(item=>item.classList.remove('active'));
    pageDom[id].classList.add('active');
    if(id==='page3')renderJobData();
    if(id==='page4')renderUniData();
}

//页面跳转绑定
document.getElementById('goPage2').onclick=()=>switchPage('page2');
document.querySelectorAll('.nav-item').forEach(item=>{
    item.onclick=()=>switchPage(item.dataset.target);
})
document.querySelectorAll('.back-btn').forEach(btn=>{
    btn.onclick=()=>switchPage(btn.dataset.back);
})

//就业原始数据
const jobArr=[
    {name:"运动康复师",city:"北京",sal:"10k-15k",unit:"三甲医院"},
    {name:"物理治疗师",city:"上海",sal:"12k-18k",unit:"私立康复诊所"},
    {name:"康复主管",city:"广州",sal:"15k-22k",unit:"专业康复中心"},
    {name:"运动防护专家",city:"深圳",sal:"11k-16k",unit:"职业运动队"},
    {name:"社区康复指导",city:"成都",sal:"7k-10k",unit:"社区卫生中心"},
    {name:"骨科康复师",city:"杭州",sal:"9k-14k",unit:"专科医院"},
    {name:"体能康复教练",city:"武汉",sal:"8k-13k",unit:"健身机构"}
]
let jobChart=null;
function renderJobData(keyword=""){
    let tbody=document.getElementById('jobTbody');
    tbody.innerHTML='';
    //数据筛选
    let filterData=jobArr.filter(item=>{
        let kw=keyword.toLowerCase();
        return item.name.includes(kw)||item.city.includes(kw)||item.sal.includes(kw)||item.unit.includes(kw);
    });
    //渲染表格
    filterData.forEach(d=>{
        tbody.innerHTML+=`<tr>
            <td>${d.name}</td>
            <td>${d.city}</td>
            <td>${d.sal}</td>
            <td>${d.unit}</td>
        </tr>`;
    });
    //绘制柱状图
    let cityAvg={};
    filterData.forEach(i=>{
        let num=i.sal.replace('k','').split('-').map(Number);
        let avg=(num[0]+num[1])/2;
        if(!cityAvg[i.city]) cityAvg[i.city]=[];
        cityAvg[i.city].push(avg);
    });
    let label=Object.keys(cityAvg);
    let data=label.map(k=>(cityAvg[k].reduce((a,b)=>a+b,0)/cityAvg[k].length).toFixed(1));
    
    if(jobChart) jobChart.destroy();
    jobChart=new Chart(document.getElementById('jobCanvas').getContext('2d'),{
        type:'bar',
        data:{
            labels:label,
            datasets:[{
                label:'平均月薪(k)',
                data:data,
                backgroundColor:'rgba(44, 88, 152, 0.7)',
                borderColor:'rgba(44, 88, 152, 1)',
                borderWidth:1,
                borderRadius:4
            }]
        },
        options:{
            responsive:true,
            plugins:{
                title:{display:true,text:'各城市运动康复岗位平均薪资分布',font:{size:16}},
                legend:{display:false}
            },
            scales:{
                y:{
                    beginAtZero:true,
                    title:{display:true,text:'薪资(k)'},
                    grid:{color:'rgba(0,0,0,0.05)'}
                },
                x:{
                    grid:{display:false}
                }
            }
        }
    });
}
//就业查询按钮绑定
document.getElementById('searchJobBtn').onclick=()=>{
    renderJobData(document.getElementById('jobSearchInp').value.trim());
};

//考研院校数据
const uniArr=[
    {sch:"北京体育大学",major:"运动康复学",city:"北京",desc:"运动解剖与临床康复评定"},
    {sch:"上海体育学院",major:"运动康复",city:"上海",desc:"现代康复治疗技术"},
    {sch:"武汉体育学院",major:"运动人体科学",city:"武汉",desc:"运动生物力学方向"},
    {sch:"成都体育学院",major:"运动康复",city:"成都",desc:"中医+运动损伤康复"},
    {sch:"天津体育学院",major:"运动康复学",city:"天津",desc:"运动伤病防护"},
    {sch:"沈阳体育学院",major:"运动康复",city:"沈阳",desc:"冰雪专项康复"},
    {sch:"广州体育学院",major:"运动康复",city:"广州",desc:"运动功能评定研究"}
]
let uniChart=null;
function renderUniData(key=""){
    let tbody=document.getElementById('uniTbody');
    tbody.innerHTML='';
    //数据筛选
    let filterData=uniArr.filter(item=>{
        let kw=key.toLowerCase();
        return item.sch.includes(kw)||item.major.includes(kw)||item.city.includes(kw);
    });
    //渲染表格
    filterData.forEach(d=>{
        tbody.innerHTML+=`<tr>
            <td>${d.sch}</td>
            <td>${d.major}</td>
            <td>${d.city}</td>
            <td>${d.desc}</td>
        </tr>`;
    });
    //绘制饼图
    let countMap={};
    filterData.forEach(i=>{
        countMap[i.city]=(countMap[i.city]||0)+1;
    });
    let lab=Object.keys(countMap);
    let dat=lab.map(k=>countMap[k]);
    //配色方案（严肃商务风）
    const colors=[
        'rgba(44, 88, 152, 0.8)',
        'rgba(72, 118, 255, 0.8)',
        'rgba(30, 136, 229, 0.8)',
        'rgba(2, 136, 209, 0.8)',
        'rgba(0, 150, 136, 0.8)',
        'rgba(56, 142, 60, 0.8)',
        'rgba(139, 195, 74, 0.8)'
    ];
    
    if(uniChart) uniChart.destroy();
    uniChart=new Chart(document.getElementById('uniCanvas').getContext('2d'),{
        type:'pie',
        data:{
            labels:lab,
            datasets:[{
                data:dat,
                backgroundColor:colors.slice(0,lab.length),
                borderWidth:1,
                borderColor:'white'
            }]
        },
        options:{
            responsive:true,
            plugins:{
                title:{display:true,text:'运动康复考研院校地域分布',font:{size:16}},
                legend:{position:'right'}
            }
        }
    });
}
//考研查询按钮绑定
document.getElementById('searchUniBtn').onclick=()=>{
    renderUniData(document.getElementById('uniSearchInp').value.trim());
};

//页面初始渲染
renderJobData();
renderUniData();
</script>
</body>
</html>
