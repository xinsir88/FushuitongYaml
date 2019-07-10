#Dockerfile
  这是build image的程序入口，过程中会增加环境变量、安装tomcat、gcc、make、cronlog等命令。
  我也不想装这些无用的，但是要想日志切割就要使用cronlog，要想使用cronlog就要安装gcc make等。
  修改了tomcat的启动方式，这是因为日志切了个，后台会一天产生一个日志文件。
  所以要注意的是，我们在看pod日志的时候，不要使用kubectl logs 看了，因为这个日志不动。
  我们后期再真正启动tomcat的时候，会挂载一个volume，会把日志存放到宿主机上，直接去宿主机上看就行了。
  
  