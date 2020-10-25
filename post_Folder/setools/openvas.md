# openvas

---
docker pull mikesplain/openvas

docker run -d -p 443:443 -e PUBLIC_HOSTNAME=192.168.2.128 --name openvas mikesplain/openvas

openvasmd --user=admin --new-password=新密码 *//直接修改admin用户的密码*

openvasmd --create-user=用户名 *//创建用户*

openvasmd --delete-user=用户名 *//删除用户*

admin,admin
