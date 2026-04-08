# Belajar Spring Dasar

by Programmer Zaman Now

# Trigger jenkins

#step 1
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH

java -version
mvn -version

mvn clean install

#step 2
./mvnw compile test-compile

#step 3
./mvnw test
