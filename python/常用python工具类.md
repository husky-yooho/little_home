#### python常用工具类

##### 1、读取配置文件----ConfigParser 
1. 基本方法
    conf_pars = ConfigParser.ConfigParser()
    conf_pars.read（file_name）:
    conf_pars.sections():           得到所有的section
    conf_pars.options(section):     得到section下的options
    conf_pars.items(section):       得到dict形式的键值对
    conf_pars.get(section,option):  得到section下option对应的value
    conf_pars.getint(section,option)



###### 2.读写文件
1. 基本方法
    open(file, "w")      文件名称，a追加，w写，r读
    close()              关流





