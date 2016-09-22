##��JSP/Servlet ��
	1��JSPҳ���ϵ�SQL��ǩ�Լ�EL��ǩ���������ļ�ͷ����ЩJavaServlet������еģ�����Ҫ��֤�Ƿ�����ҳ��ʱ�ض��������

	2�������Ҫ��ȡ�쳣���ݴ˷��ز�����ҳ�浯����ʾ����ô��Ҫ��һ���ķ������ã����в��ң����е�try catch �� ��Ҫ���
		��Ϊһ���ҵ�ϰ�߾��ǰ��쳣�����ʹ����ˣ���Ҫʵ�����Ҫ��ͱ��뽫�쳣������ף�������
	3�������������⣺
		����
			ʹ��get��������Ҫת����gbk :new String(s.getBytes("ISO-88511-1","gbk");
			post������Ҫת����UTF-8
		��Ӧ ��ʹ��UTF-8
##����ܡ�
MVC���ģʽ��
	M
		* hibernarte ����Ӧ������SQL�����Hibernate������ɣ�
		mybatis��SQL�û�������Ҫȥд�ģ�
		JPA ��Hibernate����ͬ���ںˣ���Hibernate��������
	C
		struts1.x
		struts2.x
		* springmvc  

		*spring  ģ�������
	V:
	
##��Hibernate��
###�������

####Hibernate����JAR��
		requiredĿ¼������JAR��Ҫ����
		jpa��JAR������ע���ã�
		��־����
			slf4j-api-* .jar	�ð���һ����־�ӿڣ���Ҫһ��JAR����ʵ�֣�
			slf4j-log4j12.jar	�ð���ת����JAR��
			log4j-1.2.11.jar	ʵ�ֵ�JAR��
		���ݿ�������  mysql-connector-java-5.1.7-bin.jar
	��srcͬ��Ŀ¼���½�һ��libĿ¼����JAR�����ƽ�ȥ��Ȼ���һ���jar�ļ�  Add to build path ���뵽������·����

###��дPOJO�־ò��Ӧ�Ķ���
	ʹ���Լ��Ĺ����ഴ������Ӧ�İ��¡�����IDE�Զ�������

###��дhibernate.cfg.xml�ļ� һ����srcĿ¼��
	���ݿ��������� ������url���û���������
	���ݿⷽ�� 
	��������
	POJO�������ļ���ӳ��
	etc/hibernate.properties����Կ����������ã����ݿ����ӳأ�SQL�Ż���

	�ڣ�project/core/src/main/resources/org/hibernate/���и���dtd�ļ���
		����Ϊeclipse��xml�����Զ���ʾ����
####��־�ļ�������
	��etc�¸���log4j.properties��src�£��Ϳ�����

####�������ࡿ��SessionFactory
	���������������Ĵ�����Դ��������̫��ʵ��
	ͨ�����ù������ǵ���ģʽ��һ��������ʵ����ʾһ�����ݿ�
	����Hibernateһ���ǲ��ܿ����ݿ������������������EJB��JPA����ʵ��
	����һ���������棬Session��һ������

	�������ѡ�
	#hibernate.hbm2ddl.auto create-drop ��һ�����ݿ��д�����Ȼ��ʹ����ر�ʵ��ʱ��ɾ�����н����ı�
	#hibernate.hbm2ddl.auto create ������ݿ�ı������ݣ����´�����
	#hibernate.hbm2ddl.auto update ���������ļ����ܹ������ݿ���в��������£�������
	#hibernate.hbm2ddl.auto validate

###��session��:
	��������������һ������
	�Ƿ��̰߳�ȫ�Ķ���
##��JDBC �� Hibernate �Ƚϡ�
JDBCʹ�����ྫ������죬����ʹ��ʱ���������Լ��෽��ıȽ��鷳
Hibernate���������Ǻܱ�ݵģ������漰��������Ӳ���ʱ�Ƚ��鷳
##���������̡����������Ҫ���ӱ��Ļ��������˳��
  1  �������ݿ�ͱ�������cfg.xml�ļ����ú����ݿ�Ļ�������
  2  ʹ�ù��߽���POJO�־���
  3  ����Hibernate������JAR�������ʹ��Myeclipse�����ã��Լ���������һ�Ѵ���
  4  ʹ��MyEclipse�Զ�����hbm.xml�ļ������и����ļ������ú�hbm�ļ�����ڱ����ϵ��ӳ�䣬������Myeclipse����ʱ�ֶ�ѡ��
  5  ���ú�DAO�����������͹رգ��Լ���������������ã�����û��������������ôPOJO����Ҫ�̳��Զ����ɵĳ����ࣨ����������
  6  ����DAO�����Լ���Utils�࣬ͨ��Hibernate���������ݿ�

##�����ö��һ��ӳ���ϵ��
1.��һ��һ�����޸�xml�ļ�������һ��set ���ԣ���ʾ �෽ ��һ������
< set name="���������������ϣ�" inverse="true">
	< key>< column name="���ݿ�����"/>< /key>
	< one-to-many class="�෽��·��"/>
< /set>
2.��һ��һ�����޸�POJO�־����ļ�������һ��hashset�������洢�෽������setget���������־��������ļ������ӵ��Ǹ����� ע���޸Ĺ�����
3.�ڶ��һ�����޸�xml�ļ����û����Ǹ����������many-to-one��ǩ������д���������

	<many-to-one name="����������������" class="һ������·��" column="���ݿ�������"></many-to-one>

4.�ڶ��һ�����޸�POJO�־����ļ�������һ��һ���Ķ�������setget���������־��������ļ������ӵ��Ǹ�����  ע���޸Ĺ�����
##��ʹ�ö��һ�ļ��ɡ�
###1.���Ӽ�¼��
	1.1.����Ҫ����һ���෽ʱ��һ���ɿγ̣��࿴�ɳɼ�����Ȼ�����ȵ�����ؿγ̣������ӳɼ���¼��
	1.2.�Ǿ���ʵ����һ���γ̶������ú���Ϣ
	1.3.ʵ��������ɼ�ʵ������ �γ̶���.get**Set().add(�ɼ�����); ���ɼ��������ӵ������У�
	1.4.session.save(�γ̶���)��
ע�⣺��Ȼʵ���������Ĳ������Ǿ�˵������ʵ�����ɼ���ʱ�򣬲���Ҫָ���γ̵�ֵ���Ǿ���Ҫ����һ��������
###2.ɾ����¼
	2.1.���ɾ��һ�����ǾͻὫһɾ�������û�����ü������ͻὫ�෽������ÿգ�����ɾ���෽��
	2.2.���ͨ��һ���޸Ķ෽��һ��
			��һ����set�е�Ҫ�޸ĵ�һ����������֮ǰ��Ҫ���� = session.load(����.class,������)���෽�����ݼ��ؽ�����ע��෽�����п��б���ָ��һ��Ĭ��ֵ���Ǻ͹������й�ô����
			�ٲ��ҳ������޸���update������Ҳ�����
			���Ӷ��һ����ʱ�򣬾�����һ����set������һ����¼���෽�Ĳ�������������һ������
##���쳣��
###could not find a getter for ...
	ԭ��1 �������ûдget����
		2 *.hmb.xml�ļ��е���������pojo�־�������������һ�£�һ�������ڱ����������»��ߣ�
		3 ������д�������������ܣ������Զ����ɵģ�
		4 setget�����в���������������д��ĸ
###�����ܽ᣺
	��ʹ����û�������ı���ʹ��Myeclipse�Զ����������ļ���ʹ���Լ���Table2Class������POJO�־��࣬
	��Ҫ�̳ж�Ӧ���Զ������ĳ����࣬��Ϊû�������ı�Ĭ���ǽ������п���һ�����������һ���������һ��id���ԣ�
	����Ҳ˵������һ����ǣ����ֱ����ֶβ����н���id����

	�ǲ��ǿ��Բ����ֶ�ȥʹ���Ǹ��࣬���������Զ����ɵ�һ�ж��У�

	�Զ����ɻ����ɣ�
		��ӦPOJO�ĳ����࣬hbm�����ļ����Լ�Ĭ�ϵļ����࣬HibernateSessionFactory��IBaseHibernateDao��
		��Ӧ��Dao�����ӵ�ʱ��Ĭ����û��ʹ������������Ҫ�ֶ��޸ģ�,���ӣ�ɾ�����������������ģ�����Ҫ��ʼ����������Ȼ�����������ݿ��Ҫ��
****************************************************************************************************************************************************************
##��Mybatis��
###xml�ļ����ã�
	����mybatis-config.xml�ļ�
	����generatorConfig.xml�ļ�

###����JAR����
	���İ�

###����SqlSessionFactory��


##��Spring��


##��SpringMVC��


##��Hibernate��

##��Hibernate��
