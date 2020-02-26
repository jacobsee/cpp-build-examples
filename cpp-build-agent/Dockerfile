# remote-build-agent
FROM openshift3/jenkins-slave-base-rhel7

WORKDIR /opt
RUN curl -o /tmp/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.3.0.1492.zip && \
    unzip /tmp/sonar-scanner.zip && rm /tmp/sonar-scanner.zip && \
    mv sonar-scanner* sonar-scanner

# Add an internal repo (if you're using one)
COPY internal.repo /etc/yum.repos.d/

# Install some developer tools for C++
RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
      yum install -y \
      doxygen gcc gcc-c++ make cmake zlib-devel wget libtool \
      boost-devel qpid-cpp-client-devel qpid-proton-cpp-devel graphviz-devel \
      tbb-devel openssl-devel libcurl-devel gnutls-devel sqlite-devel inotify-tools && \
      yum install -y \
      gtest-devel gmock-devel protobuf cmake-gmock-module protobuf-compiler protobuf-devel \
      --disablerepo=* --enablerepo=internal \
      && yum clean all

# Install YAML tools (delete if not necessary)
RUN wget -O /tmp/yaml-parse.zip https://github.com/jbeder/yaml-cpp/archive/release-0.3.0.zip && \
      unzip /tmp/yaml-parse.zip && \
      pushd yaml-cpp-release-0.3.0 && \
        mkdir build && cd build && cmake .. && make && make install && \
      popd && \
      rm -rf yaml-cpp-release-0.3.0 /tmp/yaml-parse.zip

