FROM centos:centos7.0.1406
MAINTAINER okahashi117
RUN yum -y install make tar git wget gcc-c++ openssl-devel readline-devel gdbm-devel libffi-devel zlib-devel curl-devel procps autoconf sudo
RUN git clone https://github.com/sstephenson/rbenv.git /usr/local/rbenv
RUN mkdir /usr/local/rbenv/shims /usr/local/rbenv/versions /usr/local/rbenv/plugins
RUN groupadd rbenv
RUN chgrp -R rbenv /usr/local/rbenv
RUN chmod -R g+rwxXs /usr/local/rbenv
RUN git clone https://github.com/sstephenson/ruby-build.git /usr/local/rbenv/plugins/ruby-build
RUN chgrp -R rbenv /usr/local/rbenv/plugins/ruby-build
RUN chmod -R g+rwxs /usr/local/rbenv/plugins/ruby-build
RUN /usr/local/rbenv/plugins/ruby-build/install.sh
RUN git clone https://github.com/sstephenson/rbenv-default-gems.git /usr/local/rbenv/plugins/rbenv-default-gems
RUN chgrp -R rbenv /usr/local/rbenv/plugins/rbenv-default-gems
RUN chmod -R g+rwxs /usr/local/rbenv/plugins/rbenv-default-gems
RUN echo 'export RBENV_ROOT="/usr/local/rbenv"' >> /etc/profile.d/rbenv.sh
RUN echo 'export PATH="/usr/local/rbenv/bin:$PATH"' >> /etc/profile.d/rbenv.sh
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
RUN echo '%rbenv ALL=(ALL) ALL' >> /etc/sudoers
RUN su -l root -c '/usr/local/rbenv/bin/rbenv install 2.1.7 -v'
RUN su -l root -c '/usr/local/rbenv/bin/rbenv rehash'
RUN su -l root -c '/usr/local/rbenv/bin/rbenv global 2.1.7'