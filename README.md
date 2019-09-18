install agent centos
# rpm --import http://packages.wazuh.com/key/GPG-KEY-WAZUH
# cat > /etc/yum.repos.d/wazuh.repo <<\EOF
[wazuh_repo]
gpgcheck=1
gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
enabled=1
name=Wazuh repository
baseurl=https://packages.wazuh.com/3.x/yum/
protect=1
EOF

# yum install wazuh-agent

WAZUH_MANAGER_IP="10.0.0.2" yum install wazuh-agent

uninstall 
yum remove wazuh-agent



windows

下载
https://packages.wazuh.com/3.x/windows/wazuh-agent-3.9.5-1.msi
安装
.\wazuh-agent-3.9.5-1.msi /q ADDRESS="10.0.0.2" AUTHD_SERVER="10.0.0.2"

uninstall
msiexec.exe /x wazuh-agent-3.9.5-1.msi /qn


Installing Audit

# yum install audit
Debian and Ubuntu based Linux distributions:

# apt-get install auditd

对监控目录执行读写监控,会写入audit.log日志
auditctl -w /home -p w -k audit-wazuh-w
auditctl -w /home -p a -k audit-wazuh-a
auditctl -w /home -p r -k audit-wazuh-r
auditctl -w /home -p x -k audit-wazuh-x

cis-cat--java插件

For CentOS/RHEL/Fedora:
# yum install java-1.8.0-openjdk
For Debian/Ubuntu:
# apt-get update && apt-get install openjdk-8-jre


规则列表
auditctl -l
删除某规则 -W
auditctl -W /home -p x -k audit-wazuh-x


配置windows策略

单击开始，单击管理工具，然后单击本地安全策略 - >安全设置 - >本地策略 - >审核策略 - >双击审核登录事件和审核帐户登录事件 - >选择成功和失败。单击确定。

mail alert设置
https://documentation.wazuh.com/3.0/user-manual/manager/manual-email-report/smtp_authentication.html