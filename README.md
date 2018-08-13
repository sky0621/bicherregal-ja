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
asia-south1              YES                YES
australia-southeast1     YES                YES
europe-west              YES                YES
europe-west2             YES                YES
europe-west3             YES                YES
northamerica-northeast1  YES                YES
southamerica-east1       YES                YES
us-central               YES                YES
us-east1                 YES                YES
us-east4                 YES                YES
us-west2                 YES                YES
</pre>
<pre>
$ gcloud app create --project=XXXXXXXX --region=asia-northeast1
</pre>

## deploy Open API
<pre>
$ gcloud endpoints services deploy openapi-appengine.yaml
</pre>

## setup java
<pre>
$ mvn archetype:generate -DgroupId=bicherregal -DartifactId=bicherregal
</pre>

##
<pre>
$ mvn appengine:stage
$ gcloud beta app deploy target/appengine-staging
</pre>
