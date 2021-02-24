# JavaSpring


Config  file 'Amit-Servlet'   for Hibernate 


<?xml version="1.0" encoding="UTF-8"?>

<beans xmlns="http://www.springframework.org/schema/beans"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

xmlns:p="http://www.springframework.org/schema/p"

xmlns:mvc="http://www.springframework.org/schema/mvc"

xmlns:tx="http://www.springframework.org/schema/tx"

xmlns:context="http://www.springframework.org/schema/context"

xsi:schemaLocation="

http://www.springframework.org/schema/beans

http://www.springframework.org/schema/beans/spring-beans-2.5.xsd

http://www.springframework.org/schema/mvc

http://www.springframework.org/schema/beans/spring-mvc-3.0.xsd

http://www.springframework.org/schema/tx

http://www.springframework.org/schema/tx/spring-tx.xsd

http://www.springframework.org/schema/context

http://www.springframework.org/schema/context/spring-context-2.5.xsd">



<context:component-scan base-package="com.springmvc12"></context:component-scan>

<context:annotation-config></context:annotation-config>


----------------------LOCAL DATA ---------------------------------------------------
<bean id="myDataSource" class="com.mchange.v2.c3p0.ComboPoolDataSource" destroy-method="close">

<property name="driverClass" value="com.mysql.jdbc.Driver"></property>

<property name="jdbcUrl" value="jdbc:mysql://localhost:3306/telusko"></property>

<property name="user" value="root"></property>

<property name="password" value="12345678"></property>

<property name="minPoolSize" value="5"></property>

<property name="maxPoolSize" value="10"></property>

<property name="maxIdleTime" value="30000"></property>

</bean>


<bean id="sessionFactory" class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">

<property name="dataSource" ref="myDataSource"/>

<property name="packagesToScan" value="com.springmvc12.alien"/>

<property name="hibernateProperties">

<props>

<prop key="hibernate.dialect">org.hibernate.dialect.MySQLDialect</prop>

<prop key="hibernate.show_sql">true</prop>

</props>

</property>

</bean>


<bean id="myTransactionManager" class="org.springframework.orm.hibernate5.HibernateTransactionManager">

<property name="sessionFactory" ref="sessionFactory"></property>

</bean>

<tx:annotation-driven transaction-manager="myTransactionManager"/>


<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">

<property name="prefix" value="/views/"></property>

<property name="suffix" value=".jsp"></property>

</bean>

</beans>
