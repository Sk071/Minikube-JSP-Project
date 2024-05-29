Create Cluster 

eksctl create cluster --name=my-eks22 \
                      --region=us-east-1 \
                      --version=1.30 \
                      --without-nodegroup


eksctl utils associate-iam-oidc-provider \
    --region us-east-1 \
    --cluster my-eks22 \
    --approve


eksctl create nodegroup --cluster=my-eks22 \
                       --region=us-east-1 \
                       --name=node2 \
                       --node-type=t2.medium \
                       --nodes=2 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=15 \
                       --ssh-access \
                       --ssh-public-key=itadmin-key \
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
                
