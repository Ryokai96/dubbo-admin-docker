# ��������
FROM tomcat:8.5.30-jre8-alpine

# ����
MAINTAINER Ryoukai <liaojiawei96@qq.com>

# ����
ENV TOMCAT_HOME /usr/local/tomcat
ENV TOMCAT_BIN $TOMCAT_HOME/bin
ENV TOMCAT_WEBAPPS $TOMCAT_HOME/webapps
ENV TOMCAT_WEBAPPS_ROOT $TOMCAT_WEBAPPS/ROOT
ENV PATH $TOMCAT_BIN:$PATH

WORKDIR $TOMCAT_HOME

# ���webapp/ROOTĿ¼
RUN rm -rf $TOMCAT_WEBAPPS_ROOT/*

# ��dubbo-admin��war���ŵ�webapps/ROOTĿ¼��
ADD ./dubbo-admin-2.0.0.war $TOMCAT_WEBAPPS_ROOT/

# ��ѹwar������ɾ��
RUN unzip $TOMCAT_WEBAPPS_ROOT/dubbo-admin-2.0.0.war -d $TOMCAT_WEBAPPS_ROOT
RUN rm -f $TOMCAT_WEBAPPS_ROOT/dubbo-admin-2.0.0.war

# ����˿ں�
EXPOSE 8080

# dubbo.propertiesλ��
ENV DUBBO_PROPERTIES ./dubbo.properties

COPY $DUBBO_PROPERTIES $TOMCAT_WEBAPPS_ROOT/WEB-INF/

# ����
CMD ["catalina.sh", "run"]