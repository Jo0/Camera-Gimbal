# Camera Gimbal

## Background

In 2014 I wanted to a camera gimbal. At the time, many great offerings were too expensive (~$500-700) and cheaper products had questionable quality and performance.

I took it upon myself to see if I could design and create my own. My girlfriend's dad (now father in law) is a machinist and was allowed to work on personal projects when off hours. Having no experience with using CAD software I was given access to a machine with SolidWorks and spent a week or so designing the various parts you see here in this repository.

## Materials

- 6061T6 Aluminium Sheet .190" thick
- 6061T6 Aluminium Sheet .750" diameter .125" thick wall
- 3 x Turnigy HD 5208 Brushless Gimbal Motor
- Turnigy 2200mAh 3S 25C Lipo Pack
- EvvGC 1.3 Gimbal Controller Board with IMU (Inertial Measurement Unit)
  
## Electronics and Software

- EvvGC 1.3 Gimbal Controller Board with IMU (Inertial Measurement Unit)
- [EvvGC Firmware](https://github.com/Jo0/Firmware)
- [EvvGC Electronics](https://github.com/Jo0/Hardware)

## Outcome And Lessons Learned

- Images: 
  - [In this repository](https://github.com/Jo0/Camera-Gimbal/tree/master/Images)
  - [Machined parts and Assembly](https://imgur.com/a/h3jFl?)
  - [Renders](https://imgur.com/a/bzajgdB)
- Videos:
  - [YouTube Playlist Of Test Runs](https://www.youtube.com/playlist?list=PLFWRZ1I7BiI8qetZ2vBfIBI2kLMp9aT8P)
  
### 1. Picking up CAD is faily easy. Creating a good design is difficult

I didn't have a feedback loop of creating a design and prototyping it before finalizing the design. I pretty much relied on intuition (common sense), referencing other designs found online, the simulation of the assembled parts in SolidWorks, and eventually a final review with my father in law before finally machining the parts.

Although my design worked. I feel like I could've gotten a better result if I were able to actually have prototypes of each design iteration before "completing the project".

### 2. CNC Machining is not a magical and easy process

CNC Machining is not a process where you drop a material into a machine, press a button, and your part magically appears.

There's still quite a bit of human intervention in the process.
  - Understanding of materials and their use cases. 
  - Feasibility of the creation of the part(s) based on the design and the machining process(steps) that is necessary to achieve the end result.
  - Programming of the processes(steps) needed to create the part(s)
  - Precision of material and machine setup process

### 3. It's hard to keep costs down and produce a good result

One of the primary goals of the project was to keep costs down. I think I ended up spending ~$225 total to create the gimbal. The cost would've been significantly higher if I had to pay for a machinist to machine my part. Due to machine time and time spent programming the operations to create the parts.

I was able to cut costs on materials by
  - Not having multiple prototypes and only machining when the design was "finalized"
  - Not picking a more established gimbal controller
    - I chose the EvvGC gimbal controller due to the cost of the electronics (~$45) and that it was opensource
    - The other gimbal controller available at the time was the [AlexMos SimpleBGC Controller](https://shop.basecamelectronics.com/) ($150) and the various clone boards available at the time ($50)
      - I didn't want to take a chance on the clone boards due to reports on questionable compatibility on the software to interface with the controller at the time

### 4. There's more to a gimbal than just a frame, brushless motors, and a controller

Although I wanted the gimbal to magically stabilize my camera upon initial setup, I quickly found that there is more configuration to be done to get everything working perfectly.

1. Your gimbal must be balanced, to a reasonable degree, even when it's powered off for it to perform at a reasonable level.
   - While the controller can compensate for everything, it's better to think about the gimbal setup and the controller as an aid to the operator rather than a tool to compensate for the imbalance and instability of the entire system
2. Motor choice must match the load that you plan on putting on the gimbal system.
   - Luckily, I chose motors that were rated higher for the load I was putting on each axis of my gimbal. Had I had decided to choose lower rated motors to cut costs, I think I would've run into issues when mounting heavier cameras like a DSLR.
3. Motor PID tuning is delicate process
   - I may have had difficulty in this area due to the fact that I cut costs and chose an open source gimbal controller. I had a lot of trial and error when tuning the PID settings for the controller to properly control the rates at which the motors compensated for the movement across axes.