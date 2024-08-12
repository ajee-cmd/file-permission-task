#!bin/bash
if[  "$#" -ne1 ]; then

fi
file=$1
mkdir process-parent
grep "process" $file > process-parent/found_processes.txt
df -h > process-parent/system resources.log
free -h >> process-parent/system_sources.log
ps aux --sort=%mem | head -n 6 > process-parent/process.log
mkdir process-jar
cp java_app/myapp.jar process-jar/
sudo useradd -g root linuxuser
sudo chown linuxuser:root process-jar/myapp.jar
sudo chmod 700 process-jar/myapp.jar
sudo -u linuxuser:root java -jar process-jar/myapp.jar
mkdir process-final
HOST_IP=$(hostname -I| awk  '{print $1}')
CURRENT_DATETIME=$(date)
echo "hi iam @priya, logges into machine @${HOST_IP},at ${CURRENT_DATETIME}
echo "" >> process.final/final_log.log
echo "content of process.log:" >> process-final/final_log.log
cat process-parent?process.log >> process-final/final_log.log
#rm -rf process-parent process-jar process-final
sudo userdel linuxuser
