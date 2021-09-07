# Instructions
* Install the required modules with `pip install -r requirements.txt`
* This installs the falcon library and the gunicorn webserver.
* Run the app with `gunicorn app:app`
* You can test if the app is running by `curl http://localhost:8000/things`
* Configure Jenkins to use JDK 11 (Manage Jenkins -> Global Tools -> Add JDK -> Name: jdk-11 , label : leave blank, url: https://download.java.net/openjdk/jdk11/ri/openjdk-11+28_linux-x64_bin.tar.gz, subdirectory: jdk-11 )
