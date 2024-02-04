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
  	- Without pre-built images
- Despite the initial setback, we successfully upgraded the Python version, ultimately enabling the 'repo sync' command to function seamlessly. 


Refer the link Github link below:

```sh
https://github.com/snappautomotive/README
```
 
