EasyPACS - Dicom Server
=======================

EasyPACS is the simpliest PACS server for your dicom files. It uses DCM4CHEE listener and converts dicom files into jpegs. It is the easiest way to store dicom files.

For details:  http://mehmetsen80.github.io/EasyPACS/ 

# Updates

This project appears to have been abandoned, but I've been using it for testing and some demo work.   As such I've worked through the kinks of getting it running, and included updated installation instructions below.  It is VERY important to use the versions specified, as the versions of Spring used are very old.   Do not use this in production.


## Deployment

Requires Windows Server (have not tested it on Linux) I've successfully deployed on Server 2016 and 2019.

1.  Install Java 1.8u202 32-bit (both the JRE and the JDK)
2.  Install The Java Advanced Imaging ImageIO tools found here: http://mirc.rsna.org/ImageIO/jai_imageio-1_1-lib-windows-i586-jre.exe
3.  Download and install Gradle 2.3: https://services.gradle.org/distributions/gradle-2.3-bin.zip
4.  Be sure to set the the path to include the bin directory of wherever you installed Gradle (in my case C:\Gradle\gradle-2.3\bin
5.  Setup and install your database (Postgres or MySQL)  
6.  Create the database using one of the two SQL scripts included in the setup subdirectory
7.  From the root of the repository, run "gradle wrapper" then "gradle build"
8.  Copy the resulting JAR file found in build/libs to C:\EasyPACs or wherever you would like to install the application.
9.  Create a /img and /dcm directory where you would like to store your images and dicom files respectively
9.  Copy the application.properties file from src/main/resources to the same directory where you installed EasyPACs and modify it appropriately.  Be sure to set the correct IP and port for your database, database name, and login credential.   Also update the paths for pacs.storage.dcm and pacs.storage.image appropriately
10.  Startup the service:  java -jar <jarfilename> 

