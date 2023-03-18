# 1344. Angle Between Hands of a Clock

Given two numbers, hour and minutes, return the smaller angle (in degrees) formed between the hour and the minute hand.

Answers within 10-5 of the actual value will be accepted as correct.

 
**Example 1:**

<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_1_1673.png" alt="mypic" style="width:200px; height:200px"/>

```
Input: hour = 12, minutes = 30
Output: 165
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_2_1673.png" alt="mypic" style="width:200px; height:200px"/>

```
Input: hour = 3, minutes = 30
Output: 75
```
**Example 3:**

<img src="https://assets.leetcode.com/uploads/2019/12/26/sample_3_1673.png" alt="mypic" style="width:200px; height:200px"/>

```
Input: hour = 3, minutes = 15
Output: 7.5
```
 
**Constraints:**

* `1 <= hour <= 12`
* `0 <= minutes <= 59`

**Solution:**
```
class Solution {
    public double angleClock(int hour, int minutes) {
        //this will give us the value of hour in form of degrees
        float h = ((hour%12) + (float) minutes/60)*30; //360/12

        //to change minutes to degree
        float m = (minutes*6); //360/60

        //the total angle formed = degrees of hour hand - degrees of minute hand 
        float angle = Math.abs(h - m);

        if(angle > 180) {
            angle = 360 - angle;
        }

        return angle;
    }
}
```
