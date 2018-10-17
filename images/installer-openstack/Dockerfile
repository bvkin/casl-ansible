FROM openshift/origin-ansible
MAINTAINER Andrew Block “andrew.block@redhat.com”

USER root

# Update System and install clients
RUN yum -y install epel-release
RUN yum -y install --setopt=tsflags=nodocs https://repos.fedorapeople.org/repos/openstack/openstack-queens/rdo-release-queens-1.noarch.rpm
RUN yum -y install \
  python2-pip python-ceilometerclient \
  python-cinderclient python-glanceclient \
  python-heatclient python-neutronclient \
  python-novaclient python-saharaclient \
  python-swiftclient python-troveclient \
  python-openstackclient python-dns \
  python2-pyOpenSSL python2-shade; \
  yum clean all; \
  rm -rf /var/cache/yum

COPY images/installer-openstack/root /

RUN /usr/local/bin/user_setup_casl

USER ${USER_UID}

ENTRYPOINT [ "/usr/local/bin/entrypoint_casl" ]
CMD [ "/usr/local/bin/run" ]
