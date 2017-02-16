This project was based on https://github.com/nicusX/k8s-terraform-ansible-sample, more insights about the way it works can be found there.



 sudo easy_install pip
 sudo pip install ansible


mkdir terraform
cd terraform/
wget https://releases.hashicorp.com/terraform/0.8.6/terraform_0.8.6_linux_amd64.zip
unzip terraform_0.8.6_linux_amd64.zip
cd ~/



export MANAGER_IP=54.202.45.150
cd terraform
terraform plan -var manager_ip='"'${MANAGER_IP}'"'
terraform apply -var manager_ip='"'${MANAGER_IP}'"'


cd ansible
ansible-playbook infra.yaml --private-key=~/.ssh/kubernetes_tf.pem --extra-vars "@terraform_vars"
