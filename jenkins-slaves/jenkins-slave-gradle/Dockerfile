FROM quay.io/openshift/origin-jenkins-agent-base:4.2

ENV GRADLE_VERSION=4.9
ENV JAVA_HOME=/usr/java/default
ENV PATH="$PATH:$JAVA_HOME/bin"
ENV ADCS_PATH=/tmp/adcs
ENV JDK_DL_LINK="http://anfadmin.ucsd.edu/linux/RHEL/7/x86_64/jdk-8u221-linux-x64.rpm"
ENV JDK_RPM_PATH=/tmp/jdk-8-linux-x64.rpm
ENV JDK_DIR=/usr/java/jdk1.8.0_221-amd64/bin/java
ENV JDK_ALT_SELECTION="3"

RUN curl -skL -o /tmp/gradle-bin.zip https://services.gradle.org/distributions/gradle-$GRADLE_VERSION-bin.zip && \
    mkdir -p /opt/gradle && \
    unzip -q /tmp/gradle-bin.zip -d /opt/gradle && \
    ln -sf /opt/gradle/gradle-$GRADLE_VERSION/bin/gradle /usr/local/bin/gradle && \
    rm -f /tmp/gradle-bin.zip && \
    chown -R 1001:0 /opt/gradle && \
    chmod -R g+rw /opt/gradle && \
    curl -skL -o $JDK_RPM_PATH $JDK_DL_LINK && \
    yum -y localinstall $JDK_RPM_PATH && \
    alternatives --install /usr/bin/java java $JDK_DIR 999 && \
    alternatives --config java <<< $JDK_ALT_SELECTION && \
    git config --global user.email "james.jen@navy.com" && \
    git config --global user.name "James Jen"
    
RUN sleep 9999999

USER 1000570000
