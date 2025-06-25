---
Title: "A Fixed Wing Aircraft"
Author: "Hewis44"
Description: "UAV"
created_at: "2025-06-19"
Total time spent: 45 Hours
---

## Day 1 – Design, Modelling & Initial CFD , Research

So yeah, this whole thing started with a simple idea — to make a cool fixed-wing plane that can lift good weight but still be light and easy to carry. I wanted something that works well, flies smooth, and isn’t a pain to assemble. Once I had the goal in mind, I just jumped into it step by step planning the design, picking the parts, and figuring out how to actually build it all.




This day I decided not to build or test anything physical but to just understand the complete workflow properly and write it down for my repo. Like, how to take a CAD model, prepare it for CFD, do meshing, set flow boundary, and analyze results. I followed some tutorials online and also messed up a couple of times in SimScale but slowly got the hang of it. Exporting the model from Onshape, importing to SimScale, setting airspeed, and all that felt like a long process at first, but after 2–3 tries it started making sense. I got better at understanding what those pressure plots actually mean and how to read drag and lift values properly. I also explored how stall angle changes with airfoil shape and wing loading. It was a lot of learning, like real nerd stuff, but now I feel much more confident about how CFD works and how I can trust the values I’m getting. I’m gonna add a proper tutorial markdown in my repo too later so that anyone else can learn from it without going through all this confusion.


















### Step 1: Planning the Design & Frame Style

I started with a rough sketch to lock down priorities: modularity, weight balance, lift, and simplicity. I chose a **high-wing** layout and **tractor propeller configuration** for better airflow and natural stability. Then I started modelling the **fuselage**.

![Fuselage CAD](https://github.com/user-attachments/assets/5bae02b1-cc2a-44e4-8133-6d79855d9084)
![Fuselage Screenshot](https://github.com/user-attachments/assets/729b0380-42bd-4b34-8b42-575f8dbd0a40)

The fuselage worked well in CAD, so I moved on to the **wing**. I kept it rectangular — simple to model, cut, and balance. Size: 1250mm span, 250mm chord.

I studied 3 airfoils: **GOE225**, **S1223**, and **NACA4412**. Plotted Cl/Cd, stall behaviour, etc. GOE225 gave the best performance overall.

![Airfoil Plots](https://github.com/user-attachments/assets/1c8f1cb4-a696-4966-baf2-9564db4b7d6c)
![Comparisons](https://github.com/user-attachments/assets/8b23e1f0-a2b2-4cf2-be4e-a2f05a0338f4)

Then I started modelling the **GOE225 wing**:

![GOE225 Modelling](https://github.com/user-attachments/assets/89856658-af8e-43d7-b7a6-b5f17453f8a8)
![GOE225 Build](https://github.com/user-attachments/assets/c33ed9e1-377c-4e16-99b3-99e03df74136)

Assembled wing + internal structure:

![Wing Assembled](https://github.com/user-attachments/assets/d7f7170b-0eef-4ba6-9ded-cecd61ae6b9b)
![Spars](https://github.com/user-attachments/assets/3208263f-8a2f-4060-a461-cb59042ce33f)
![Ailerons](https://github.com/user-attachments/assets/f7a5e7ac-ce0e-44b6-8482-32931f93962b)

I made a solid version of the wing for CFD:

![Solid Wing](https://github.com/user-attachments/assets/090b1432-67fe-41db-b690-b77b26cf707b)

---

##  Day 2– Tail Design, Final CFD, and Autonomy Prep 



Today I spent time getting my wing and fuselage designs ready for laser cutting. I had to take the CAD models and then export all the ribs, spars, and other parts into DXF format. I remembered I had some leftover acrylic sheets from my old school robotics project, so I’m thinking to use those for the motor mounts and servo plates. Then I opened Fusion 360 and did a small stress simulation for fun, like just to see how much weight the wing can take. It showed that if each side handles around 20N, the spars need to be thick enough or maybe I’ll add a carbon tube in the middle just to be safe. Also tried checking how much the tail flexes under yaw movement, and it was not bad actually. I didn’t expect to enjoy this analysis part so much but once you start getting results it becomes addictive. I made a battery bay design also with a small hatch system, so I don’t have to open everything again and again. Hopefully next time I’ll start assembling the frame after I get the parts cut.









Started the day with **V-tail design**. Used two angled stabilizers at 110°, surface area was 70% of conventional H-tail to save weight.

![V-Tail CAD](https://github.com/user-attachments/assets/83de1561-285c-4204-908f-47ea7918f57d)
![V-Tail Solid](https://github.com/user-attachments/assets/9ad913cc-3cf6-4f16-a524-fd5dca456465)

Mounted **servos on tail** and aligned pushrod paths.

![Servos on Tail](https://github.com/user-attachments/assets/725007fe-c253-4ebf-ace6-f23807e630e8)

Then moved to **final assembly:**

![Full Assembly](https://github.com/user-attachments/assets/e82674e9-f814-4d14-94f0-454af5cca70f)



So today I just went all in with CFD stuff. Like, I wanted to really make sure that the airfoil I chose was actually the best, not just by reading somewhere but by seeing the actual data. I compared GOE225 with S1223 and NACA4412 again but this time I ran proper simulations using different angles of attack. I spent a lot of time learning how to set up the mesh properly, 'cause the accuracy depends a lot on that. I tried coarse mesh first but then realized results were not matching, so after trying mid and fine meshes, I figured mid was giving me a good balance of speed and detail. I also learned about turbulence models like k-omega SST and tried that. It gave pretty nice pressure and velocity plots. Honestly, seeing those color maps and streamlines felt satisfying. And finally, even after all the simulations, GOE225 still showed better performance overall, like higher lift and smoother pressure change. S1223 was good too, but it stalled quickly and the pressure difference was kind of too sharp. So yeah, this kind of confirmed that my choice was solid.











Ran **full body CFD** on wing + fuselage + tail.

![CFD 1](https://github.com/user-attachments/assets/e306804c-a240-442c-8784-0946bb24982a)
![CFD 2](https://github.com/user-attachments/assets/7af9e95d-f0b9-4a35-abd7-f7cdf57e013b)
![CFD 3](https://github.com/user-attachments/assets/3d59e1f2-b964-48e8-8485-21ce659d24e6)
![CFD 4](https://github.com/user-attachments/assets/5611e62e-dd8f-455a-9652-456b837036b2)
![Full CFD](https://github.com/user-attachments/assets/ba557577-9a38-43b3-9977-3992a43c132f)

Final observations:
- GOE225 gave **28.58 N lift** (wing-only) @ 4° AoA
- Full body gave **37.26 N lift**, **3.61 N drag**
- Smooth pressure gradient, no flow separation
- Enough lift margin to carry 2 kg payload safely

Selected GOE225 for its:
- High lift
- Gentle stall
- Low drag
- Simpler fabrication than S1223

---

### Avionics & Autonomy Setup

Started placing electronics and picking flight gear:

![Component Layout](https://github.com/user-attachments/assets/1cb3ff6d-ff6e-4196-85e7-1c82593e7d9e)

Going fully autonomous — added:
- **Pixhawk flight controller**
- **Ublox GPS module**
- **433 MHz telemetry**

Planning to flash **ArduPilot** and program waypoint missions soon. Next steps: install in frame, test with Mission Planner, and do ground test + maiden auto flight.
im gonna Add BOM,sketches and laser cutting files in the repo


## Build ( coming soon)

---
