# elasticsearch_project

执行脚本位置：sh /data/etl_script/qding_userprofile/base_user_info/copyESToES.sh
#! /bin/bash
date=$1
date=${date:=`date +%Y-%m-%d  -d "1 days ago"`}
echo $date

jar_path=/data/etl_script/qding_jar_file/qdbigdata-0.1.8.1-jar-with-dependencies.jar


srcClustName=bigdata-ES
srcIndexName=bigdata_system_monitor
srcIp=10.50.8.244
srcPort=9300

tagClustName=qdp-es
tagIndexName=test
tagTypeName=logs
tagIp=10.50.6.34
tagPort=9300

/hdata1/bigdata/jdk/jdk1.8.0_11/bin/java  -Xms2048m -Xmx2048m -XX:PermSize=128m -XX:SurvivorRatio=2 -XX:+UseParallelGC  -cp $jar_path  com.qding.es.CopyESToES $srcClustName  $srcIndexName $srcIp $srcPort  $tagClustName  $tagIndexName  $tagTypeName $tagIp  $tagPort 
