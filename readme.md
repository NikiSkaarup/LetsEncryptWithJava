
# HTTPS Requests via Java not working due to Lets Encrypt SSL Certificates.

## Windows

### Link to download the let's encrypt certificate: 

[Lets Encrypt Certificate](https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.der)

Save the certificate in your downloads folder

### Open Command Prompt as Administrator, and run the Command to install Let's Encrypt certificate:

If JAVA_HOME is set in your SYSTEM Enviroment Variables, use the Simple Versions

if your java folder is located in **Program Files** use the 64bit version

if your java folder is located in **Program Files (x86)** use the 32bit version

*Check your java version and change [ jdk1.8.0_131 ] to match your installed JDK version, the JDK is located in your Java folder*

#### Simple version
``` "%JAVA_HOME%\bin\keytool" -trustcacerts -keystore "%JAVA_HOME%\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file %USERPROFILE%\downloads\lets-encrypt-x3-cross-signed.der ```

#### 64bit Java
``` "C:\Program Files\Java\jdk1.8.0_131\bin\keytool" -trustcacerts -keystore "C:\Program Files\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file %USERPROFILE%\downloads\lets-encrypt-x3-cross-signed.der ```

#### 32bit Java
``` "C:\Program Files (x86)\Java\jdk1.8.0_131\bin\keytool" -trustcacerts -keystore "C:\Program Files (x86)\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file %USERPROFILE%\downloads\lets-encrypt-x3-cross-signed.der ```

### certificate already exists error

#### Simple version

``` "%JAVE_HOME%\bin\keytool" -delete -alias lets-encrypt-x3-cross-signed -keystore "%JAVE_HOME%\jre\lib\security\cacerts" -storepass changeit ```

#### 64bit Java
``` "C:\Program Files\Java\jdk1.8.0_131\bin\keytool" -delete -alias lets-encrypt-x3-cross-signed -keystore "C:\Program Files\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit ```

#### 32bit Java
``` "C:\Program Files (x86)\Java\jdk1.8.0_131\bin\keytool" -delete -alias lets-encrypt-x3-cross-signed -keystore "C:\Program Files (x86)\Java\jdk1.8.0_131\jre\lib\security\cacerts" -storepass changeit ```

## Ubuntu / Linux

### Run the command below to download a [script](https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e) which can download and install the certificates for you on your server

``` wget https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e/raw/15926be913682876ae68bb4f71e489bc53feaae3/install-letsencrypt-in-jdk.sh ```

*[source of script](https://gist.github.com/Firefishy/109b0f1a90156f6c933a50fe40aa777e)*


### Run the script
``` bash ./install-letsencrypt-in-jdk.sh ```

### Restart tomcat so it will be using the updated certificates
``` service tomcat8 restart ```

## Mac OS - by radeonxray

###Step 1:
From https://www.mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/

#### MacOS Terminal:

Run: ``` nano .bash_profile ```

Insert the following: ``` export JAVA_HOME=$(/usr/libexec/java_home) ```
Save and close nano (*ctrl + x, ctrl + y*)

Run: ``` source .bash_profile ```
(Nothing happens, that's ok)

Run: ``` echo $JAVA_HOME ```
(Terminal should now show/point to the Path)

###Step 2:
From http://stackoverflow.com/questions/34110426/does-java-support-lets-encrypt-certificates

MacOS Terminal:
Run: ``` sudo cp -a $JAVA_HOME/jre/lib/security/cacerts $JAVA_HOME/jre/lib/security/cacerts.orig ```

Run: ``` wget https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.der ```
(requires you have already installed wget on MacOS, if not, run: brew install wget)

Run: ``` sudo keytool -trustcacerts -keystore $JAVA_HOME/jre/lib/security/cacerts -storepass changeit -noprompt -importcert -alias lets-encrypt-x3-cross-signed -file lets-encrypt-x3-cross-signed.der ```

Restart the Tomcat server and/or Netbeans project.
