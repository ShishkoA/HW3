# Tasks
​
<h5> Awk /ɔːk/ /<h5>
<h6> 1. What is the most frequent browser?</h6>
<p>Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)</p>
<h6> 2. Show number of requests per month for ip 216.244.66.230 (for example: Sep 2016 - 100500 reqs, Oct 2016 - 0 reqs, Nov 2016 - 2 reqs...)</h6>
<p>grep "216.244.66.230" access.log | awk '{print $4}' | awk -F/ '{ print $2"/"$3 }' | awk -F: '{ print $1 }' |  uniq -c</p>
<p>awk ' /216.244.66.230/ {print $4}' | awk -F/ '{ print $2"/"$3 }' | awk -F: '{ print $1 }' |  uniq -c</p>
<h6> 3. Show total amount of data which server has provided for each unique ip (i.e. 100500 bytes for 1.2.3.4; 9001 bytes for 5.4.3.2 and so on)</h6>
​awk '{arr[$1]+=$10} END {for (i in arr) {print i,arr[i]/1048576 " MB"}}' access.log | sort -n
<h5> Sed </h5>
<h6>1. Change all browsers to "lynx"</h6>
sed -i 's/"Mozilla\/[0-9].[0-9]\([^"]*\).*/lynx/g' access.log
<h6>2. Masquerade all ip addresses. Rewrite file.</h6>
sed 's/[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}/SOMETHING/g' access.log
