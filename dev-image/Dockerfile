FROM amazonlinux

RUN yum -y update
RUN yum -y install unzip tar git
RUN yum -y install nano which
RUN curl -sL https://rpm.nodesource.com/setup_14.x | bash - && \
    yum -y install nodejs
RUN amazon-linux-extras install -y python3.8 && \
    ln -s /usr/bin/pip3.8 /usr/bin/pip
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf aws && \
    rm awscliv2.zip
RUN npm install -g typescript
RUN npm install -g aws-cdk
RUN npm install -g @aws-amplify/cli

COPY .bashrc /root/.bashrc

RUN mkdir /root/.aws
COPY .aws/ /root/.aws/

WORKDIR /workspaces/projects
CMD ["/bin/bash"]
