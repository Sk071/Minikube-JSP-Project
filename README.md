Create Cluster 

eksctl create cluster --name=my-eks22 \
                      --region=ap-south-1 \
                      --zones=ap-south-1a,ap-south-1b \
                      --version=1.30 \
                      --without-nodegroup


eksctl utils associate-iam-oidc-provider \
    --region ap-south-1 \
    --cluster my-eks22 \
    --approve


eksctl create nodegroup --cluster=my-eks22 \
                       --region=ap-south-1 \
                       --name=node2 \
                       --node-type=t3.medium \
                       --nodes=3 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=Key \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access



create argocd 

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

argocd admin initial-password -n argocd


eksctl delete cluster clustername
                
