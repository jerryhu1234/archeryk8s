
1、setting:
values.yaml下配置
相关configMap的文件，settings.py，soar.yaml，analysis_slow_query.sh等
找出与mysql,redis,mongo的数据库连接

2、install:
helm install ./ --name archeryk8s --set-file ruleJson=rule.json

3、run:
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

4、visit:
kubectl port-forward pods/archery-xxxxxx 9123:9123

