# Frequently asked questions / problems and solutions

## AgOpenGPS

* When running, my machine position shakes even when I'm not moving
  * Check that your F9P is updated correctly [here](https://github.com/farmerbriantee/AgOpenGPS_Boards/wiki/configuring-the-zed-f9p)
  * Check that it's outputting at the right resolution/frequency (figure at the bottom showing 10 - if it's one, configure F9P properly)
![image](https://user-images.githubusercontent.com/9885921/229077593-1c1dd81e-ee2b-47f2-b111-a0b4d408b82e.png)
  * Ensure the antennas have a good view of the sky and that NTRIP is enabled and sending corrections over UDP (or serial, if using USB)
![image](https://user-images.githubusercontent.com/9885921/229078300-0fee1200-c3d6-45b3-8e89-b39428ea637f.png)
  * If using UDP, do NOT have USB connected at the same time. UDP is preferred, so disconnect all USB connections
![image](https://user-images.githubusercontent.com/9885921/229078483-6ac621df-e2bd-4975-b028-4f7299803ed9.png)


