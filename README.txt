install:
helm template ./ --name archeryk8s --set-file ruleJson=rule.json > archery.yaml
settings:
kubectl exec -it archeryk8s-xxxx bash
/////////////////////////////////////
cd /opt/archery
source /opt/venv4archery/bin/activate
python3 manage.py makemigrations sql  
python3 manage.py migrate 

# 数据初始化
python3 manage.py loaddata initial_data.json

# 创建管理用户
python3 manage.py createsuperuser
