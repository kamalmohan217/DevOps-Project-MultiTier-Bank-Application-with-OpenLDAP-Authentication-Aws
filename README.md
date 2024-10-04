# DevOps-Project-MultiTier-Bank-Application-with-OpenLDAP-Authentication-Aws

For configuration of Open LDAP followed the steps as mentioned in the screenshot attahed below.

![image](https://github.com/user-attachments/assets/a3044284-f208-4b77-b223-3f308f65c54e)

Edit the password for general setting as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/bee2b711-a278-499f-8b19-1f181694b4f6)
![image](https://github.com/user-attachments/assets/e6fa37c7-ed74-4d7f-9551-289f4450df37)

Edited the server profile as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/98761ce6-226c-4015-ba00-208a8ada1405)
![image](https://github.com/user-attachments/assets/33effb02-2d9f-45ac-adb3-29c917502c5a)
![image](https://github.com/user-attachments/assets/17ec1665-28f3-4a25-a300-0286cc543bec)
![image](https://github.com/user-attachments/assets/5bea9ed3-ff97-46f0-b0c3-f927e2da69ff)
![image](https://github.com/user-attachments/assets/04dd1322-0fc7-453c-9c4b-ad6e1db3dd7d)

The default password for general setting and server profile is **lam** but I changed it as shown in the screenshot attached above and using the changed password I was able to login.

![image](https://github.com/user-attachments/assets/0c5639be-26d5-4e4a-8b2e-a8c52e457551)

After the changes as mentioned above tree view is as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/5dfadc25-5e20-4f68-9e6c-21e3bf087b3a)

Now Login with the Open LDAP Manager password as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/f1421b70-b0b0-4ddb-892e-3caaf422d1e9)

I had create a Group with the name of sysadmin and User with the name of dexter as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/c76314ce-da91-416d-b852-d711764aa33e)
![image](https://github.com/user-attachments/assets/5686a247-8e32-409a-b28d-e70710c8bfaf)

I will Login into Jenkins, SonarQube and Nexus using the user dexter and provided administrator privilege to the user dexter.

**Authentication in Jenkins using Open LDAP**

![image](https://github.com/user-attachments/assets/cfd26ec9-06ea-409b-aeb2-3dec8a1998c1)
![image](https://github.com/user-attachments/assets/f40d7715-dffa-4bf8-9357-7bdb2115fbf3)

**Authentication in SonarQube using Open LDAP**
```
vim /opt/sonarqube/conf/sonar.properties             


sonar.security.realm=LDAP
ldap.url=ldap://IP_Address_of_OpenLDAP_Server:389                                           
ldap.bindDn=cn=ldapadm,dc=singhritesh85,dc=com
ldap.bindPassword=Admin123
ldap.user.baseDn=ou=People,dc=singhritesh85,dc=com
ldap.user.request=(&(objectClass=inetOrgPerson)(uid={login}))
ldap.user.realNameAttribute=cn
ldap.user.emailAttribute=mail
ldap.group.baseDn=ou=Group,dc=singhritesh85,dc=com
ldap.group.request=(&(objectClass=groupOfUniqueNames)(uniqueMember={dn}))
sonar.log.level=DEBUG



Now Restart the Sonarqube.
```
Now you will be able to login with Open LDAP user dexter as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/f2e8d9a8-b6f1-4c70-b183-da341119acf2)

Here you need to provide privilege to the dexter user in SonarQube which you could do as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/d82b2722-053b-4088-8c63-8194167acfe5)

Configure OpenLDAP for Authentication Sonatype Nexus as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/a1d7e64f-0fe7-400a-b91c-66c70d8c38c8)
![image](https://github.com/user-attachments/assets/2eab89a6-211b-4642-946a-76e468691ca7)
![image](https://github.com/user-attachments/assets/7cbe8bcc-0286-4c9a-b89f-300a5363d6c9)
![image](https://github.com/user-attachments/assets/90f26cab-608b-4fe2-b617-9192b3c4b92c)
![image](https://github.com/user-attachments/assets/3d818a2b-a2ee-44d0-b7cb-76d12898af90)
![image](https://github.com/user-attachments/assets/527bb670-f6a0-47f5-91cd-7bcb0277df5b)
![image](https://github.com/user-attachments/assets/a9ec6add-5054-40d1-8d96-e76096db6615)
![image](https://github.com/user-attachments/assets/5edc3ac3-2133-4f59-8851-ed3176313153)

Now to provide Administrator privilege to OpenLDAP user dexter follow the below steps.

![image](https://github.com/user-attachments/assets/e88f1bfa-2d7f-4151-817a-46f216e3497c)
![image](https://github.com/user-attachments/assets/12dec1cc-781b-4088-be2a-941eaa1eab78)

Do the installation of plugins SonarQube-Scanner, Nexus Artifact Uploader and Pipeline Utility Step as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/de922e89-1f6a-4e96-924e-1faeb07be306)

The two Jenkins Job has been as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/74eea426-7813-4691-8f0e-0dcdd0b9f3db)

After running the Jenkins Job screenshot of SonarQube, Nexus and ArgoCD is as shown in the screenshot attached below.

![image](https://github.com/user-attachments/assets/a6d2e627-8f9f-4543-b215-4e85ec412990)
![image](https://github.com/user-attachments/assets/f929d291-1105-4f3e-bc4b-620d447ff32c)
