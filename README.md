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

����
https://packages.wazuh.com/3.x/windows/wazuh-agent-3.9.5-1.msi
��װ
.\wazuh-agent-3.9.5-1.msi /q ADDRESS="10.0.0.2" AUTHD_SERVER="10.0.0.2"

uninstall
msiexec.exe /x wazuh-agent-3.9.5-1.msi /qn


Installing Audit

# yum install audit
Debian and Ubuntu based Linux distributions:

# apt-get install auditd

�Լ��Ŀ¼ִ�ж�д���,��д��audit.log��־
auditctl -w /home -p w -k audit-wazuh-w
auditctl -w /home -p a -k audit-wazuh-a
auditctl -w /home -p r -k audit-wazuh-r
auditctl -w /home -p x -k audit-wazuh-x

cis-cat--java���

For CentOS/RHEL/Fedora:
# yum install java-1.8.0-openjdk
For Debian/Ubuntu:
# apt-get update && apt-get install openjdk-8-jre


�����б�
auditctl -l
ɾ��ĳ���� -W
auditctl -W /home -p x -k audit-wazuh-x


����windows����

������ʼ�����������ߣ�Ȼ�󵥻����ذ�ȫ���� - >��ȫ���� - >���ز��� - >��˲��� - >˫����˵�¼�¼�������ʻ���¼�¼� - >ѡ��ɹ���ʧ�ܡ�����ȷ����

mail alert����
https://documentation.wazuh.com/3.0/user-manual/manager/manual-email-report/smtp_authentication.html