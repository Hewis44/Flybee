---
title: "A Fixed Wing aircraft"
author: "Hewis44"
description: "UAV"
created_at: "2025-06-19"
Total time spent: 
---
## June 16  ~ 4 hours
So yeah, this whole thing started with a simple idea  to make a cool fixed-wing plane that can lift good weight but still be light and easy to carry. I wanted something that works well, flies smooth, and isn’t a pain to assemble. Once I had the goal in mind, I just jumped into it step by step planning the design, picking the parts, and figuring out how to actually build it all.

Step 1: Planning the Design & Frame Style

I started with a rough sketch on paper to imagine what the whole aircraft would look like. I listed down my top priorities: stability, good payload, easy to carry, and strong enough to fly multiple times without breaking. The frame would need to be modular and compact, but it still had to handle a decent amount of weight. That’s why I chose a high-wing configuration — it gives natural stability due to the pendulum effect, which makes the plane settle back to level flight without needing too much correction.

I compared different motor positions — pusher vs tractor — and chose tractor. Why? Because placing the propeller at the front gives smoother airflow over the rest of the plane. It also helps reduce vibrations and makes cooling easier for the motor. It’s also easier to mount it securely on the front.

SO i started designing the Fuselage
![image](https://github.com/user-attachments/assets/5bae02b1-cc2a-44e4-8133-6d79855d9084)
![image](https://github.com/user-attachments/assets/729b0380-42bd-4b34-8b42-575f8dbd0a40)
The fuslage almost worked as expected
Now wing:
For the wing planform, I went with rectangular. It’s not the most aerodynamic but it’s simple to manufacture and super predictable in flight. Also, cutting rectangular shapes from balsa is much easier and gives consistent results. The wing size was chosen to be 1250 mm span with 250 mm chord, giving a good enough wing area to generate the lift we need.
This was one of the most critical parts. I picked three airfoils to study: GOE225, S1223, and NACA4412. I ran comparative plots for lift coefficient (Cl), drag coefficient (Cd), and lift-to-drag ratio (L/D). I also compared stall behavior and sensitivity to turbulence.
![image](https://github.com/user-attachments/assets/1c8f1cb4-a696-4966-baf2-9564db4b7d6c)
![image](https://github.com/user-attachments/assets/8b23e1f0-a2b2-4cf2-be4e-a2f05a0338f4)

GOE225 was the final choice because it gave the best mix of high lift, lower drag, and gradual stall characteristics. It has a 7.6% camber at 40% chord, which is good for high lift. It’s also easier to fabricate compared to S1223, which has a more fragile trailing edge. With GOE225, I got lift values up to 37.26 N in the full body CFD at 4 degrees AoA, which is more than enough to lift the 2 kg payload and rest of the plane.

![image](https://github.com/user-attachments/assets/e0b917cf-3697-41c9-8dde-3b15ccf0d585)
![image](https://github.com/user-attachments/assets/2db8c3ca-ed08-4084-a509-3fc16c605354)
![image](https://github.com/user-attachments/assets/b5d69539-8f3e-4ccb-85fa-849b2d1ce2b8)


Now That i know GOE225 is the best wing design i started modelling it


![image](https://github.com/user-attachments/assets/89856658-af8e-43d7-b7a6-b5f17453f8a8)

![image](https://github.com/user-attachments/assets/c33ed9e1-377c-4e16-99b3-99e03df74136)


This is the assembled wing:
![image](https://github.com/user-attachments/assets/d7f7170b-0eef-4ba6-9ded-cecd61ae6b9b)

These are the spars to assemble the wing:
![image](https://github.com/user-attachments/assets/3208263f-8a2f-4060-a461-cb59042ce33f)

I made a solid one for cfd

![image](https://github.com/user-attachments/assets/090b1432-67fe-41db-b690-b77b26cf707b)

Now That we r done with wing and Fuselage , I started designing the tail
The V-tail was created using two tail surfaces set at a calculated angle of 110 degrees. The surface area was 70% of what a normal tail would have, which saves weight. I added hinges and servo mount slots, making sure the pushrods would line up without too much angle to avoid friction.

![image](https://github.com/user-attachments/assets/83de1561-285c-4204-908f-47ea7918f57d)

I made a solid one for cfd too


![image](https://github.com/user-attachments/assets/9ad913cc-3cf6-4f16-a524-fd5dca456465)












