# Building applications for IVI systems using Android Automotive OS  
`Done under CIE (PES University)`

## Week 1 : 
- The host machine, crucial for our development environment, was equipped with Python 2.7, rendering the 'repo sync' command ineffective.
- Faced with this obstacle, our team delved into the documentation to identify a solution. After thorough research and collaboration, we pinpointed the necessity to update the Python version to 3.8. 
- Despite the initial setback, we successfully upgraded the Python version, ultimately enabling the 'repo sync' command to function seamlessly. 

### Highlights:
1. Had problems running repo on a system with Python 2.7<br>
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
1. Attmpted to get automotive emulator running using Snapp Automotive (UNSUCCESSFUL):
	Used the following guide: [SnappAutomotive README](https://github.com/snappautomotive/README)<br>

	Encountered the following error:<br>
		Emulator did not get past booting stage even after several attempts and repeated tinkering with settings.<br>
   		![image](https://github.com/ShreevathsaGP/CIE-IVI/assets/59483990/82f939ee-0ce5-4872-b9ac-db2459b8227f)<br>
   		
  	Decided to move on from Snapp Automotive to Volvo and Polestar SDK's, due to: <br>
	- The error mentioned above
	- Snapp Automotive would restrict our development
	- Regular build's are more upto date and can be troubleshooted better

3. Attempted to get automotive emulator running using Polestar and Volvo (UNSUCCESSFUL):<br>
	Explored the following SDK update sites:<br>
	- [Volvo System Images](https://developer.volvocars.com/sdk/volvo-sys-img.xml)
 	- [Polestar System Images](https://developer.polestar.com/sdk/polestar2-sys-img.xml)

	Encountered the following problems with Volvo Image:<br>
	- System Image did not load
 	- AVD had did not run 	
 	
	
 	Encountered the following problems with Polestar Image:<br>
	- AVD did not run

   ### Decided to move onto regular build.<br>
   	When initially Andorid Automotive was used and when either *"NO ACTIVITY"* or *"MEDIA"* was selected in the activity window, only the
   	Tablet with Android OS used to load and not the Android Automotive OS
   	![image](https://github.com/ShreevathsaGP/CIE-IVI/assets/40132560/c105b507-358b-45d5-81c7-c506618e0929)

	Hence Concluded that using a regular AAOS build with custom programs is a better option.

5. Got automotive emulator working using regular build (SUCCESSFUL):<br>
	Used the following guide: [AAOS Hello World: How to Build Your First App for Android Automotive OS](https://grapeup.com/blog/how-to-build-your-first-app-for-android-automotive-os/)<br>

	Learnt about and explored [androidx car package](https://developer.android.com/reference/androidx/car/app/package-summary)<br>

 	Finally got the automotive emulator running on host machine:<br>
	![android_emulator_showcase](https://github.com/ShreevathsaGP/CIE-IVI/assets/59483990/e96e3180-2a89-4c90-9bcd-748e4f5358cd)
		
6. Built a sample interactive application for AAOS:<br>
	Used the following guide: [AAOS Hello World: How to Build Your First App for Android Automotive OS](https://grapeup.com/blog/how-to-build-your-first-app-for-android-automotive-os/)<br>

 	Had to heavily reconfigure build.gradle and AndroidManifest due to above tutorial being outdated<br>

 	Implemented following Java Classes:
	```java
 	public class GrapeAppScreen extends Screen {

	    public GrapeAppScreen(@NonNull CarContext carContext) {
	        super(carContext);
	    }
	
	    @NonNull; @Override
	    public Template onGetTemplate() {
	        Row row = new Row.Builder().setTitle("Greetings from CIE - IVI!!").build();
	        Action action = new Action.Builder().setOnClickListener(() -> CarToast.makeText(getCarContext(), "Hello!", CarToast.LENGTH_SHORT).show()).setTitle("Say Hi!").build();
	        ActionStrip actionStrip = new ActionStrip.Builder().addAction(action).build();
	        return new PaneTemplate.Builder(new Pane.Builder().addRow(row).build()).setActionStrip(actionStrip).setHeaderAction(Action.APP_ICON).build();
	    }
	}
 	```
 	```java
	public class GrapeAppService extends CarAppService {
	    public GrapeAppService() {}
	    @NonNull; @Override
	    public HostValidator createHostValidator() {
	        return HostValidator.ALLOW_ALL_HOSTS_VALIDATOR;
	    }
	    @NonNull; @Override
	    public Session onCreateSession() {
	        return new Session() {
	            @Override; @NonNull
	            public Screen onCreateScreen(@Nullable Intent intent) { return new GrapeAppScreen(getCarContext()); }
	        };
	    }
	}
  	```

   	Completed the application that:<br>
   	- Starts interaction with a message
   	- Continues interaction when clicking on "Say Hi!" button

	![Screenshot 2024-02-04 at 1 17 45 PM](https://github.com/ShreevathsaGP/CIE-IVI/assets/59483990/1e7504af-6b64-44c9-bcee-84606c6432ae)<br>

### Outcomes & Learnings:
UPDATE THIS!



## Week n : 
- Agenda:-

	-Try making arrangements of installing PuTTY for RasPI to get the error log file and make the required changes in the build <br>
	-Media playback through USB should be readable<br>
	-Bluetooth call connectivity to be looked into

- Work Done:-
  	
   	- Installed ADB on my development machine (MACBOOK).
  	-  ```brew install --cask android-platform-tools```.
  	-  Connected the Target device to Wifi and got the IP Address using the settings menu.
  	- Used ``` adb connect <ip_address of the target device> ``` to connect to Pi.
  	-  <img width="492" alt="image" src="https://github.com/ShreevathsaGP/CIE-IVI/assets/40132560/9e5a2cab-b5da-4892-9dee-df4ec9b0acd5">
   	- Used ``` adb bugreport ``` to create a bug report.
   	- Used Logcat to get the Log Output of the device live.
   	- Stored the logcat output in a textfile called logcat.txt
   	- ![image](https://github.com/ShreevathsaGP/CIE-IVI/assets/40132560/64507351-0286-48d3-afb1-e49a6679cb8f)
   	- ^ is the output of logcat in terminal
   	- <img width="1512" alt="image" src="https://github.com/ShreevathsaGP/CIE-IVI/assets/40132560/caf44513-8019-4749-8701-9798b2c4d72e">
    	- output stored in a textfile.

- Observations:-
  	- Phone Contacts getting synced slowly, exact reason for the slow sync - yet to figure out.
  	- TEXT messages recieved by the phone is displayed while it is connected to the pi via bt.
  	- Possible reasons for the failure of calling - USB Mic/Speaker setup needed.
  	- Phone when connected to pi via USB, gets scanned and read, but device instantly crashes when accessing files in pi.
  	- Target recognising USB as an audio device -- need to debug.
    


   


