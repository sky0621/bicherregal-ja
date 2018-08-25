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

## setup java
<pre>
$ mvn -v
Apache Maven 3.5.0
Maven home: /usr/share/maven
Java version: 1.8.0_181, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-oracle/jre
Default locale: ja_JP, platform encoding: UTF-8
OS name: "linux", version: "4.13.0-46-generic", arch: "amd64", family: "unix"

$ mvn archetype:generate -DgroupId=bicherregal -DartifactId=bicherregal
</pre>
