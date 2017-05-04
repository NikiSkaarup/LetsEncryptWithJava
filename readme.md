
# HTTPS Requests via Java not working due to Lets Encrypt SSL Certificates.

## Link to download the let's encrypt certificate: 
[Lets Encrypt Certificate](https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.der)

## Open Command Prompt as Administrator, and run the Command to install Let's Encrypt certificate:
*Check your java version and change [ jdk1.8.0_131 ] to match your installed JDK version*

### 64bit Java
``` keytool -trustcacerts -keystore "C:\Program Files\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file lets-encrypt-x3-cross-signed.der ```

### 32bit Java
``` keytool -trustcacerts -keystore "C:\Program Files (x86)\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file lets-encrypt-x3-cross-signed.der ```
