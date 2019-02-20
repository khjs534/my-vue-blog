---
slug: safebox-post
title: "Safebox: Experiments in IoT"
date: 2019-02-11 15:48 UTC
image: "./images/safebox.jpg"
---
## Safebox

In December of 2016 I was coming close to graduating from Dev Bootcamp and needed to pitch a final project to create with a few of my cohorts. The media in Chicago at the time was feverishly reporting on package theft due to the holiday season picking up. For my final project in Dev Bootcamp I wanted to incorporate parts of my electrical engineering background with what i had learned in DBC. I came up with an idea to create a proof of concept box that would be put on your porch or in the a mail room that would allow the user to control the opening and closing of this box. I pitched the idea and as a result became team lead for my project.

### Intended Goal
* Build an interfacing device that could allow a user to open and close a box from a mobile device.
* Have the box notify the user when the box was locked by someone delivering a package or an approved user

### Approach

With many hardware based research and design it is beneficial to be flexible. I divided team work into 3 initial R&D sections. 2 people would research hardware and see which platform would fit our needs better. A third person would research how to create a local server on the platform and what services we would use to communicate with the user.

We originally thought of using an Arduino Yun that was also came with a light linux shell that ran in parallel with arduino, but the the linux shell approved to be too light weight for our needs. The arduino was our original plan for this project because we had seen [another project](https://www.twilio.com/blog/2016/07/how-to-teach-your-dog-to-text-selfies.html) that was very successful interfacing between the device and user. Once this teammate found that this device could no longer be used for our project they began looking to figuring out interfacing options. What kind of hardware would we need for a person to physically interface with the device.

I looked into using the Raspberry Pi. It had a more versatile version of linux runnning and many more options for us in terms of hardware I/O that we could use and integrate into the final project. Additionally they are very commercially available and seemed like the best option as the Arduino had run dry.

For our software options we had found that we would need to use ngrok to start a local server and as a start we wanted to use Twilio to send and receive SMS to control the device.

### Conclusion

For more information you can find the repo [here](https://github.com/khjs534/safebox)

