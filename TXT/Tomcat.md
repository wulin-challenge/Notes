#Tomcat 

һ���ʹ��doget���� ��Ŀ��/+XML�ĵ����úõ�·��

ʹ���Զ����JSP��ʱ�������Ŀ��+JSP�ļ�ȫ����ע���Сд�� 
 ��ȱʡ  ���Ƿ��ʵ� Ĭ�����ӵ�  index.jsp�ļ�

##	Web������Web�������ȡ�����������
###��web ������ 

��Ϊ������

      ������һ�ַ�����ù淶��ܣ�J2EE ������������������������������ֲ����ҵ��Ӧ�á��� J2EE �淶�У���Ӧ���� WEB Container �� EJB Container �ȡ�
      WEB �������������е�Ӧ�ó��������JSP��SERVLET���ṩһ��������ʹ JSP��SERVLET ֱ�Ӹ������еĻ����������������ع�ע����ϵͳ����
      ��������Ƕ���˵��web ����Ӧ�����ڼܹ��ϵĸ����web ������Ҫ�� WEB ��������ʵ�֡����磺TOMCAT��WEBLOGIC��WEBSPHERE �ȡ�
      �������ṩ�Ľӿ��ϸ����� J2EE �淶�е� WEB APPLICATION ��׼�����ǰѸ��������� J2EE �е� WEB ������
			WEB ����������Ǹ����� HTTP ������򽻵����� EJB �������ǡ����Ǹ���ĸ����ݿ⡢��������򽻵���
      ��������Ϊ�� �����ڲ���Ӧ�ó������������ͨ��Э�齻�������˸��룬�Ӷ������ڲ�Ӧ�ó�������ĸ�����ʵ�ַ���ĸ���������
			���磺
					SERVLET ���ù��� HTTP ��ϸ�ڣ�����ֱ�����û������� session��request��response ���С�EJB ���ù������ݿ������ٶȡ�����������ƣ�ֱ������������ɡ�

####��Web��������
      Web ��������Web Server�����Դ��� HTTP Э�顣�� Web ���������յ�һ�� HTTP ���󣬻᷵��һ�� HTTP ��Ӧ�������ͻ�һ�� HTML ҳ�档
      Web ������������Ӧ��Ծ�̬ҳ���ͼƬ������ ����ҳ����ת��redirect�������߰Ѷ�̬��Ӧ��dynamic response���Ĳ���ί�У�delegate����һЩ�����ĳ���
      	���� CGI �ű���JSP��JavaServer Pages���ű���servlets��ASP��Active Server Pages���ű����������� JavaScript������һЩ�����ķ������˼�����
			Web �����������ṩһ������ִ�з������˳���ͷ���(������������)��Ӧ�Ļ����������ᳬ��ְ�ܷ�Χ��
			Web ��������Ҫ�Ǵ�����Ҫ����������� HTML �������Թ������

####��Ӧ�ó����������The Application Server����

      ���ݶ��壬��ΪӦ�ó����������Ҫ�����ͨ������Э�飨���� HTTP Э�飩����ҵ�߼���¶����expose���ͻ���Ӧ�ó���
      Ӧ�ó���ʹ�ô���ҵ�߼���������ö����һ����������̣������е�һ��������һ����

####��serverlet��

      Servlet��Server Applet����ȫ�� Java Servlet��δ���������ġ����� Java ��д�ķ������˳�������Ҫ�������ڽ���ʽ��������޸����ݣ����ɶ�̬ Web ���ݡ�
      ����� Servlet ��ָ Java ����ʵ�ֵ�һ���ӿ�
      ����� Servlet ��ָ�κ�ʵ������� Servlet �ӿڵ��࣬һ������£����ǽ� Servlet ����Ϊ���ߡ�
      Servlet ������֧�� Java ��Ӧ�÷������С���ʵ���Ͻ���Servlet ������Ӧ�κ����͵����󣬵������������� Servlet ֻ������չ���� HTTP Э��� Web ��������

####��Tomcat��

      Tomcat ��������һ����ѵĿ���Դ����� Web Ӧ�÷�����������������Ӧ�÷�����������С��ϵͳ�Ͳ��������û����Ǻܶ�ĳ����±��ձ�ʹ�ã��ǿ����͵��� JSP �������ѡ��
      ����һ����ѧ����˵������������Ϊ������һ̨���������ú� Apache ������������������Ӧ�� HTML ҳ��ķ�������
      ʵ���� Tomcat ������Apache ����������չ�������Ƕ������еģ����Ե������� tomcat ʱ����ʵ������Ϊһ���� Apache �����Ľ��̵������еġ�
    Apache Tomcat is an open source software implementation of the Java Servlet and JavaServer Pages technologies.

####��Tomcat��Web��������Ӧ�÷������Ĺ�ϵ��

      Tomcat ��������һ����ѵĿ���Դ����� Web Ӧ�÷���������Ϊ Tomcat �����Ƚ��������ȶ�����ѣ��������� Java �����ߵ�ϲ�����õ��˲������������̵��Ͽɣ���ΪĿǰ�Ƚ����е� Web Ӧ�÷�������

##һ��Tomcat ��Ӧ�÷�����

      ��ĿǰΪֹ��Tomcat һֱ����Ϊ�� Servlet/JSP API ��ִ������Ҳ����ν�� Servlet ������Ȼ����Tomcat����������ˣ������ṩ�� JNDI �� JMX API ��ʵ�ֻ��ơ�������ˣ�Tomcat ��Ȼ����������Ӧ�÷���������Ϊ�����ṩ����� J2EE API ��֧�֡�

      ������˼���ǣ�Ŀǰ�����Ӧ�÷�����ͨ���� Tomcat ��Ϊ���� Servlet �� JSP API ������������ Tomcat����������ֻ��ͨ������һ����л���Ϳ��԰� Tomcat Ƕ�뵽���ǵ�Ӧ���С��ź����ǣ�������ҵӦ�÷�������û�����ش˹���

      ���ڿ�������˵�������Ϊ��Ѱ������ Servlet��JSP��JNDI �� JMX ���������� Java Web Ӧ�õĻ���ѡ��Tomcat ��һ������Ľ������������Ϊ��Ѱ��֧�������� J2EE API����ôѰ��һ��Ӧ�÷��������߰� Tomcat��ΪӦ�÷������ĸ�����
      ����һ�������Ľ�������������ַ�ʽ���ҵ������� J2EE API ʵ�֣�Ȼ������Ǹ�Tomcat �������ʹ�á���Ȼ���ϻ������ص����⣬�������ַ�ʽ����Ϊ��Ч�ġ�

##����Tomcat �� Web ������

      Tomcat ���ṩһ��֧�� Servlet �� JSP ���е�������Servlet �� JSP �ܸ���ʵʱ��Ҫ��������̬��ҳ���ݡ������� Web ��������˵�� Apache ����֧�־�̬��ҳ������֧�ֶ�̬��ҳ�ͻ��Ե�����Ϊ����Tomcat �����Ϊ��̬��ҳ����ͬʱҲ��Ϊ��̬��ҳ�ṩ֧�֡�
      ������û��ͨ���� Web �������졢����Ҳ���� Web �������ḻ������ Tomcat ��Ϊ֧�־�̬���ݲ������䡣������� Web �����������õײ����Ա�д�� C����������Ӧƽ̨������������ô� Java ��д�� Tomcat ִ���ٶȲ��������������Ტ�ۡ�

      һ����˵�����վ�㶼�ǽ� Tomcat �� Apache �Ľ�ϣ�Apache ��������������Կͻ��˵� HTTP ����Ȼ�� Servlets �� JSP ������ת���� Tomcat ��������Tomcat ��ɴ����󣬽���Ӧ���ظ� Apache����� Apache ����Ӧ���ظ��ͻ��ˡ�
      
##	����
���������utf-8     xml utf-8  ����
������   �����  ����  ʹ��response.setContentType("text/html; charset=utf-8");����Ч����response.setChaoactorEncoding;
xml�ļ����������룬saxreader������document����
�޸�tomcat�Ķ˿ں� conf/server.xml �ҵ�connector 8080

myecpipse �ļ�����utf-8
���ݿ�
������
ҳ����� utf-8
Tomcat ���� URIEncoding="UTF-8"

���������get��ʽ����Ҫ���±������ַ���
���������post��ʽ request.setCharactorEncoding(utf-8);

�Լ������Ĺ��������web.xml�̳���conf/web.xml.ֻ��Ҫ��д�Լ���web.xml��ص����õĲ����Ϳ��Ը����书��


##����Ŀ¼
ָ��webappĿ¼��Ŀɷ��ʵ��ļ�
����1.conf/server.xml�ҵ�host
value�Ա�����,< Context path="/hello" docBase="c:/mydsadf"/>

����2��conf/catalina/localhost/myxml.xml
context���ý���< Context  docBase="c:/mydsadf"/>
���ʷ�ʽhttp://localhsot:8080/myxml/

war������1.myeclipse������war
2.Ŀ¼���ļ�ѹ����zip����չ��

����Ŀ¼����

con/server��xml
< host>
<Context path="/abc" docBase="d:/webA"

Ĭ����ҳ

����web�µ�web.xml������ 
< welcome-file-list>
< welcome-file>index.html< /welcome-file>
< /welcome-file-list>

��������

server.xml
<host name="www.baidu.com" appBase="c:/webA" 
unpackWARs="true" autoDeploy="true">
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log." suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />
< Context path="/" docBase="d:/webA" />
>

File f=new File("/information.xml");���д���Ǵ��ģ���ָ���쳣��

request.getParameter�����ַ�����������������ǿյģ��ͷ��س���Ϊ����ַ�����