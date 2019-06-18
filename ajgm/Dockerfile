FROM openjdk:8-jdk-alpine

ENV LANG zh_CN.UTF-8

ENV GROOVY_VERSION 2.5.7
ENV GROOVY_HOME /opt/groovy

ENV MAVEN_VERSION 3.6.1
ENV MAVEN_HOME /opt/maven

ENV PATH $GROOVY_HOME/bin:$MAVEN_HOME/bin:$PATH

RUN echo "Downloading Groovy" 
RUN wget --no-verbose --output-document=groovy.zip "http://mirror.bit.edu.cn/apache/groovy/${GROOVY_VERSION}/distribution/apache-groovy-binary-${GROOVY_VERSION}.zip" 

RUN echo "Unzip Groovy" 
RUN unzip groovy.zip 
RUN rm groovy.zip 
RUN mv "groovy-${GROOVY_VERSION}" "${GROOVY_HOME}/" 
    
RUN echo "Downloading Maven"
RUN wget --no-verbose --output-document=maven.zip "http://mirror.bit.edu.cn/apache/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.zip"
RUN echo "Unzip Maven" 
RUN unzip maven.zip 
RUN rm maven.zip 
RUN mv "apache-maven-${MAVEN_VERSION}" "${MAVEN_HOME}/" 

RUN echo "Assign Aliyun Maven Conf"
RUN mv $MAVEN_HOME/conf/settings.xml $MAVEN_HOME/conf/settings.xml.bak
COPY settings.xml $MAVEN_HOME/conf/settings.xml

