
# HTTPS Requests via Java not working due to Lets Encrypt SSL Certificates.

## Windows

### Link to download the let's encrypt certificate: 

[Lets Encrypt Certificate](https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.der)

Save the certificate in your downloads folder and 

### Open Command Prompt as Administrator, and run the Command to install Let's Encrypt certificate:

if your java folder is located in **Program Files** use the 64bit version

if your java folder is located in **Program Files (x86)** use the 32bit version

*Check your java version and change [ jdk1.8.0_131 ] to match your installed JDK version, the JDK is located in your Java folder*

#### 64bit Java
``` "C:\Program Files\Java\jdk1.8.0_131\bin\keytool" -trustcacerts -keystore "C:\Program Files\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file %USERPROFILE%\downloads\lets-encrypt-x3-cross-signed.der ```

#### 32bit Java
``` "C:\Program Files (x86)\Java\jdk1.8.0_131\bin\keytool" -trustcacerts -keystore "C:\Program Files (x86)\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file %USERPROFILE%\downloads\lets-encrypt-x3-cross-signed.der ```

## Ubuntu / Linux

### Download a [script](https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e) which will download and install the certificates for you on your server

``` wget https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e/raw/15926be913682876ae68bb4f71e489bc53feaae3/install-letsencrypt-in-jdk.sh ```

*[source of script](https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e)*


### Run the script
``` bash ./install-letsencrypt-in-jdk.sh ```

### Restart tomcat
``` service tomcat8 restart ```



