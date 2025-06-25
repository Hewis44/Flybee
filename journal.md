---
Title: "A Fixed Wing Aircraft"
Author: "Hewis44"
Description: "UAV"
created_at: "2025-06-19"
Total time spent: 45 Hours
---

## Day 1, 13th JUNE – Design, Modelling & Initial CFD , Research ( 15 HOURS)


So yeah, this whole thing started with a simple idea — to make a cool fixed-wing plane that can lift good weight but still be light and easy to carry. I wanted something that works well, flies smooth, and isn’t a pain to assemble. Once I had the goal in mind, I just jumped into it step by step planning the design, picking the parts, and figuring out how to actually build it all.




This day I decided not to build or test anything physical but to just understand the complete workflow properly and write it down for my repo. Like, how to take a CAD model, prepare it for CFD, do meshing, set flow boundary, and analyze results. I followed some tutorials online and also messed up a couple of times in SimScale but slowly got the hang of it. Exporting the model from Onshape, importing to SimScale, setting airspeed, and all that felt like a long process at first, but after 2–3 tries it started making sense. I got better at understanding what those pressure plots actually mean and how to read drag and lift values properly. I also explored how stall angle changes with airfoil shape and wing loading. It was a lot of learning, like real nerd stuff, but now I feel much more confident about how CFD works and how I can trust the values I’m getting. I’m gonna add a proper tutorial markdown in my repo too later so that anyone else can learn from it without going through all this confusion.




![image](https://github.com/user-attachments/assets/cb4e9a28-a517-455f-a758-8aead2b5cbb3)


BANG BANG BANG


***Honestly Evryone Should try this***

At the beginning of this whole fixed-wing project, I had literally no clue how to use CAD or CFD tools properly. Like I had seen people using stuff like SolidWorks or Fusion 360, but my laptop wasn’t that powerful, so I didn’t want to install anything heavy. That’s when I found Onshape, and bro it was honestly a game-changer. It runs fully in the browser, so I didn’t even need to worry about lag or anything. I used it to make every single part of the plane — the fuselage, the wing structure, the tail, everything. It was clean and pretty simple to understand once you get used to the interface. For learning how to do all that properly, I followed tutorials from YouTube channels like CAD CAM Tutorials, Joko Engineeringhelp, and Product Design Online. They explained small things like how to use constraints properly, how to mirror sketches, and how to do fillets and assemblies. I literally used to keep one side of my screen for YouTube and the other side for Onshape and copy whatever they were doing until I got my design working. Joko’s channel helped me understand how to model symmetric parts and wings, especially how to make proper parametric sketches so I could edit later easily.

Follow this playlist For learning ansys:https://youtube.com/playlist?list=PLykANdmho34xuMaku22umA1xP6vidDfIN&si=9iTnEPpwRTiwWmO0




Then came the CFD part, and man, it was a different level. I decided to use ANSYS Fluent for the simulations because it gives very detailed results, and I wanted to check lift and drag values accurately. But ANSYS looked very pro-level in the beginning, and it took me a full day just to understand what a boundary condition is. I started slow by watching videos on channels like LearnCAx, CAx Tutorials, and SimuTech Group. These channels go step-by-step, like first they show how to import geometry (I exported my wing as a STEP file from Onshape), then how to clean up the model in ANSYS SpaceClaim, and then how to create mesh, apply freestream conditions, and finally simulate. At first I was just copying whatever they were doing, but after a while I started understanding why they were using k-omega SST model and how the mesh refinement near the surface actually affects the boundary layer results. One of the most useful parts was learning how to run an AoA sweep and see how the lift changes at each angle. That’s how I confirmed that GOE225 airfoil was giving more lift and better stall behaviour than others I tested. Also learned how to generate those nice colorful contour plots showing pressure and velocity lines. The simulation part honestly felt very satisfying when I saw the air flow properly over my wing, and no weird flow separations. If I had not followed those YouTube tutorials, especially from LearnCAx and SimuTech Group, I don’t think I could’ve figured it out on my own. So yeah, a big chunk of this project was basically me learning from YouTube and then applying it directly to my own design. Pure desi jugaad style learning, but it worked.


These were my learnings and some flaws,mistakes i did while modelling this plane:


![IMG-20250307-WA0043](https://github.com/user-attachments/assets/b3c95c86-7bfa-42f8-82f5-1e99955f22a4)



The first image (the one with the circular patterns) shows the pressure field with vector lines from the front view. I used this to understand how the flow gets disturbed around the wing tips and how pressure behaves symmetrically across both wings. You can see those big swirling circles — those are basically vortices forming at the tips due to pressure difference from top and bottom of the wing. This was expected, but I was surprised how clean and uniform the pressure distribution was in the mid-section. That gave me confidence that the design isn’t creating sudden turbulence or separation zones in the middle part of the wing.



Watched this video for understanding laminar Flow:
![image](https://github.com/user-attachments/assets/b9d130a0-e586-4e42-8b31-87f30e2ad686)







![IMG-20250307-WA0044](https://github.com/user-attachments/assets/c9c49a54-e6ae-43d6-91f5-068c6427b0a0)



![IMG-20250307-WA0042](https://github.com/user-attachments/assets/b3737c52-c347-479e-a9f1-6ba34ac5a746)


these are velocity streamlines over a side cut of the aircraft. Here I used a velocity inlet of 21.59 m/s and watched how air behaves over the GOE225 airfoil plus the fuselage. This result helped me see how the air smoothly accelerates over the curved upper surface of the wing and slows down below, which is exactly what creates lift. The greenish-blue area above the wing means higher velocity (low pressure), and the lower part has lower velocity (high pressure). One mistake I made here was not refining the mesh properly near the surface in my first try, because the results were looking very patchy. Then I increased the inflation layers and refined the near-wall mesh, and finally I got this smooth output. Also, in the third image which is a full-body side view, you can clearly see the velocity gradients around the whole aircraft — especially how the air slows near the tail. That’s something I didn’t consider during early design, so I’ll maybe lift the tail a bit upward in next revision to avoid airflow hitting directly.



![IMG-20250307-WA0039](https://github.com/user-attachments/assets/7f659497-22bc-41d1-bb56-08e308d884e8)



![IMG-20250307-WA0040](https://github.com/user-attachments/assets/275880bd-001b-4294-a2d0-e85b6ed8e1dc)


 the wing section with GOE225 airfoil that I modelled in Onshape. I used a proper spline-based profile and projected it across multiple ribs. Initially, I tried drawing it manually but the accuracy was off. Then I learned to use coordinates from airfoiltools.com and import those into Onshape sketch, and it made a big difference. This helped make a smooth, realistic wing and not just some random rounded shape.

Then the next image shows a close-up pressure contour at wing-root — basically how the pressure is behaving where the wing joins the fuselage. I saw a strong red spot here which might indicate stress point or potential for structural fatigue, so I might reinforce this joint using carbon rods or laser-cut ply parts. This insight would’ve been missed if I didn’t simulate it properly.the last image is another pressure side view, showing again how pressure drops sharply above the wing and rises below it. Even though it looks very colourful, interpreting this helped me understand how smoothly GOE225 behaves at 4° angle of attack without sudden stall or flow separation.

Overall, this CFD phase taught me so much. From learning how to clean geometry, fix mesh errors, apply correct physics models like k-omega SST, and properly interpret the force outputs — every part was something new. I made many silly mistakes at first like assigning wrong inlet speed, forgetting to use symmetry plane, not applying inflation layers, etc. But by doing trial and error and watching those tutorials side by side, I slowly made my way. It’s honestly one of the most satisfying parts of this whole UAV build. Seeing the virtual airflow over a design you made yourself is such a good feeling. It made me realise how powerful CFD is, and now I’m even thinking of trying transient simulations and maybe propeller analysis next.


### 15 JUNE: Planning the Design & Frame Style   ( TOOK WHOLE ETRNITY)-15-20 HOURS


I started by scribbling a basic sketch of the UAV, mainly to fix what mattered most — modularity, lift, and weight balance. I knew from the start I wanted a high-wing design because it’s naturally more stable and gives better visibility for autopilot. I went for a tractor propeller setup, so airflow over the wing is smooth and undisturbed, especially important during takeoff. I began modelling the fuselage in Onshape — just a simple boxy design first, then slowly refined it to match internal space needs and weight distribution.
![Fuselage CAD](https://github.com/user-attachments/assets/5bae02b1-cc2a-44e4-8133-6d79855d9084)
![Fuselage Screenshot](https://github.com/user-attachments/assets/729b0380-42bd-4b34-8b42-575f8dbd0a40)

Once the fuselage looked okay, I shifted focus to the wing design. I kept it rectangular for ease of construction and better roll stability — the span I chose was 1250 mm and chord 250 mm, which gave decent wing area for the expected weight class. For the airfoil, I tested three options: GOE225, S1223, and NACA4412. I compared their Cl/Cd ratio, stall angle, and thickness. GOE225 performed best overall, especially in moderate Reynolds numbers — gave higher lift with manageable drag.

![Airfoil Plots](https://github.com/user-attachments/assets/1c8f1cb4-a696-4966-baf2-9564db4b7d6c)
![Comparisons](https://github.com/user-attachments/assets/8b23e1f0-a2b2-4cf2-be4e-a2f05a0338f4)

I then modelled the GOE225-based wing on Onshape, adding ribs, spars, and servo slots. I paid extra attention to internal structure for strength without adding too much weight. Ailerons were also added using simple hinges. After assembling everything virtually, I created a solid version of the wing for CFD. This would help me simulate lift and airflow properly before committing to a real build. This whole phase gave me a much clearer idea of what my aircraft will behave like in flight.

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
