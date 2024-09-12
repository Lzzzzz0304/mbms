<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ABlue数据库设计.md</title>
  <link rel="stylesheet" href="https://stackedit.cn/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#一、数据库表设计">一、数据库表设计</a>
<ul>
<li></li>
</ul>
</li>
<li><a href="#二、数据设计">二、数据设计</a>
<ul>
<li></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="一、数据库表设计"><span class="prefix"></span><span class="content">一、数据库表设计</span><span class="suffix"></span></h1>
<h3 id="user-表"><span class="prefix"></span><span class="content">User 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>username</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>用户名</td>
</tr>
<tr>
<td>nickname</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>昵称</td>
</tr>
<tr>
<td>password</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>密码</td>
</tr>
<tr>
<td>phone</td>
<td>N</td>
<td>varchar</td>
<td>20</td>
<td>N</td>
<td>手机号</td>
</tr>
<tr>
<td>role</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>用户角色(0-管理员，1-普通用户，3-医生)</td>
</tr>
<tr>
<td>del</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>删除标志(逻辑删除)</td>
</tr>
<tr>
<td>avatar_url</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>头像URL</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>Sql语句：</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token keyword">User</span> <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    username <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    nickname <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    password <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    phone <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    role <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'用户角色 (0-管理员, 1-普通用户, 3-医生)'</span><span class="token punctuation">,</span>
    del <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'删除标志 (逻辑删除)'</span><span class="token punctuation">,</span>
    avatar_url <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="drug_category-表"><span class="prefix"></span><span class="content">Drug_Category 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>分类名称</td>
</tr>
<tr>
<td>parent_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>Y</td>
<td>父级分类ID</td>
</tr>
<tr>
<td>root_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>根分类ID</td>
</tr>
<tr>
<td>description</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>分类描述</td>
</tr>
<tr>
<td>status</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>状态 (1-启用、0-禁用)</td>
</tr>
<tr>
<td>level</td>
<td>N</td>
<td>int</td>
<td>4</td>
<td>N</td>
<td>分类级别（0-顶级分类）</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>update_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Drug_Category <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类名称'</span><span class="token punctuation">,</span>
    parent_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'父级分类ID'</span><span class="token punctuation">,</span>
    root_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'根分类ID'</span><span class="token punctuation">,</span>
    description <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类描述'</span><span class="token punctuation">,</span>
    <span class="token keyword">status</span> <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'状态 (1-启用、0-禁用)'</span><span class="token punctuation">,</span>
    level <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类级别（0-顶级分类）'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span> <span class="token comment">-- updated_time 字段名调整一致</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span> <span class="token comment">-- 括号位置调整正确</span>

</code></pre>
<h3 id="drug表"><span class="prefix"></span><span class="content">Drug表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>药品名称</td>
</tr>
<tr>
<td>category</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>分类ID (外键)</td>
</tr>
<tr>
<td>price</td>
<td>N</td>
<td>decimal</td>
<td>10,2</td>
<td>N</td>
<td>价格</td>
</tr>
<tr>
<td>picture_url</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>图片URL</td>
</tr>
<tr>
<td>stock</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>库存数量</td>
</tr>
<tr>
<td>status</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>状态 (如：在售、停售)</td>
</tr>
<tr>
<td>consumption</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>消耗说明</td>
</tr>
<tr>
<td>indication</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>指示说明</td>
</tr>
<tr>
<td>metering</td>
<td>N</td>
<td>varchar</td>
<td>50</td>
<td>Y</td>
<td>计量单位</td>
</tr>
<tr>
<td>component</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>成分</td>
</tr>
<tr>
<td>taboo</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>禁忌</td>
</tr>
<tr>
<td>reaction</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>反应</td>
</tr>
<tr>
<td>effect</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>效果</td>
</tr>
<tr>
<td>matter</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>物质</td>
</tr>
<tr>
<td>toxicity</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>毒性</td>
</tr>
<tr>
<td>brand</td>
<td>N</td>
<td>text</td>
<td>255</td>
<td>Y</td>
<td>品牌</td>
</tr>
<tr>
<td>type</td>
<td>N</td>
<td>text</td>
<td>50</td>
<td>Y</td>
<td>类型</td>
</tr>
<tr>
<td>dose</td>
<td>N</td>
<td>text</td>
<td>50</td>
<td>Y</td>
<td>剂量</td>
</tr>
<tr>
<td>character</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>性状</td>
</tr>
<tr>
<td>storage</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>储存条件</td>
</tr>
<tr>
<td>period</td>
<td>N</td>
<td>text</td>
<td>50</td>
<td>Y</td>
<td>有效期</td>
</tr>
<tr>
<td>approval</td>
<td>N</td>
<td>text</td>
<td>255</td>
<td>Y</td>
<td>批准文号</td>
</tr>
<tr>
<td>manufactor</td>
<td>N</td>
<td>text</td>
<td>255</td>
<td>Y</td>
<td>生产厂家</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Drug <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'药品名称'</span><span class="token punctuation">,</span>
    category <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类ID (外键)'</span><span class="token punctuation">,</span>
    price <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'价格'</span><span class="token punctuation">,</span>
    picture_url <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">COMMENT</span> <span class="token string">'图片URL'</span><span class="token punctuation">,</span>
    stock <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'库存数量'</span><span class="token punctuation">,</span>
    <span class="token keyword">status</span> <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'状态 (如：在售、停售)'</span><span class="token punctuation">,</span>
    consumption <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'消耗说明'</span><span class="token punctuation">,</span>
    indication <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'指示说明'</span><span class="token punctuation">,</span>
    metering <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">50</span><span class="token punctuation">)</span> <span class="token keyword">COMMENT</span> <span class="token string">'计量单位'</span><span class="token punctuation">,</span>
    component <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'成分'</span><span class="token punctuation">,</span>
    taboo <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'禁忌'</span><span class="token punctuation">,</span>
    reaction <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'反应'</span><span class="token punctuation">,</span>
    effect <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'效果'</span><span class="token punctuation">,</span>
    matter <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'物质'</span><span class="token punctuation">,</span>
    toxicity <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'毒性'</span><span class="token punctuation">,</span>
    brand <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'品牌'</span><span class="token punctuation">,</span>
    <span class="token keyword">type</span> <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">50</span><span class="token punctuation">)</span> <span class="token keyword">COMMENT</span> <span class="token string">'类型'</span><span class="token punctuation">,</span>
    dose <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">50</span><span class="token punctuation">)</span> <span class="token keyword">COMMENT</span> <span class="token string">'剂量'</span><span class="token punctuation">,</span>
    <span class="token punctuation">`</span>character<span class="token punctuation">`</span> <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'性状'</span><span class="token punctuation">,</span>  <span class="token comment">-- 使用反引号</span>
    storage <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'储存条件'</span><span class="token punctuation">,</span>
    period <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">50</span><span class="token punctuation">)</span> <span class="token keyword">COMMENT</span> <span class="token string">'有效期'</span><span class="token punctuation">,</span>
    approval <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'批准文号'</span><span class="token punctuation">,</span>
    manufactor <span class="token keyword">TEXT</span> <span class="token keyword">COMMENT</span> <span class="token string">'生产厂家'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="doctor-表"><span class="prefix"></span><span class="content">Doctor 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>医生姓名</td>
</tr>
<tr>
<td>department_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>科室ID (外键)</td>
</tr>
<tr>
<td>department_name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>科室名称</td>
</tr>
<tr>
<td>specialization</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>专长</td>
</tr>
<tr>
<td>experience_years</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>Y</td>
<td>从业年限</td>
</tr>
<tr>
<td>price</td>
<td>N</td>
<td>decimal</td>
<td>10,2</td>
<td>Y</td>
<td>价格</td>
</tr>
<tr>
<td>avatar_url</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>头像URL</td>
</tr>
<tr>
<td>post</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>职称</td>
</tr>
<tr>
<td>address</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>地址</td>
</tr>
<tr>
<td>description</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>描述</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token punctuation">`</span>Doctor<span class="token punctuation">`</span> <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'医生姓名'</span><span class="token punctuation">,</span>
    department_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'科室ID (外键)'</span><span class="token punctuation">,</span>
    department_name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'科室名称'</span><span class="token punctuation">,</span>
    specialization <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'专长'</span><span class="token punctuation">,</span>
    experience_years <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'从业年限'</span><span class="token punctuation">,</span>
    price <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'价格'</span><span class="token punctuation">,</span>
    avatar_url <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'头像URL'</span><span class="token punctuation">,</span>
    post <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'职称'</span><span class="token punctuation">,</span>
    address <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'地址'</span><span class="token punctuation">,</span>
    description <span class="token keyword">TEXT</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'描述'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="department_category-表"><span class="prefix"></span><span class="content">Department_Category 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>分类名称</td>
</tr>
<tr>
<td>parent_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>Y</td>
<td>父级分类ID</td>
</tr>
<tr>
<td>root_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>根分类ID</td>
</tr>
<tr>
<td>description</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>分类描述</td>
</tr>
<tr>
<td>status</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>状态 (如：启用、禁用)</td>
</tr>
<tr>
<td>level</td>
<td>N</td>
<td>int</td>
<td>4</td>
<td>N</td>
<td>分类级别</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>update_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Department_Category <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token keyword">COMMENT</span> <span class="token string">'id 自动增长列'</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类名称'</span><span class="token punctuation">,</span>
    parent_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'父级分类ID'</span><span class="token punctuation">,</span>
    root_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'根分类ID'</span><span class="token punctuation">,</span>
    description <span class="token keyword">TEXT</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类描述'</span><span class="token punctuation">,</span>
    <span class="token keyword">status</span> <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'状态 (如：启用、禁用)'</span><span class="token punctuation">,</span>
    level <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类级别'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    update_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="department-表"><span class="prefix"></span><span class="content">Department 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>科室名称</td>
</tr>
<tr>
<td>category</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>分类ID (外键)</td>
</tr>
<tr>
<td>is_hot</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>是否热门</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token punctuation">`</span>Department<span class="token punctuation">`</span> <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'科室名称'</span><span class="token punctuation">,</span>
    category <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'分类ID (外键)'</span><span class="token punctuation">,</span>
    is_hot <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'是否热门'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="symptom-表"><span class="prefix"></span><span class="content">Symptom 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>症状名称</td>
</tr>
<tr>
<td>description</td>
<td>N</td>
<td>text</td>
<td>-</td>
<td>Y</td>
<td>症状描述</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Symptom <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'症状名称'</span><span class="token punctuation">,</span>
    description <span class="token keyword">TEXT</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'症状描述'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span><span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="symptomdescription-表"><span class="prefix"></span><span class="content">SymptomDescription 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>symptom_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>症状ID (外键)</td>
</tr>
<tr>
<td>picture_url</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>图片URL</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> SymptomDescription <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    symptom_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'症状ID (外键)'</span><span class="token punctuation">,</span>
    picture_url <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'图片URL'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span><span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="address-表"><span class="prefix"></span><span class="content">Address 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>user_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>用户ID (外键)</td>
</tr>
<tr>
<td>name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>收件人姓名</td>
</tr>
<tr>
<td>phone</td>
<td>N</td>
<td>varchar</td>
<td>20</td>
<td>N</td>
<td>收件人手机号</td>
</tr>
<tr>
<td>province</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>省份</td>
</tr>
<tr>
<td>city</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>市</td>
</tr>
<tr>
<td>district</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>区/县</td>
</tr>
<tr>
<td>addr</td>
<td>N</td>
<td>varchar</td>
<td>500</td>
<td>N</td>
<td>详细地址</td>
</tr>
<tr>
<td>default</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>是否默认地址</td>
</tr>
<tr>
<td>del</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>删除标志 (逻辑删除)</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Address <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    user_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'用户ID (外键)'</span><span class="token punctuation">,</span>
    name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'收件人姓名'</span><span class="token punctuation">,</span>
    phone <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'收件人手机号'</span><span class="token punctuation">,</span>
    province <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'省份'</span><span class="token punctuation">,</span>
    city <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'市'</span><span class="token punctuation">,</span>
    district <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'区/县'</span><span class="token punctuation">,</span>
    addr <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">500</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'详细地址'</span><span class="token punctuation">,</span>
    <span class="token punctuation">`</span><span class="token keyword">default</span><span class="token punctuation">`</span> <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'是否默认地址'</span><span class="token punctuation">,</span>
    del <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'删除标志 (逻辑删除)'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span> <span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="trolley-表"><span class="prefix"></span><span class="content">Trolley 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>user_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>用户ID (外键)</td>
</tr>
<tr>
<td>drug_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>药品ID (外键)</td>
</tr>
<tr>
<td>quantity</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>数量</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> Trolley <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    user_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'用户ID (外键)'</span><span class="token punctuation">,</span>
    drug_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'药品ID (外键)'</span><span class="token punctuation">,</span>
    quantity <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'数量'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span><span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>
</code></pre>
<h3 id="order-表"><span class="prefix"></span><span class="content">Order 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>order_no</td>
<td>N</td>
<td>varchar</td>
<td>50</td>
<td>N</td>
<td>订单编号</td>
</tr>
<tr>
<td>user_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>用户ID (外键)</td>
</tr>
<tr>
<td>address_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>地址ID (外键)</td>
</tr>
<tr>
<td>amount</td>
<td>N</td>
<td>decimal</td>
<td>10,2</td>
<td>N</td>
<td>订单金额</td>
</tr>
<tr>
<td>status</td>
<td>N</td>
<td>tinyint</td>
<td>1</td>
<td>N</td>
<td>订单状态 (0-未付款, 1-已支付, 2-待发货, 3-已发货, 4-已完成, 5-已关闭)</td>
</tr>
<tr>
<td>payment_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>支付时间</td>
</tr>
<tr>
<td>delivery_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>发货时间</td>
</tr>
<tr>
<td>finish_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>完成时间</td>
</tr>
<tr>
<td>close_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>关闭时间</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token punctuation">`</span><span class="token keyword">Order</span><span class="token punctuation">`</span> <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    order_no <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">50</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'订单编号'</span><span class="token punctuation">,</span>
    user_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'用户ID (外键)'</span><span class="token punctuation">,</span>
    address_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'地址ID (外键)'</span><span class="token punctuation">,</span>
    amount <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'订单金额'</span><span class="token punctuation">,</span>
    <span class="token keyword">status</span> <span class="token keyword">TINYINT</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'订单状态 (0-未付款, 1-已支付, 2-待发货, 3-已发货, 4-已完成, 5-已关闭)'</span><span class="token punctuation">,</span>
    payment_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'支付时间'</span><span class="token punctuation">,</span>
    delivery_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'发货时间'</span><span class="token punctuation">,</span>
    finish_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'完成时间'</span><span class="token punctuation">,</span>
    close_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'关闭时间'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span><span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h3 id="order_item-表"><span class="prefix"></span><span class="content">Order_Item 表</span><span class="suffix"></span></h3>

<table>
<thead>
<tr>
<th>字段名</th>
<th>是否主键</th>
<th>字段类型</th>
<th>占用字节数</th>
<th>是否允许为空</th>
<th>字段说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>id</td>
<td>Y</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>id 自动增长列</td>
</tr>
<tr>
<td>user_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>用户ID (外键)</td>
</tr>
<tr>
<td>order_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>订单ID (外键)</td>
</tr>
<tr>
<td>drug_id</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>药品ID (外键)</td>
</tr>
<tr>
<td>drug_name</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>N</td>
<td>药品名称</td>
</tr>
<tr>
<td>drug_pic</td>
<td>N</td>
<td>varchar</td>
<td>255</td>
<td>Y</td>
<td>药品图片URL</td>
</tr>
<tr>
<td>price</td>
<td>N</td>
<td>decimal</td>
<td>10,2</td>
<td>N</td>
<td>单价</td>
</tr>
<tr>
<td>quantity</td>
<td>N</td>
<td>int</td>
<td>11</td>
<td>N</td>
<td>数量</td>
</tr>
<tr>
<td>total_price</td>
<td>N</td>
<td>decimal</td>
<td>10,2</td>
<td>N</td>
<td>总价</td>
</tr>
<tr>
<td>created_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>N</td>
<td>记录创建时间</td>
</tr>
<tr>
<td>updated_time</td>
<td>N</td>
<td>datetime</td>
<td>8</td>
<td>Y</td>
<td>记录更新时间</td>
</tr>
</tbody>
</table><p>sql</p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token punctuation">`</span>Order_Item<span class="token punctuation">`</span> <span class="token punctuation">(</span>
    id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token keyword">AUTO_INCREMENT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span><span class="token punctuation">,</span>
    user_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'用户ID (外键)'</span><span class="token punctuation">,</span>
    order_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'订单ID (外键)'</span><span class="token punctuation">,</span>
    drug_id <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'药品ID (外键)'</span><span class="token punctuation">,</span>
    drug_name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'药品名称'</span><span class="token punctuation">,</span>
    drug_pic <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">255</span><span class="token punctuation">)</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'药品图片URL'</span><span class="token punctuation">,</span>
    price <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'单价'</span><span class="token punctuation">,</span>
    quantity <span class="token keyword">INT</span><span class="token punctuation">(</span><span class="token number">11</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'数量'</span><span class="token punctuation">,</span>
    total_price <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'总价'</span><span class="token punctuation">,</span>
    created_time <span class="token keyword">DATETIME</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录创建时间'</span><span class="token punctuation">,</span>
    updated_time <span class="token keyword">DATETIME</span> <span class="token keyword">DEFAULT</span> <span class="token boolean">NULL</span> <span class="token keyword">COMMENT</span> <span class="token string">'记录更新时间'</span>
<span class="token punctuation">)</span><span class="token keyword">ENGINE</span><span class="token operator">=</span><span class="token keyword">InnoDB</span> <span class="token keyword">DEFAULT</span> <span class="token keyword">CHARSET</span><span class="token operator">=</span>utf8mb4<span class="token punctuation">;</span>

</code></pre>
<h1 id="二、数据设计"><span class="prefix"></span><span class="content">二、数据设计</span><span class="suffix"></span></h1>
<h3 id="1.药品分类"><span class="prefix"></span><span class="content">1.药品分类</span><span class="suffix"></span></h3>
<ul>
<li>滋补调养
<ul>
<li>补肾</li>
<li>补血补气</li>
<li>安神助眠</li>
<li>心脏疾病</li>
<li>益肝</li>
</ul>
</li>
<li>男科用药
<ul>
<li>阳痿早泄</li>
<li>前列腺炎</li>
<li>泌尿系统疾病</li>
<li>男性不育症</li>
</ul>
</li>
<li>风湿骨科
<ul>
<li>风湿类风湿</li>
<li>跌打损伤</li>
<li>关节炎</li>
<li>骨质增生</li>
<li>劲椎病</li>
<li>腰椎间盘</li>
</ul>
</li>
<li>肠胃用药
<ul>
<li>胃炎胃疼</li>
<li>腹泻</li>
<li>消化不良</li>
<li>肠胃溃疡</li>
</ul>
</li>
<li>皮肤用药
<ul>
<li>皮炎湿疹</li>
<li>皮肤过敏</li>
<li>皮肤外伤</li>
</ul>
</li>
<li>五官用药
<ul>
<li>眼部炎症</li>
<li>咽喉炎</li>
<li>口腔溃疡</li>
<li>眼部健康</li>
<li>鼻炎</li>
<li>中耳炎</li>
</ul>
</li>
<li>妇科用药
<ul>
<li>避孕</li>
<li>阴道炎</li>
<li>痛经</li>
</ul>
</li>
<li>保健用药
<ul>
<li>维生素</li>
<li>钙铁锌硒</li>
</ul>
</li>
<li>小儿用药
<ul>
<li>儿童补钙</li>
<li>补锌补铁</li>
<li>消化不良</li>
<li>厌食</li>
<li>腹泻便秘</li>
</ul>
</li>
<li>感冒咳嗽
<ul>
<li>感冒发烧</li>
<li>咳嗽</li>
<li>气喘</li>
<li>上火</li>
<li>支气管炎</li>
</ul>
</li>
<li>处方药
<ul>
<li>呼吸系统</li>
<li>心脑血管</li>
<li>肝胆用药</li>
<li>皮肤及性病</li>
<li>消化系统</li>
<li>神经系统</li>
<li>泌尿系统</li>
<li>风湿骨科</li>
<li>免疫调节</li>
</ul>
</li>
</ul>
<p><strong>sql语句</strong></p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token comment">-- 插入顶级分类</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> drug_category <span class="token punctuation">(</span>name<span class="token punctuation">,</span> parent_id<span class="token punctuation">,</span> root_id<span class="token punctuation">,</span> description<span class="token punctuation">,</span> <span class="token keyword">status</span><span class="token punctuation">,</span> level<span class="token punctuation">,</span> created_time<span class="token punctuation">,</span> updated_time<span class="token punctuation">)</span> <span class="token keyword">VALUES</span>
<span class="token punctuation">(</span><span class="token string">'滋补调养'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'滋补调养'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'男科用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'男科用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'风湿骨科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'风湿骨科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'肠胃用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'肠胃用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'皮肤用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'皮肤用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'五官用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'五官用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'妇科用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'妇科用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'保健用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'保健用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'小儿用药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'小儿用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'感冒咳嗽'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'感冒咳嗽'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'处方药'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'处方药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">-- 插入二级分类</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> Drug_Category <span class="token punctuation">(</span>name<span class="token punctuation">,</span> parent_id<span class="token punctuation">,</span> root_id<span class="token punctuation">,</span> description<span class="token punctuation">,</span> <span class="token keyword">status</span><span class="token punctuation">,</span> level<span class="token punctuation">,</span> created_time<span class="token punctuation">,</span> updated_time<span class="token punctuation">)</span> <span class="token keyword">VALUES</span>
<span class="token comment">-- 滋补调养</span>
<span class="token punctuation">(</span><span class="token string">'补肾'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'补肾'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'补血补气'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'补血补气'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'安神助眠'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'安神助眠'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心脏疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'心脏疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'益肝'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'益肝'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 男科用药</span>
<span class="token punctuation">(</span><span class="token string">'阳痿早泄'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'阳痿早泄'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'前列腺炎'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'前列腺炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'泌尿系统疾病'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'泌尿系统疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'男性不育症'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'男性不育症'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 风湿骨科</span>
<span class="token punctuation">(</span><span class="token string">'风湿类风湿'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'风湿类风湿'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'跌打损伤'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'跌打损伤'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'关节炎'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'关节炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'骨质增生'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'骨质增生'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'劲椎病'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'劲椎病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'腰椎间盘'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'腰椎间盘'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 肠胃用药</span>
<span class="token punctuation">(</span><span class="token string">'胃炎胃疼'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'胃炎胃疼'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'腹泻'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'腹泻'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'消化不良'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'消化不良'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'肠胃溃疡'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'肠胃溃疡'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 皮肤用药</span>
<span class="token punctuation">(</span><span class="token string">'皮炎湿疹'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'皮炎湿疹'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'皮肤过敏'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'皮肤过敏'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'皮肤外伤'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'皮肤外伤'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 五官用药</span>
<span class="token punctuation">(</span><span class="token string">'眼部炎症'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'眼部炎症'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'咽喉炎'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'咽喉炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'口腔溃疡'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'口腔溃疡'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'眼部健康'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'眼部健康'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'鼻炎'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'鼻炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中耳炎'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中耳炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 妇科用药</span>
<span class="token punctuation">(</span><span class="token string">'避孕'</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'避孕'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'阴道炎'</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'阴道炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'痛经'</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'痛经'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 保健用药</span>
<span class="token punctuation">(</span><span class="token string">'维生素'</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'维生素'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'钙铁锌硒'</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'钙铁锌硒'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 小儿用药</span>
<span class="token punctuation">(</span><span class="token string">'儿童补钙'</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'儿童补钙'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'补锌补铁'</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'补锌补铁'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'消化不良'</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'消化不良'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'厌食'</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'厌食'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'腹泻便秘'</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token string">'腹泻便秘'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 感冒咳嗽</span>
<span class="token punctuation">(</span><span class="token string">'感冒发烧'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'感冒发烧'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'咳嗽'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'咳嗽'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'气喘'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'气喘'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'上火'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'上火'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'支气管炎'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token string">'支气管炎'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 处方药</span>
<span class="token punctuation">(</span><span class="token string">'呼吸系统'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'呼吸系统'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心脑血管'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'心脑血管'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'肝胆用药'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'肝胆用药'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'皮肤及性病'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'皮肤及性病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'消化系统'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'消化系统'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'神经系统'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'神经系统'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'泌尿系统'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'泌尿系统'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'风湿骨科'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'风湿骨科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'免疫调节'</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'免疫调节'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<h3 id="2.科室分类"><span class="prefix"></span><span class="content">2.科室分类</span><span class="suffix"></span></h3>
<ul>
<li>内科
<ul>
<li>呼吸内科</li>
<li>消化内科</li>
<li>神经内科</li>
<li>心血管内科</li>
<li>肾内科</li>
<li>血液内科</li>
<li>免疫科</li>
<li>内分泌科</li>
</ul>
</li>
<li>外科
<ul>
<li>普通外科</li>
<li>神经外科</li>
<li>心胸外科</li>
<li>泌尿外科</li>
<li>心血管外科</li>
<li></li>
</ul>
</li>
<li>妇产科
<ul>
<li>妇科</li>
<li>产科</li>
<li>妇幼保健科</li>
</ul>
</li>
<li>儿科
<ul>
<li>儿科综合</li>
<li>小儿内科</li>
<li>小儿外科</li>
<li>新生儿科</li>
</ul>
</li>
<li>五官科
<ul>
<li>耳鼻喉科</li>
<li>眼科</li>
<li>口腔科</li>
</ul>
</li>
<li>中医科
<ul>
<li>中医全科</li>
<li>中医内科</li>
<li>中医外科</li>
<li>中医妇科</li>
<li>中医儿科</li>
</ul>
</li>
<li>传染科
<ul>
<li>肝病科</li>
<li>艾滋病科</li>
</ul>
</li>
<li>精神心理科
<ul>
<li>精神科</li>
<li>心理咨询科</li>
</ul>
</li>
</ul>
<p><strong>sql</strong></p>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token comment">-- 插入大类</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> department_category <span class="token punctuation">(</span>name<span class="token punctuation">,</span> parent_id<span class="token punctuation">,</span> root_id<span class="token punctuation">,</span> description<span class="token punctuation">,</span> <span class="token keyword">status</span><span class="token punctuation">,</span> level<span class="token punctuation">,</span> created_time<span class="token punctuation">)</span> <span class="token keyword">VALUES</span>
<span class="token punctuation">(</span><span class="token string">'内科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'外科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'外科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'妇产科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'妇科和产科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'儿科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'儿科综合'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'五官科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'耳鼻喉、眼科、口腔科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中医科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医相关科室'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'传染科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'传染病科室'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'精神心理科'</span><span class="token punctuation">,</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'精神和心理健康'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">-- 插入子类</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> Department_Category <span class="token punctuation">(</span>name<span class="token punctuation">,</span> parent_id<span class="token punctuation">,</span> root_id<span class="token punctuation">,</span> description<span class="token punctuation">,</span> <span class="token keyword">status</span><span class="token punctuation">,</span> level<span class="token punctuation">,</span> created_time<span class="token punctuation">)</span> <span class="token keyword">VALUES</span>
<span class="token comment">-- 内科子类</span>
<span class="token punctuation">(</span><span class="token string">'呼吸内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'呼吸系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'消化内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'消化系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'神经内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'神经系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心血管内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'心血管系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'肾内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'肾脏相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'血液内科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'血液系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'免疫科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'免疫系统相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'内分泌科'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token string">'内分泌相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 外科子类</span>
<span class="token punctuation">(</span><span class="token string">'普通外科'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'常规外科手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'神经外科'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'神经系统外科手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心胸外科'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'胸腔心脏相关手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'泌尿外科'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'泌尿系统相关手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心血管外科'</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token string">'心血管系统外科手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 妇产科子类</span>
<span class="token punctuation">(</span><span class="token string">'妇科'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'女性生殖健康'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'产科'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'孕产健康管理'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'妇幼保健科'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token string">'妇女儿童保健'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 儿科子类</span>
<span class="token punctuation">(</span><span class="token string">'儿科综合'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'儿科相关综合疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'小儿内科'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'小儿内科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'小儿外科'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'小儿外科手术'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'新生儿科'</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token string">'新生儿相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 五官科子类</span>
<span class="token punctuation">(</span><span class="token string">'耳鼻喉科'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'耳鼻喉相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'眼科'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'眼部疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'口腔科'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token string">'口腔相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 中医科子类</span>
<span class="token punctuation">(</span><span class="token string">'中医全科'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医全科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中医内科'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医内科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中医外科'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医外科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中医妇科'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医妇科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'中医儿科'</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'中医儿科疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 传染科子类</span>
<span class="token punctuation">(</span><span class="token string">'肝病科'</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'肝病相关传染疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'艾滋病科'</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token string">'艾滋病相关疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>

<span class="token comment">-- 精神心理科子类</span>
<span class="token punctuation">(</span><span class="token string">'精神科'</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'精神疾病'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">(</span><span class="token string">'心理咨询科'</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token string">'心理健康咨询'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token function">NOW</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>

    </div>
  </div>
</body>

</html>
