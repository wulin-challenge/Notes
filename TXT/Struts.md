#Struts2�ʼ�
####ʹ��ognl����ʽ��<s:debug></s:debug>
####ʹ�õ�jar������Ҫ����library��������ʱ��Ҫ����Ҫ����libĿ¼��
������
< result-types>
      ...
      < result-type name="myresult" class="com.foo.MyResult" />
  < /result-types>

####actionû��result��ִ�еķ���û�з���ֵ��������д��out.write(JSON); ����action�������յ�JSON�ַ���
####result��ǩ����Ĭ����ת����Ҫ��ʾ˵�����ض���
##��struts���й��̡�
1.������ĸ����¼�������һ��URL������
2.����Ŀ��Ĭ�Ϲ������������ˣ����ö�Ӧ��action��(��Ҫ���ú�xml�ļ���package��action��ǩ��
3.��action�а�������������ִ����������ķ���
4.��action�����з����������������Ĵ��봦���ĵط�����returnֵ��ȷ���Ȼ���ת�Ľ��ҳ�棨����xml�ļ���result��ǩ��

##���Struts2����������
������ֱ��ʹ��MyEclipse�Ŀ��ٴ��struts2.1+Hibernate3.3.2+JSTL1.2.2(����jdk7.45+tomcat7.08)��
1.�ҵ�Struts2Ӧ������Ҫʹ�õ���JAR�����ر�ע�ⲻ�ܺ�Hibernate��JAR�����ظ��ģ���Ȼ�ͱ�����
	**Struts2.33�汾�Ŀ�������JAR����·���� f:\Tool\AllJar\SSH\struts23
		sm-3.3.jar
		sm-commons-3.3.jar
		sm-tree-3.3.jar
		ommons-fileupload-1.2.2.jar
		ommons-io-2.0.1.jar
		ommons-lang3-3.1.jar
		ommons-logging-1.1.1.jar
		reemarker-2.3.19.jar
		avassist-3.11.0.GA.jar
		gnl-3.0.5.jar
		truts2-core-2.3.3.jar
		work-core-2.3.3.jar

2. ����JSP�ļ�
3. ����Action�ļ���ʵ����Struts��Action�ӿڵ���ͨ��,���߼̳�ActionSupport�ࣩ
4. ��дStruts2�������ļ�Struts.xml
5. ��web.xml�м���Struts2 ��������Ĺ��������ã����Ĺ�������

###����Action��URL��
	package��namespace����Action�����ּ��Ϻ�׺

###URL Ĭ���������� ��
	/a/b/c/d/df.action
	/a/df.action
	*�������ǵȼ۵ģ����泤���Ǹ�ͬ���ֽ�Ϊ�����֣�ǰ�벿�ֵ�·���Ǵ�d��a
	�������������ģ�ֱ���ҵ�������Żᱨ��������˵��ֻҪ���ǶԵģ��м������д�����ǻ�Ӱ������

###���û�и�Actionָ��class��
	struts.xml�̳е�struts-default.xml ��������һ��Ĭ�ϵ�class������˵���ᱨ��
	<default-class-ref name=""/>

###����Ҳ���Action��
	����Ҫ����Ĭ�ϵ�Action���ƣ�û�еĻ����ͻᱨ�����о�ִ���Ǹ���
	<default-action-ref name=""/>

###URL�ĺ�׺�������Զ��壨�Ḳ��ԭ�������ã�
��struts.xml ������:
	��ʹ�ö���Ļ����ö��ŷָ���Ĭ����action�Ϳ�
	name : ����Դ������ļ� default.properties�г�����
	value ������ֵ
	< constant name="struts.action.extension" value="myth">< /constant>
���ߣ�
	src���½�һ��default.properties ����ֻд��Ҫ�޸ĵĳ���
		struts.action.extension=myth 
	
	�����߶��޸��˰�����˳��
	1 struts-default.xml
	2 struts-plugin.xml
	3 struts.xml
	4 struts.properties
	5 web.xml
	������ͬ�ĳ������úã����߸���ǰ��
������struts.xml������

<-- ����URL��׺ Ĭ����action���-->
	< constant name="struts.action.extension" value="myth"></ constant>
	<-- ���ù��ʻ���Դ�ļ����޸�ʱ���Ƿ����¼��� Ĭ����false -->
	< constant name="struts.i18n.reload" value="true"></ constant> 
	<-- ����struts2��ܵ������ļ��޸�ʱ���Ƿ����¼��� Ĭ����false-->
	< constant name="struts.configuration.xml.reload" value="true"></ constant> 
	<--
		 ����struts2��ģʽ 
			false ����ģʽ Ĭ����false
			true ����ģʽ ��Ҫ����ĵ�����Ϣ ���Զ�������������������Ϊtrue
	-->
< constant name="struts.devMode" value="true">< /constant>

================================================================
�Զ���ʹ�õ� struts.xml ����·�����������֣�������˿���
��Ҫ��struts.xml��дһ��<include file=""></include>·��������srcΪ��㣬ע��ѵ㻻��  /

##��action����ת����
1����JSPҳ���ϵ�������ύ��actionʱ��ֻҪ��action������ͬ������������setget����
	��֮��ֱ��ʹ��get�������ܻ�ȡ��ֵ����װ�ɶ�����setgetҲ��һ�����Եĵ�����JSP�ϵ�input��name��Ҫ�Ӷ�������ǰ׺
	�����������������ݣ���ʹ��Collection���� Collection<T> ts;ͬ���ļ�setget������������JSP�ϵĶ��input��name��Ҫд�����ָ�ʽ
		ts[0].name ts[1].name......

2����struts��Щ�����޷�ת��ʱ������Ҫ�Զ���ת����
	�������ֶΡ����ֲ���
		* �ڵ�ǰaction�����½� convert.properties �ļ������Զ����
		* �ڸ��ļ��� xwork.default.fieldvalue=��Ч���ֶ�ֵ "{0}".
		* ��struts.xml�ļ����ظ���Դ�ļ�
			<constant name="struts.custom.i18n.resources" 
				value="cn.itcast.converter.converter,
						cn.itcast.i18n.resources">
		</constant>
	�������ࡿ��ȫ�֣���
		* ��srcĿ¼���½�һ��xwork-conversion.properties�ļ�
		* ���ݣ� ��ת��������=����ת������ȫ����
			���磺java.util.Date=cn.itcast.convert.DataConverter
3��result��ǩ��Ϊinput����Ĭ��Ϊ����ҳ�����ת����
	�ڴ���ҳ�����������Ϣ��<s:fielderror fieldName="createTime"/>
	�����ÿ���ֶθ�����ʾ��Ϣ��
		��converte.properties������һ��invalid.fieldvalue.createTime=****

��ע�⡿
	JSPҳ��������struts��ǩ<%@ taglib uri="/struts-tags" prefix="s" %>
	* �������ļ���ǵ�һ��Ҫ���ӵ�struts.xml�ļ���ȥ����û�ӣ�Ҳ������JSPҳ����ֱ��ʹ��
###����Servlet���
struts2 �� HttpServletRequest HttpSession ServletContext�����˷�װ����Map����
������һ��:   ͨ��ServletActionContext��ֱ�ӻ�ȡ
	�������actionִ�е������Ķ��󣬰�����parameter request session application�ȡ�
//�ֱ��������Ե�����request session application
	HttpServletRequest request = ServletActionContext.getRequest();
		request.setAttribute("username", "username_request");
	Map sessionMap = ServletActionContext.getContext().getSession();
		sessionMap.put("username", "username_session");
	ServletContext sc = ServletActionContext.getServletContext();
		sc.setAttribute("username", "username_application");
//JSPҳ��Ļ�ȡ��
    ${requestScope.username}<br>
    ${sessionScope.username}<br>
    ${applicationScope.username}<br>

###��ͨ��ʵ�ֽӿ�struts2�Զ�ע�롿
	ʵ�����ĸ��ӿڣ�ServletRequestAware��ServletResponseAware��ServletContextAware��SessionAware
	ʵ��������ֱ���HttpServletRequest��HttpServletResponse��Map��ServletContext
	��д�ĸ�set������������д��this.** = **;

##���ļ��ϴ���
��1����·һ�£�����������ʱ��action��һ����input��result�ſ���
��2��<-- �����ļ��ϴ����ܴ�С -->
	< constant name="struts.multipart.maxSize" value="2097152000"></ constant>
��3��������ʾ����
�½�һ��properties�ļ��������Զ���
	struts.messages.error.uploading=Error uploading: {0}
	struts.messages.error.file.too.large=File too large: {0} "{1}" "{2}" {3}
	struts.messages.error.content.type.not.allowed=Content-Type not allowed: {0} "{1}" "{2}" {3}
	struts.messages.error.file.extension.not.allowed=File extension not allowed: {0} "{1}" "{2}" {3}
	{0}��<input>��ǩ��name ����ֵ
	{1}���ϴ��ļ�����ʵ����
	{2}���ϴ��ļ����浽��ʱĿ¼������
	{3}���ϴ��ļ������ͣ�����too.large��˵���ϴ��ļ��Ĵ�С��
	
##���뵽struts�����ļ���ȥ

struts2��ܵ��ļ��ϴ���
	* ���ļ��ϴ���
		* �ڶ�����action������������ԣ�
			* �ڶ�����action�У�Ҫ������ҳ���б���name����ͬ�������ԣ�ͬ�������Ե�����ʱFile���ͣ�
			* �ڶ�����action�У�Ҫ����[ͬ��������]ContentType������ʱString���ͣ�
			* �ڶ�����action�У�Ҫ����[ͬ��������]FileName������ʱString����
			* �����������ṩget��set����
		* ��ҵ�񷽷��У������ļ��ϴ���
			* ��ȡҪ�ϴ��ļ���·���������λ��
			* ��Ŀ���ļ����ڣ�����һ�����ϴ��ļ�ͬ�����ļ�
			* ͨ��FileUtils�������ṩcopyFile()����������ʱ�ļ����ݿ�����Ŀ���ļ����µ��Ǹ�ͬ�����ļ�
		* �����ϴ��ļ����ܴ�С
			* ��struts.xml�ļ��У�<constant name="struts.multipart.maxSize" value="2097152000"></constant>
		* �����ϴ��ļ��Ĵ�С�����ͺ���չ����
			* ���Զ���������ļ��У���action��ǩ�£�
				<!-- �����������Ĳ������������ļ��ϴ������� -->
				<interceptor-ref name="defaultStack">
	              	<!-- 
	              		�����ļ��ϴ��������Ĳ���
	              			* �붨�������˳���޹�
	              			* ����������(allowedTypes)����������չ��(allowedExtensions)���뱣��һ��
	              	 -->
	              	<!-- 
	              		* �����ϴ��ļ��Ĵ�С
	              			* struts.xml�ļ������õ����ϴ��ļ����ܴ�С
	              			* �������õ����ϴ��ļ��ĵ�����С
	              	 -->
	              	<param name="fileUpload.maximumSize">20971520</param>
	              	<!-- �����ϴ��ļ����������ͣ�������ö��ֵ�Ļ�����","���� -->
	              	<param name="fileUpload.allowedTypes">text/plain,application/msword</param>
	              	<!-- �����ϴ��ļ�����չ����������ö��ֵ�Ļ�����","���� -->
	              	<param name="fileUpload.allowedExtensions">.txt</param>
	            </interceptor-ref>
	         * �Զ����ϴ��ļ��Ĵ�����ʾ��Ϣ��
	         	* �ڶ�����actionͬĿ¼�£�����һ����Ϊfileuploadmessage.properties��Դ�ļ�(��Ϊ�Զ���)
	         	* ����Դ�ļ��������£�
	         		struts.messages.error.uploading=Error uploading: {0}
					struts.messages.error.file.too.large=File too large: {0} "{1}" "{2}" {3}
					struts.messages.error.content.type.not.allowed=Content-Type not allowed: {0} "{1}" "{2}" {3}
					struts.messages.error.file.extension.not.allowed=File extension not allowed: {0} "{1}" "{2}" {3}
		
		
	* ���ļ��ϴ���
		* �������������ö��뵥�ļ��ϴ�һ�¡�
		* ��Ҫע����ǣ�
			* ��ҳ���У���Ȼ�Ƕ��ļ��ϴ�������ҳ���б�����name���Ե�ֵ���뱣��һ�£�
			* �ڶ�����action��������������ԣ����͸ĳ����飻
			* ��ҵ�񷽷��У���ش������̸ĳɵ��ļ��ϴ���ѭ����
##���ļ����ء�
 1�������ļ�ʱ ѹ��ֵջ�����������������Ҫת�룺fileName = new String(filename.getBytes(),"ISO-8859-1");
�����ļ�  filename=${filename}.xls
##��У�顿
####��struts2�ֶ���֤����
		Ҳ����˵�ֶ�����ֱ����action���д��validate���������� 
		������ֻҪ������дthis.addFieldError( key, value);�������ˣ��������ɿ��������
	* ����Ҫ��ҳ���л�ȡ��Ӧ�ı�ǩname���Ե�ֵ���ڶ�����action������ ͬ�������ԣ��ṩget��set����

	* Ҫ�̳�ActionSupport�����ʵ��Validateable�ӿ�
	
	* ��дValidateable�ӿڵ�validate()����
		* ǰ���ǣ�Ҫ��֤setUsername()��validate()��login()����Ҫ��������Ⱥ�˳��ִ��
	
	* �����¼ʧ�ܣ���δ�����
		* this.addFieldError( key, value);
			* key��������ʾ�ֶ�
			* value��������ʾ��Ϣ
	
	* ʲôʱ�������֤ͨ����
		* ��֤ͨ����1��map���ϲ����ڣ�2��map���ϴ��ڲ�Ϊ��
		* ��֤��ͨ����map���ϴ��ڲ��Ҳ�Ϊ��
	
	* ��������
		* �û�������Ϊnull ,""
		* ���벻��Ϊnull, "" ����������ĳ���6-12֮�� 
	
	* �������ҵ�񷽷�������֤�������ĳ��ָ��ҵ�񷽷�������֤��
		* ��д��validate()�������������ҵ�񷽷�������֤
		* ��д��validate()��������Ҫ��֤��ָ����ҵ�񷽷���(ҵ�񷽷���������ĸ��д)��ʵ�����ĳ��ָ����ҵ�񷽷�������֤
			* ΪʲôҪ��������ƴ�ӣ���Ϊstruts2��ܵײ�ƴ�ӣ����������д���ײ���Ҳ�����Ӧ������
	
####��struts2�����֤(xml��ʽ)��:
	* ����Ҫ��ҳ���л�ȡ��Ӧ�ı�ǩname���Ե�ֵ���ڶ�����action������ͬ�������ԣ��ṩget��set����
	
	* ����һ��xml��ʽ��֤�ļ���
		* ������ʽ��ActionClassName-validation.xml��ActionClassNameָ���Ƕ�����action������
		* <validators>��ǩ����Ԫ��
		* field��ָ��action��ҪУ������ԣ�ʵ���Ͼ���ҳ���б�����name���Ե�ֵ
			* name��ָ��ҳ���б�����name���Ե�ֵ
		* field-validator��ָ����֤����
			* type��ָ����֤�������ƣ�
					struts2����ṩ����֤�������xwork-core-xxx.jar
					�µ�com\opensymphony\xwork2\validator\validators
					��default.xml�����ļ���
		* param����ײ����֤���򴫵ݵĲ���
		* message����֤ʧ��ʱ���ṩ�Ĵ�����ʾ��Ϣ
	
	* ���Ҫ��ָ������������֤�Ļ���
		* xml��֤�ļ���������ʽ��ActionClassName-ActionName-validation.xml��
								ActionName��Ӧ����struts.xml�ļ���Ӧ��action��ǩ��name���Ե�ֵ

##���Զ�����������
�������� ���ԡ���

	������һ���ǺͶ�Ӧ��action�󶨵ģ���ԭ����filter�Ƕ�URLģʽ�������ص�

	# ִ��˳��ִ����struts�����õ�������ջ������intercept��������ִ��action��execute����
	# ���������� intercept����  ����null�ͻ����ִ��action 
		�����ǰ��͵�������actionʵ��������ִ���˷�����ô֮���action�Ͳ������ظ�ִ��
	# ����Ƿ�����������ִ�У��о�ȥִ�У�û�оͻ�õ�null��ͬ���ļ���ִ��action
			String result = invocation.invoke();
			return result;
������Զ�����������
#####1�� ���е�����������Ҫʵ��Interceptor�ӿڻ��߼̳�Interceptor�ӿڵ���չʵ����
	
#####2��Ҫ��дinit()��intercept()��destroy()����
	
		* init()����struts2�������ʱִ�У���������������������ִֻ��һ�Σ���������Ҫ�����ݵĳ�ʼ������
		
		* intercept()����ÿһ�������ִ��һ�Σ�����ش���������
		
			* intercept()��������һ��ActionInvocation�ӿڵ�ʵ��
			
			* ͨ������ӿڵ�ʵ�������Ի�ȡ��������
			��
					//cn.itcast.aop.UserAction @15b5783�� ������Ķ���
				System.out.println("invocation.getAction() : "+invocation.getAction());
					//cn.itcast.aop.UserAction @15b5783�� ��invocation.getAction()������ȡ����ͬһ�Ķ���
				System.out.println("invocation.getProxy().getAction() : "+invocation.getProxy().getAction());
					//userAction_save���Զ��������ļ��е�action��ǩ��name���Ե�ֵ
				System.out.println("invocation.getProxy().getActionName() : "+invocation.getProxy().getActionName());
					//save����Ӧ������ָ��Ҫִ�еķ�����
				System.out.println("invocation.getProxy().getMethod() : "+invocation.getProxy().getMethod());
					//	/aop���Զ��������ļ��е�package��ǩ��namespace���Ե�ֵ
				System.out.println("invocation.getProxy().getNamespace() : "+invocation.getProxy().getNamespace());
		* destroy()��������������ǰִ�У���������������������ִֻ��һ�Ρ�
		
#####3�� ��struts.xml�����ļ��У�����ע��
		* �������ļ��е�package��ǩ�£�����������ã�
		
		<interceptors>
			<!-- �����Զ���������� -->
			<interceptor name="expessionInterceptor" class="cn.itcast.aop.ExpessionInterceptor" />
			<!-- �����Զ���������ջ -->
			<interceptor-stack name="expessionStack">
				 <interceptor-ref name="defaultStack"/>
				 <!-- ����ʹ���Զ��������� -->
				 <interceptor-ref name="expessionInterceptor"/>
			</interceptor-stack>
		</interceptors>
		<!-- �����޸�struts2�������ʱ��Ĭ��ִ�е����Զ���������ջ -->
		<default-interceptor-ref name="expessionStack" />
		
		������ŵľ���action��������
	
##��ognlѧϰ��

###��valueStack����
	ValueStackʵ������һ���ӿڣ���struts2������OGNLʱ��ʵ������Ŷ�Ǹ�����ʵ���˸ýӿڵ�OgnlValueStack�࣬�����������OGNL�Ļ���
	�ᴩ����action�������ڣ�ÿ��action��Ķ�����һ��valueStack�����൱��һ�����ݵ���תվ�������б����˵�ǰaction�����������ض���
	struts��ܰ�valueStack���󱣴�����Ϊ ��struts.valueStack�������������У�request�У�

		 ValueStack vs = (ValueStack)request.getAttribute("struts.valueStack");
		 vs.set("key","value");//ʵ�����Ƿ�����Map�������ٷ���ջ���
		 vs.getRoot().add(0,new Person());//��person����ѹ��List���ϵ�0λ�ã�ջ����
	
###������OGNL Context�� ������
	# OgnlValueStack�����������Ҫ�����ԣ�root �� context 
	     * ����toot��������һ��List����
	     * Context��һ��Map��ȷ�е�˵��һ��OgnlContext����
	# �����OgnlContext�����У���һ��Ĭ�ϵĶ������ root OGNL����context�����Ĭ�϶�������е�Ԫ��ʱ����Ҫ#�ţ�ֱ��ͨ������������
	# ��������������ʱ�� request��session��attr ������Ҫ#�����á�
	�ܽ᣺ognl Context����ObjectStack���Ժ�ContextMap����

	 �ײ��ࣺ
		public class OgnlValueStack implements ValueStack {
			 CompoundRoot root;    ---  list����
			transient Map<String, Object> context;  --- map����
		}
												
			
##��OGNL����ʽ����ʾ��JSP��
ʵ�ʲ����Ĳ���ֵջ������ֵջ�����ԣ�Context�������ģ�����һ��Map���ϣ�

	����ʹ��EL����ʽȡֵ-----------------------------------------<br>
		${requestScope.username}<br>
		${sessionScope.username}<br>
		${applicationScope.username}<br><br><br><br>
	����ʹ��Ognl����ʽȡֵ-----------------------------------------<br>
				������Map���ϼ�#��
####1.�����������Context�еĶ����������ǲ��Ǹ����������ڷ���ʱ����Ҫ����#ǰ׺��<br>
		<s:property value="#request.username"/><br>
		<s:property value="#session.username"/><br>
		<s:property value="#application.username"/><br><br>
		<s:property value="#request['username']"/><br>
		<s:property value="#parameters.cid[0]"/><br>
		<s:property value="#attr.username"/><br><br>
			�����ʶ���ջ�ж���ɲ���#��
#### 2.���Ҫ���ʸ����󣨼�ValueStack���ж�������ԣ������ʡ��#��������ֱ�ӷ��ʸö�������Լ��ɡ�<br>
		<s:property value="msg"/><br><br>
		��������ֵջ�е� ObjectStack<br>
		����̨���룺�� vs.getRoot().add(0,new Person()); 
		<s:property value="name"/><br> �����ж��name��������ֻȡ��ջ�е�һ��
		<s:property value="sex"/><br>
		<s:property value="age"/><br>
		<s:property value="salary"/><br><br>
	
	
####�÷�3:����Map<br>
		<s:radio list="#{'01':'��','02':'Ů'}"></s:radio><br><br><br><br>
		%���÷�����%�����ŵ���;���ڱ�ǩ������ֵ������Ϊ�ַ�������ʱ������ִ�л���%{}�����OGNL����ʽ�� <br>
		<s:property value="#request.username"/><br>
		<s:property value="%{#request.username}"/>%{}�������÷�����������ı���ʽ�ǲ���ognl����ʽ������ǿ������Ϊognl����ʽ<br><br>
		
����$����������Ҫ����;��

	    1 *  �����ڹ��ʻ���Դ�ļ��У�����OGNL����ʽ<br>
		<s:text name="ognl" /><br><br>
			��properties�ļ������ã�ognl=${error} ognl
			ȡ����ֵջ�е�error����  ���룺valueStack1.set("error", "error_valueStack");
	    
	    2 *  ��Struts 2�����ļ��У�����OGNL����ʽ<br>
	    <s:property value="#parameters.msg[0]"/><br><br>
		 <result name="s" >ognl/ognl.jsp?msg=${msg}</result>
			�����msg��request��param ʹ�� ${} ���ʵĶ���ֵջ���
		
	<s:debug></s:debug> �ܲ鿴ֵջ״̬

##��OGNL��ǩ��