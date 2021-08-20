# SLAM_Map

<div dir="rtl">

**خطوات عمل خريطة لمجال تحرك الروبوت باستخدام TurtleBot3 على طريقة SLAM.**

 **تم تجربة المشروع على نظام ubuntu 18.04 بداخل Virtualbox على نظام ويندوز.**
  
 **لابد من التأكد من تثبيت البايثون ونظام ROS و وجود مساحة عمل catkin قبل البدء بالخطوات التالية.**
  
  **في هذا المشروع عملت على نسخة Melodic.**
  
  
 **الخطوة الأولى: تهيئة بيئة العمل**

1-1
_تحميل الحزم اللازمة على نظام ROS._

  ![1-first](https://user-images.githubusercontent.com/55546717/130168116-44159582-9f18-488a-a6ca-c05c743db957.PNG)

1-2
_تحميل حزم TurtleBot3_

  `$ sudo apt-get install ros-melodic-dynamixel-sdk`
  
`$ sudo apt-get install ros-melodic-turtlebot3-msgs`
  
`$ sudo apt-get install ros-melodic-turtlebot3`

1-3
_ضبط اسم النموذج الافتراضي لروبوت TurtleBot3_

لاختيار Burger `$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc`
  
Waffle Pi أو `$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc`


**الخطوة الثانية: تجربة المحاكاة على برنامج Gazebo**

2-1
_تحميل الحزم اللازمة من Github على catkin_

`$ cd ~/catkin_ws/src/`
  
`$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`
  
`$ cd ~/catkin_ws && catkin_make`

2-2
_أولًا نختار نوع الروبوت_

`$ export TURTLEBOT3_MODEL=burger`

أو `$ export TURTLEBOT3_MODEL=waffle`

أو `$ export TURTLEBOT3_MODEL=waffle_pi`

_ثم اختيار نموذج التشغيل من أحد الخيارات التالية:_

_تشغيل Burger on Empty World_

`$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch`

*يمكن تشغيل نموذج واحد للمحاكاة في كل مرة

_تشغيل Waffle on TurtleBot3 world_

`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

_تشغيل Waffle Pi on TurtleBot3 House_

`$ roslaunch turtlebot3_gazebo turtlebot3_house.launch`

2-3
_للتحكم بالروبوت تعمل الأمر التالي في Terminal جديد_

`$ export TURTLEBOT3_MODEL=waffle`

`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`

*للتحكم بأي روبوت آخر فقط قم بتغيير اسم النموذج -burger or waffle or waffle_pi- الذي اخترته للتشغيل على المحاكي


**الخطوة الثالثة: عمل خريطة بطريقة SLAM وحفظها**

3-1
_لعمل الخريطة نقوم بعملية تشغيل المحاكاة من الخطوة السابقة 2-2 باختيار أي روبوت._

*يمكن عمل الخريطة على TurtleBot3 World or TurtleBot3 House فقط.

3-2
_تشغيل SLAM في Terminal جديد_

`$ export TURTLEBOT3_MODEL=burger`

`$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`

*اختر ذات نموذج الروبوت المستخدم لتشغيل المحاكي -burger or waffle or waffle_pi-.

3-3
_في Terminal 2-3 جديد نستخدم أمر تحريك الروبوت من الخطوة السابقة_

3-4
_حفظ الخريطة بعد الإنتهاء_

`$ rosrun map_server map_saver -f ~/map`


**المراجع المستخدمة:**

- TurtleBot3 e-manual
  
https://robots.ros.org/

- 
</div>
