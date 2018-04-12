# 基础镜像
FROM tomcat:8.5.30-jre8-alpine

# 作者
MAINTAINER Ryoukai <liaojiawei96@qq.com>

# 定义
ENV TOMCAT_HOME /usr/local/tomcat
ENV TOMCAT_BIN $TOMCAT_HOME/bin
ENV TOMCAT_WEBAPPS $TOMCAT_HOME/webapps
ENV TOMCAT_WEBAPPS_ROOT $TOMCAT_WEBAPPS/ROOT
ENV PATH $TOMCAT_BIN:$PATH

WORKDIR $TOMCAT_HOME

# 清空webapp/ROOT目录
RUN rm -rf $TOMCAT_WEBAPPS_ROOT/*

# 将dubbo-admin的war包放到webapps/ROOT目录下
ADD ./dubbo-admin-2.0.0.war $TOMCAT_WEBAPPS_ROOT/

# 解压war包后将其删除
RUN unzip $TOMCAT_WEBAPPS_ROOT/dubbo-admin-2.0.0.war -d $TOMCAT_WEBAPPS_ROOT
RUN rm -f $TOMCAT_WEBAPPS_ROOT/dubbo-admin-2.0.0.war

# 输出端口号
EXPOSE 8080

# dubbo.properties位置
ENV DUBBO_PROPERTIES ./dubbo.properties

COPY $DUBBO_PROPERTIES $TOMCAT_WEBAPPS_ROOT/WEB-INF/

# 运行
CMD ["catalina.sh", "run"]
