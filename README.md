# CIE-IVI
IVI Project done under CIE

# Building applications for IVI systems using Android Automotive OS  

## Week 1 : 
- The host machine, crucial for our development environment, was equipped with Python 2.7, rendering the 'repo sync' command ineffective.
- Faced with this obstacle, our team delved into the documentation to identify a solution. After thorough research and collaboration, we pinpointed the necessity to update the Python version to 3.8. 
- Despite the initial setback, we successfully upgraded the Python version, ultimately enabling the 'repo sync' command to function seamlessly. 

### Highlights:
1. Had problems running repo on a system with Python 2.7
	Use the command:
	```sh
	python3 /home/cie/bin/repo ...
	python3 /home/cie/bin/repo init ...
	```
 
	Instead of:
	```sh
	repo init ...
	```

2. Repo sync is failing<br>
	repo sync ran successfully until 93% completion.<br>

	Following errors occured thereafter:<br>
 	The complete error log can be inspected here: [repo_sync_error_log.txt](repo_sync_error_log.txt)<br>

	![image description](Screenshot%20from%202024-01-29%2015-49-30.png)
	![image description](Screenshot%20from%202024-01-29%2015-49-40.png)

### Outcomes & Learnings:
1. Decided to temporary halt development on Raspberry Pi 4:
	- Shifted focus from Raspberry Pi to host machine due to persistent challenges in Pi development
	- Continuous errors and bugs hindered progress on Pi platform
	- Lack of comprehensive documentation made issue resolution difficult
	- Opted for host machine development for stability and better documentation
	- Strategic move enables gaining insights and refining development workflows
	- Establishing solid foundation on host machine for smoother transition to future hardware
	- Plan to leverage experience for enhanced capabilities and smoother transition to Raspberry Pi 5

2. Moved onto using Host System for building. Host system has specifications:
	- Intel® Core™ i7-12800HX Processor
	- 32GB RAM
	- 1TB SSD

## Week 2: 
- Got the latest Canary version of Android Studio setup and running on the Ubuntu host machine
- Made attempts to get automotive emulator running on the most machine using:
	- Snapp Automotive
 	- Volvo Build
  	- Polestar Build
  	- Regular build
- Finally got automotive emulator running with regular Android Automotive OS (ie. without Snapp Automotive or Volvo Build)
- Built a simple interactive application
- Started ideating on application ideas that test core features of IVI like:
	- Camera integration
	- Voice interaction
 	- Navigation
  	- Text interaction
  	- Some level of autonomous driving ability

### Highlights:
1. Attmepted to get automotive emulator running using Snapp Automotive (UNSUCCESSFUL):
	Used the following guide: [SnappAutomotive README](https://github.com/snappautomotive/README)<br>

	Encountered the following error:<br>
		![image](https://github.com/ShreevathsaGP/CIE-IVI/assets/59483990/74484be5-ad88-4cc8-ad2c-2bafc645f12e)<br>
		Emulator did not get past this booting stage even after several attempts and repeated tinkering with settings.<br>

  	Decided to move on from Snapp Automotive to Volvo and Polestar SDK's, due to:<br>
   		- The error mentioned above
   		- Snapp Automotive would restrict our development
   		- Regular build's are more upto date and can be troubleshooted better

2. Attempted to get automotive emulator running using Polestar and Volvo (UNSUCCESSFUL):
	Explored the following SDK update sites:<br>
	- [Volvo System Images](https://developer.volvocars.com/sdk/volvo-sys-img.xml)
 	- [Polestar System Images](https://developer.polestar.com/sdk/polestar2-sys-img.xml)
	

4. Got automotive emulator working using regular build (SUCCESSFUL):
	Used the following guide: [AAOS Hello World: How to Build Your First App for Android Automotive OS](https://grapeup.com/blog/how-to-build-your-first-app-for-android-automotive-os/)<br>

	Learnt about and explored [androidx car package](https://developer.android.com/reference/androidx/car/app/package-summary)<br>

 	Finally got the automotive emulator running on host machine:
	
	   
