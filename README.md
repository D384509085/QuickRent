易租网接口文档v2

依据模块划分，涵盖大部分功能的接口文档

baseurl: 127.0.0.1/8010

基于第一版修改内容：

1. 把api按模块分类
2. 添加了租房管理模块和管理员模块的api
3. 修改了房屋数据库表
4. 修改之前查询房屋参数错误的问题

user 用户相关操作

地址: /v2/user

注册

地址：/v2/user

请求方式：POST

请求参数：

    {
        "username" : "王睿"
        "password" : "123456"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

登录

地址：/v2/user/login (这里是为了防止密码明文在url中，所以用POST请求@王睿提出)

请求方式：POST

请求参数：

    {
        "username" : "wangrui"
        "password" : "123456"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

订单管理模块

地址：/v2/order

出租订单查询

地址:/v2/order/rent

请求方式：GET

请求参数：

    {
       "username" : "王睿"
    }

返回参数：

    {
        {
            "orderid" : "1"
            "rent_user" : "王睿"
            "bor_user" : "孙致波"
            "status" : "1"
            "roomid" : "3"
        },
        {
            "orderid" : "4"
            "rent_user" : "王睿"
            "bor_user" : "易碧喻"
            "status" : "0"
            "roomid" : "6"
        }
    }

借房订单查询：

地址：v2/order/borrow

请求方式：GET

请求参数：

    {
       "username" : "王睿"
    }

返回参数：

    {
        {
            "orderid" : "1"
            "rent_user" : "王睿"
            "bor_user" : "孙致波"
            "status" : "1"
            "roomid" : "3"
        },
        {
            "orderid" : "4"
            "rent_user" : "王睿"
            "bor_user" : "易碧喻"
            "status" : "0"
            "roomid" : "6"
        }
    }



修改订单：

地址：/v2/order/

请求方式：PUT

请求参数：

    {
        "orderid" : "2"
        "rent_user" : "王睿"
        "bor_user" : "孙致波"
        "roomid" : "3"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

删除订单

地址：/v2/order/

请求方式：DELETE

请求参数：

    {
        "orderid" : "3"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

出租(借出)管理模块

查询已借出的房屋

地址：v2/rent/room

请求方式：GET

请求参数：

    {
        "username" : "王睿"
    }

返回参数：

    {
        {
            "roomid" : "2"
            "rent_user" : "王睿"
        	"price" : "3000"
        	"adress" : "洪山路108号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "1"
        },
        {
            "roomid" : "3"
            "rent_user" : "王睿"
        	"price" : "4000"
        	"adress" : "洪山路109号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "1"
        }
    }

添加借出的房屋：

地址：v2/rent/room

请求方式：POST

请求参数：

    {
        "rent_user" : "王睿"
        "price" : "3000"
        "adress" : "洪山路108号"
        "house" : "1室1厅",
        "housesize" : "30平米",
        "housefloor" : "3/6层",
        "status" : "0",
        "checked" : "0"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }



修改借出的房屋：

地址：v2/rent/room

请求方式：PUT

请求参数：

    {
        "roomid" : "3"
        "rent_user" : "王睿"
        "price" : "3000"
        "adress" : "洪山路108号"
        "house" : "1室1厅",
        "housesize" : "30平米",
        "housefloor" : "3/6层",
        "status" : "0",
        "checked" : "1"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

删除借出的房屋

地址：v2/rent/room

请求方式：DELETE

请求参数：

    {
        "roomid" : "3"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

租房(借入)管理模块

查询所有可租房屋：

地址：v2/borrow/anjukeroom

请求方式：GET

请求参数：

    {
        "city" : "gz"
    }

注：放入城市缩写，方便爬虫

返回参数：

    {
        {
        	"name" : "花地湾招村新街小区",
        	"price" : "1500",
        	"url" : "https://gz.zu.anjuke.com/fangyuan/1151058067",
        	"adress" : "荔湾-芳村 招村新街",
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
        	"title" : "花地湾地铁站附近 温馨精装修一房一厅 家电齐全 随时方便看房",
        	"imageurl" : {
                 	"img1" : "https://pic1.ajkimg.com/display/hj/a7d019b1ba3b24ffd9ec79bf3316e058/600x450c.jpg?t=1",
                 	"img2" : "https://pic1.ajkimg.com/display/hj/b9433672ef2d1d9ffb618de7f878ee39/600x450c.jpg?t=1",
                 	"img3" : "https://pic1.ajkimg.com/display/hj/035106432c370f8e84c10536ac2b838d/600x450c.jpg?t=1",
                 	"img4" : "https://pic1.ajkimg.com/display/hj/7ab8d82f8e2af63b544daf802d49aba9/600x450c.jpg?t=1",
            	 	"img5" : "https://pic1.ajkimg.com/display/hj/cf9b44e5fc424d1259c00b67c2c1afd5/600x450c.jpg?t=1",
                 	"img6" : "https://pic1.ajkimg.com/display/hj/2822b17e45c908b3c9bd08f5b90f6485/600x450.jpg?t=1"
          	  }
    	},
        {
        	"name" : "花地湾招村新街小区",
        	"price" : "1500",
        	"url" : "https://gz.zu.anjuke.com/fangyuan/1151058067",
        	"adress" : "荔湾-芳村 招村新街",
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
        	"title" : "花地湾地铁站附近 温馨精装修一房一厅 家电齐全 随时方便看房",
        	"imageurl" : {
                 	"img1" : "https://pic1.ajkimg.com/display/hj/a7d019b1ba3b24ffd9ec79bf3316e058/600x450c.jpg?t=1",
                 	"img2" : "https://pic1.ajkimg.com/display/hj/b9433672ef2d1d9ffb618de7f878ee39/600x450c.jpg?t=1",
                 	"img3" : "https://pic1.ajkimg.com/display/hj/035106432c370f8e84c10536ac2b838d/600x450c.jpg?t=1",
                 	"img4" : "https://pic1.ajkimg.com/display/hj/7ab8d82f8e2af63b544daf802d49aba9/600x450c.jpg?t=1",
            	 	"img5" : "https://pic1.ajkimg.com/display/hj/cf9b44e5fc424d1259c00b67c2c1afd5/600x450c.jpg?t=1",
                 	"img6" : "https://pic1.ajkimg.com/display/hj/2822b17e45c908b3c9bd08f5b90f6485/600x450.jpg?t=1"
          	  }
    	}
    }

注1：这是爬虫爬到的数据，不能按关键字查询，所以在这里把所有的房屋信息都传给前端，进入房屋详情页面的时候带参跳转，数据就不从后台请求了。

注2：在本平台只可用租在本平台发布的房屋

查询本平台房屋：(查询本平台status为0的房屋)

地址：v2/borrow/room

请求方式：GET

请求体：

    {
        
    }

返回体：

    {
        {
            "roomid" : "2"
            "rent_user" : "王睿"
        	"price" : "3000"
        	"adress" : "洪山路108号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "1"
        },
        {
            "roomid" : "3"
            "rent_user" : "王睿"
        	"price" : "4000"
        	"adress" : "洪山路109号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "1"
        }
    }

添加订单：

地址：/v2/order/

请求方式：POST

请求参数：

    {
        "rent_user" : "王睿"
        "bor_user" : "孙致波"
        "roomid" : "3"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }



管理员模块

注：为了方便，管理员模块每一项操作都需要输入密码，密码订为123456

查询所有用户信息：

地址：v2/root/user

请求方式：POST

请求参数：

    {
        "password" : "123456"
    }

返回参数:

    {
        {
        	"userid" : "1",
            "username" : "123",
            "password" : "123"
        },
        {
            "userid" : "2",
            "username" : "123",
            "password" : "123"
        }
    }
    
    或
    {
        "resault" : "failed"
    }
    

获取需要审核的房屋(checked属性为0)

地址：v2/root/room

请求方式：POST

请求参数：

    {
        "password" : "123456"
    }

返回参数：

    {
        {
            "roomid" : "2"
            "rent_user" : "王睿"
        	"price" : "3000"
        	"adress" : "洪山路108号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "0"
        },
        {
            "roomid" : "3"
            "rent_user" : "王睿"
        	"price" : "4000"
        	"adress" : "洪山路109号"
        	"house" : "1室1厅",
        	"housesize" : "30平米",
        	"housefloor" : "3/6层",
            "status" : "0"
            "checked" : "0"
        }
    }

确认审核房屋(逻辑和修改房屋大同小异)

地址：v2/root/check

请求方式：POST

请求参数：

    {
        "roomid" : "3"
    }

返回参数：

    {
        "message" :
        {
            "result" : "success"
        }
    }

数据库表设计v2

版本：v1 

实现系统最基本的数据库支持

user用户

  字段名     	类型     	描述        	主键关系
  id      	int    	自增id      	主键  
  userName	varchar	用户名       	    
  password	varchar	密码        	    
  power   	int    	是否管理员,是1否0	    

order订单

  字段名       	类型  	描述          	主键关系
  id        	int 	自增id        	主键  
  rentUser  	int 	user主键，租用户id	外键  
  borrowUser	int 	user主键，借用户id	外键  
  status    	int 	订单是否完成，是1否0 	    
  room      	int 	room主键，房屋id 	外键  

room房屋

  字段名       	类型     	描述          	主键关系
  id        	int    	自增id        	主键  
  rentUser  	int    	user主键，租用户id	外键  
  price     	int    	价格          	    
  adress    	varchar	地址          	    
  house     	varchar	几室几厅 1室1厅   	    
  housesize 	int    	大小(平米)      	    
  housefloor	varchar	楼层 3/6层     	    
  status    	int    	是否已经被预定，是1否0	    
  checked   	int    	是否被审核，是1否0  	    

collection收藏

  字段名 	类型  	描述  	主键关系
  id  	int 	自增id	主键  
  user	int 	用户id	外键  
  room	int 	房屋id	外键  

card_possess卡券

  字段名     	类型     	描述        	主键关系
  id      	int    	自增id      	主键  
  user    	int    	用户id      	外键  
  cardName	varchar	用户拥有的一个卡券名	    

tag标签

  字段名 	类型     	描述       	主键关系
  id  	int    	自增id     	主键  
  room	int    	房屋id     	外键  
  tag 	varchar	房屋拥有的一个标签	    




