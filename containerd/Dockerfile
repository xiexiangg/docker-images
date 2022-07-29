FROM centos:7
RUN yum install -y yum-utils device-mapper-persistent-data lvm2 \
&& yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo \
&& yum install containerd -y \
&& containerd config default | tee /etc/containerd/config.toml
RUN touch /etc/crictl.yaml
RUN echo -e '\
runtime-endpoint: "unix:///run/containerd/containerd.sock" \n\
image-endpoint: "unix:///run/containerd/containerd.sock" \n\
timeout: 10 \n\
debug: false \n\
pull-image-on-create: false \n\
disable-pull-on-run: false \n\
' > /etc/crictl.yaml
CMD ["containerd"]