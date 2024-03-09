\<OLD VIDS DONT LOOK, GO TO LECTURE>
- What is a safety-critical system
	- **Focus on safety**. A safety critical or life critical system is a system whose failures or malfunction may result in:
		- Death or serious injury to people
		- Loss or severe damage to equipment/property
		- Environmental harm
	- **Increasingly more computer based**
- What is a safety-critical software/program
	- Safety is the "freedom from those conditions that can cause death, injury, illness, damage to or loss of property, or environmental harm"
	- Software by itself is neither safe or unsafe, however, when its part of a system it can cause or contribute to unsafe conditions. Such software is safety critical
	- In general a safety-critical program is one in which human life depends on the correct operation of the program
	- **Safety-critical software** - Definition according to IEEE: "software whose use in a system can result in unacceptable risk. Safety-critical software includes software whose operation or failure to operate can lead to a hazardous state, software intended to recover from hazardous states, and software intended to mitigate the severity if an accident "
- What happens if something does wrong
	- Somebody dies or is injured
	- Loss of revenue
	- Product accreditation rescinded
	- Court case - who is liable
		- You are liable unless you can prove you have reduced risk on a ALARP basis (**As Low As Reasonably Possible**)
	- High cost to fix
- Software Safety Benefits
	- Software monitoring and control allows a wider range if conditions to be monitored and controlled than is possible using electro mechanical safety systems
	- Software can detect and correct safety-critical operator errors
- System dependability
	- **Most important**
	- System failures can effect a lot of people
	- ![500](Pasted%20image%2020230829181351.png)
- What makes systems safe
- What makes software safe
- How safe is safe enough
- What are the safety-critical standards
- How to produce safe software?

## Lecture


## Safety-Critical Systems
- Designing programs that work correctly and are free of bugs are desirable; but not all software have the same requirements
	- In many application programs software bugs only pose an inconvenience
	- In kernel-mode software bugs may be disastrous
	- Software that connects to a physical system may cause expensive physical damage if bugs occur
	- In some fields software bugs can put people in danger
- It is rarely possible to create software that is entirely bug free, but the frequency and likelihood can be reduced

**Definition:**
	- Safety is the "freedom from those conditions that can cause death, injury, illness, damage to or loss of property, or environmental harm"
	- Software by itself is neither safe or unsafe, however, when its part of a system it can cause or contribute to unsafe conditions. Such software is safety critical
	- In general a safety-critical program is one in which human life depends on the correct operation of the program
	- **Safety-critical software** - Definition according to IEEE: "software whose use in a system can result in unacceptable risk. Safety-critical software includes software whose operation or failure to operate can lead to a hazardous state, software intended to recover from hazardous states, and software intended to mitigate the severity if an accident "

## Safety vs Reliability
- A system can be **safe** because it cannot cause harm, and yet be **unreliable** because it does not perform its functions when they are needed.
- Eg. If your car fails to start, it is perfectly safe but unreliable
- In general, if a system can fail safe then it can be safe although unreliable if the failures occur too often

## Safety-focused software development 
- Potential safety issues can arise at any stage in the software development process
	- **Requirements gathering and planning**: wrong requirements were gathered, wrong stakeholders were contacted (didn't get an accurate idea of how to implement safety features), or the project is attempting something inherently unsafe
	- **Design:** the design inherently has high coupling and poor cohesion, which can lead to risk even if the modules are implemented perfectly. 
	- **Implementation:** poor programming practices, programming practices unsuited to the safety class of the project, overreliance on external code / software libraries / operating system code
	- **Testing:** insufficient testing, wrong category of testing for the safety class of the project
	- **Maintenance:** lack of updates, updates themselves can add risk

![900](Pasted%20image%2020230829203307.png)

![900](Pasted%20image%2020230829203331.png)

## Safety Critical programming guidelines
- **Programming principles that make intention of programmer less clear**
	- (careless indentation, nested comments, octal notation, identifier hiding, reliance on operator precedence, variable declaration in case statement, dead code, using return values of functions with them etc.)
	- This is all generally good programming advice that becomes especially vital in safety-critical programming
- **Programming practices that make the code less predictable / portable**
	- (use of macros, function pointers, multiple exit points, jumps, use of special compiler features, offsetof, dynamic memory allocation, recursion etc.)
	- These can be fine in standard applications programming, but are greatly discouraged in safety-critical systems where being able to make guarantees about modules of code is important
- **Programming practices that carry some inherent risk / require skill to use correctly**
	-  (pointer arithmetic, multiple levels of indirection)
	- Again, perfectly fine in ordinary application development, but even skilled programmers are likely to make mistakes here and the risk is too great to be worthwhile
- **Reliance on external code / operating system functionality**
	- (locale-dependent functions, <stdio.h>, <signal.h>, abort/exit/getenv/system, errno etc.)
	- Normal to use this stuff in applications development but keeping code centralised where possible makes stronger guarantees possible
- **Undefined and unspecified behaviour**
	- (dereference NULL, uninitialised variables, signed integer overflow etc.)
	- Important in all software development but vital in safety-critical software

## Security vs Safety
-  Similar rules are in place for secure systems as safety critical systems
-  The emphasis typically relies on different areas (e.g. secure systems will try to ensure that appropriate authentication and authorisation protocols are in place for remote administration, while safety-critical systems may see any remote administration as an unacceptable risk.)
- In many cases the rules for writing secure systems are less strict than safety-critical systems
- An insecure system will pose an unacceptable safety-critical system risk, while there are additional rules in place if human lives are on the line
- This is balanced by the fact that a lot more software needs to be secure than safety-critical

![700](Pasted%20image%2020230829230322.png)

![700](Pasted%20image%2020230829230341.png)

## Slides after 14 are examples from previous exams