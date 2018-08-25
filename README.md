# bicherregal-ja

## env
<pre>
$ cat /etc/os-release
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
</pre>

## setup gcloud and GAE
<pre>
$ gcloud components update
</pre>
<pre>
$ gcloud auth login
</pre>
<pre>
$ gcloud config set project XXXXXXXX
Updated property [core/project].
</pre>
<pre>
$ gcloud app regions list
REGION                   SUPPORTS STANDARD  SUPPORTS FLEXIBLE
asia-northeast1          YES                YES
　　〜〜〜
</pre>

## create app engine
<pre>
$ gcloud app create --project=XXXXXXXX --region=asia-northeast1
</pre>

## create maven project
<pre>
$ mvn -v
Apache Maven 3.5.0
Maven home: /usr/share/maven
Java version: 1.8.0_181, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-oracle/jre
Default locale: ja_JP, platform encoding: UTF-8
OS name: "linux", version: "4.13.0-46-generic", arch: "amd64", family: "unix"
</pre>

<pre>
$ mvn archetype:generate -Dappengine-version=1.9.63 -Djava8=true -Dfilter=com.google.appengine.archetypes:

[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0)
Choose archetype:
1: remote -> com.google.appengine.archetypes:appengine-flexible-archetype (A basic Java application with Google App Engine flexible.)
2: remote -> com.google.appengine.archetypes:appengine-skeleton-archetype (A skeleton application with Google App Engine)
3: remote -> com.google.appengine.archetypes:appengine-standard-archetype (A basic Java application with Google App Engine Standard)
4: remote -> com.google.appengine.archetypes:endpoints-skeleton-archetype (A skeleton project using Cloud Endpoints Frameworks with Google App Engine Standard)
5: remote -> com.google.appengine.archetypes:guestbook-archetype (A guestbook application with Google App Engine)
6: remote -> com.google.appengine.archetypes:hello-endpoints-archetype (A simple starter application using Cloud Endpoints Frameworks with Google App Engine Standard)
7: remote -> com.google.appengine.archetypes:skeleton-archetype (Archetype with a README about Google App Engine archetypes)

Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 6
Choose com.google.appengine.archetypes:hello-endpoints-archetype version: 
1: 1.0
2: 1.1
3: 1.1.1-1.9.4
4: 1.1.2-1.9.20
5: 1.1.3-1.9.20
6: 1.1.4-1.9.21
7: 1.1.4-1.9.25
8: 1.1.5-1.9.38
9: 2.0.0
Choose a number: 9: 1

Define value for property 'groupId': bicherregal
Define value for property 'artifactId': bicherregal                                     
Define value for property 'version' 1.0-SNAPSHOT: : 
Define value for property 'package' bicherregal: : 
[INFO] Using property: appengine-version = 1.9.63
Confirm properties configuration:
groupId: bicherregal
artifactId: bicherregal
version: 1.0-SNAPSHOT
package: bicherregal
appengine-version: 1.9.63
 Y: : Y

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 05:15 min
[INFO] Finished at: 2018-08-26T01:08:48+09:00
[INFO] Final Memory: 19M/194M
[INFO] ------------------------------------------------------------------------
</pre>

## build project
<pre>
$ mvn clean install
</pre>
- リソースファイル未定義のためスキップ
<pre>
[INFO] skip non existing resourceDirectory /work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/src/main/resources
</pre>
- コンパイル
<pre>
[INFO] Compiling 3 source files to /work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/bicherregal-1.0-SNAPSHOT/WEB-INF/classes
</pre>
- テストコードが無いので
<pre>
[INFO] No tests to run.
</pre>
- warファイル作成
<pre>
[INFO] Assembling webapp [bicherregal] in [/work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/bicherregal-1.0-SNAPSHOT]
[INFO] Processing war project
[INFO] Copying webapp webResources [/work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/generated-sources/appengine-endpoints] to [/work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/bicherregal-1.0-SNAPSHOT]
[INFO] Copying webapp resources [/work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/src/main/webapp]
[INFO] Webapp assembled in [192 msecs]
[INFO] Building war: /work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/bicherregal-1.0-SNAPSHOT.war
</pre>
- ローカルMavenリポジトリにwarファイルをインストール
<pre>
[INFO] Installing /work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/target/bicherregal-1.0-SNAPSHOT.war to /home/koge/.m2/repository/bicherregal/bicherregal/1.0-SNAPSHOT/bicherregal-1.0-SNAPSHOT.war
[INFO] Installing /work/src/java/github.com/sky0621/bicherregal-ja/bicherregal/pom.xml to /home/koge/.m2/repository/bicherregal/bicherregal/1.0-SNAPSHOT/bicherregal-1.0-SNAPSHOT.pom
</pre>

## start dev server
<pre>
$ mvn appengine:devserver
</pre>

## access local web
<pre>
http://localhost:8080/
</pre>
