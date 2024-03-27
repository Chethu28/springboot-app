# springboot-app deployment using Helm charts


# Pre-Requisites


# Installing Trivy 

```
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" |sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update -y
sudo apt-get install trivy -y
```

# Install jenkins in Ubuntu 

```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

```

```
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

```
sudo apt-get update
sudo apt-get install fontconfig openjdk-17-jre
sudo apt-get install jenkins

```

# Installing aws cli 
```

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
ls -l /usr/local/bin/aws
aws version
 
```

# Installing Kubectl

```

sudo curl --silent --location -o /usr/local/bin/kubectl   https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl 

kubectl version --short --client

```
# Installing eksctl
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

eksctl version

```

# Installing docker 

```
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker jenkins
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker

```
# Installing Helm 

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

sudo chmod 700 get_helm.sh

sudo ./get_helm.sh

helm version --client

```

# Creating a EKS cluster

```
eksctl create cluster --name demo --region us-east-1 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2
```

# Deleting cluster

```
eksctl delete cluster --name demo --region us-east-1
```
