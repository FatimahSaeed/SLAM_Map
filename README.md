# SLAM_Map

<div dir="rtl">

**Turtlebot3 على طريقة SLAM. خطوات عمل خريطة لمجال تحرك الروبوت وحفظها باستخدام**

 **تم تجربة المشروع على نظام ubuntu 18.04 بداخل Virtualbox على نظام ويندوز.**
  
 **لابد من التأكد من تثبيت البايثون ونظام ROS و وجود مساحة عمل catkin قبل البدء بالخطوات التالية.**
  
  **في هذا المشروع عملت على نسخة Melodic.**
  
  
 **الخطوة الأولى: تهيئة بيئة العمل**

_تحميل الحزم اللازمة على نظام ROS._

  ![1-first](https://user-images.githubusercontent.com/55546717/130168116-44159582-9f18-488a-a6ca-c05c743db957.PNG)

_تحميل حزم TurtleBot3_

 `$ sudo apt-get install ros-melodic-dynamixel-sdk`
 
`$ sudo apt-get install ros-melodic-turtlebot3-msgs`
 
`$ sudo apt-get install ros-melodic-turtlebot3`

_ضبط اسم النموذج الافتراضي لروبوت TurtleBot3_

لاختيار Burger `$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc`
 
Waffle Pi أو `$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc`


**الخطوة الثانية: تجربة المحاكاة على برنامج Gazebo**

_تحميل الحزم اللازمة من Github على catkin_

`$ cd ~/catkin_ws/src/`
 
`$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`
 
`$ cd ~/catkin_ws && catkin_make`

ملاحظة: يمكنك تشغيل أي روبوت على أي نموذج للمحاكاة فقط قم بتغيير اسم الروبوت

_تشغيل Burger on Empty World_

`$ export TURTLEBOT3_MODEL=burger`
 
`$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch`

ملاحظة: يمكن تشغيل نموذج واحد للمحاكاة في كل مرة

_تشغيل Waffle on TurtleBot3 world_

`$ export TURTLEBOT3_MODEL=waffle`
 
`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

_تشغيل Waffle Pi on TurtleBot3 House_

`$ export TURTLEBOT3_MODEL=waffle_pi`
 
`$ roslaunch turtlebot3_gazebo turtlebot3_house.launch`

_للتحكم بالروبوت تعمل الأمر التالي في Terminal جديد_

`$ export TURTLEBOT3_MODEL=waffle`
 
`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`

ملاحظة: للتحكم بأي روبوت آخر فقط قم بتغيير اسم النموذج الذي اخترته للتشغيل على المحاكي


**الخطوة الثالثة: عمل خريطة وحفظها**
</div>
