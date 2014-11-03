
# nodejs模块组件，
# node环境下执行npm install pagination-api 即可安装，方便快捷，支持自定义，
# https://www.npmjs.org/package/pagination-api

# pagination

举例：
在路由中定义：

	var pagination = require('pagination');

	++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

	+++++++[var total_rows;] //total_rows是所有博客的总数量

	total_rows = PostSorts_count_all_result[0].count_all_result;

	+++++++[var per_pages;] //per_pages是url接受到的当前所在页
		var per_pages = 1;
		if(req.query.per_page){
			per_pages = req.query.per_page;
		};
		if(req.body.per_page){
			per_pages = req.body.per_page;
		};

	+++++++[var per_page;] //per_page设置每页显示几篇文章

	per_page = 4;

	+++++++[var base_url;] //base_url定义url地址

	base_url = 'blogs?';
		
	+++++++[var changePer_page;] //changePer_page用于读取数据库进行分页的参数
			
	changePer_page = ( per_pages - 1 ) * per_page;

	+++++++[var Create_links;] //Create_links创建分页

	Create_links = pagination.create_links(total_rows,per_page,per_pages,base_url);

	+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

	最后发送到views-----------[res.render('/',Create_links:Create_links});]


在views中:
	
	[<%- Create_links %>]

# 示例在/test
















