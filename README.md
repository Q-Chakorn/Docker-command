# Docker-command
install docker sudo snap install docker
sudo apt-get update

1) คำสั่งดูเลขเวอร์ชั่น docker engine ในเครื่อง
	docker -v 

2) คำสั่งล็อกอินเข้าไปใน docker hub (ที่เก็บไฟล์ image ของ docker)
	docker login

3) คำสั่ง logout ออกจาก docker hub ...บาย บาย
	docker logout 

4) คำสั่งค้นหาไฟล์ image จาก docker hub
	docker search <IMAGE>

5) คำสั่งดาวน์โหลดไฟล์ image จาก docker hub มาที่เครื่องเรา
	docker pull <image_name>:<tag> 

6) คำสั่งรันไฟล์ image  -> เพื่อสร้าง container (สร้างกี่ตัวก็ได้)
	docker run [options] <image_name>:<tag>

7) คำสั่งดูรายชื่อไฟล์ images ที่อยู่ในเครื่องเรา
	docker images
	docker images --no-trunc // แสดง Images ID แบบเต็มๆ

8) คำสั่งลบไฟล์ images 
	docker rmi <image_name> // ถ้ามี container ที่เกิดจาก image นั้นทำงานอยู่จะลบไม่ได้
	docker rmi -f <image_name> // บังคับให้ลบ
	docker rmi -f $(docker images -a -q) // ลบทั้งหมด

9) คำสั่งดูรายชื่อ container 
	docker ps // แสดง container ที่ทำงานอยู่
	docker ps -a // แสดงรายการ container ทั้งหมดที่ทำงานอยู่และหยุดทำงานไปแล้ว

10) คำสั่งลบ container
	docker rm <container_name> // container ที่กำลังทำงานไม่ได้ ต้อง stop ก่อน
	docker rm -f <container_name> // บังคับลบ
	docker rm $(docker ps -a -q) // ลบทั้งหมด
	docker rm $( docker ps -q -f status=exited) // ลบ container ทั้งหมดที่ไม่ทำงาน

11) คำสั่งสั่งให้ container ทำงาน (สตาร์ท)
	docker start <container_name>

12) คำสั่งหยุด container (กลับมาสตาร์ทใหม่ภายหลังได้)
	docker stop <container_name>
	docker stop $(docker ps -a -q) // หยุดการทำงาน container ทั้งหมด

13) คำสั่งแช่แข็ง container
	docker pause <CONTAINER_ID> 
	docker unpause <CONTAINER_ID> //เลิกแช่แข็ง

14) คำสั่งเข้าไปใน container แล้วรันคำสั่ง เช่น รัน bash shell ของ linux
	docker exec -it <container_name> <command>

14) คำสั่งดูข้อมูลของ container
	docker inspect <container_name>

15) คำสั่งดูการใช้ทรัพยกรเครื่องของ container
	docker stats // ทั้งหมด
	docker stats <container_name> // ระบุชื่อ container ถ้าดูแบบหลายตัวให้เว้นวรรคชื่อ container

16) คำสั่งดู logs ของ container
	docker logs 

16) คำสั่งคำสั่งสร้างไฟล์ image
	docker build [OPTIONS] PATH | URL | -
	sudo docker build -t avalantglobal/oneweb4-designer-suites:1234

17) คำสั่ง commit ไฟล์ image ที่เราสร้าง
	docker commit  <CONTAINER_ID> <NEW IMAGE NAME>

18) คำสั่งส่งไฟล์ image  ขึ้น docker hub
	docker image push [OPTIONS] NAME[:TAG]
	sudo docker push avalantglobal/oneweb4-designer-suites:V22.05.20220606.1116.un .

19) คำสั่ง save , load ไฟล์ image
	docker save <imagesname> > /path/<name>
	docker load < /path/<name>

