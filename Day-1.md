# 1.1 What is an Embedded System ?

An embedded system is a combination of computer hardware and software, either fixed in capability or programmable, designed for a specific function or functions within a larger system. Industrial machines, agricultural and process industry devices, automobiles, medical equipment, cameras, household appliances, airplanes, vending machines and toys, as well as mobile devices, are possible locations for an embedded system.

# 1.2 What Is a Target?

A target deploys MATLAB® and Simulink® designs to embedded hardware. With a target, you can prototype, verify, and deploy your application by generating processor-specific code, integrating real-time operating systems and device drivers, and profiling execution on your embedded hardware.

# 1.2.1 Hierarchy of Targets
You can develop a target by using an existing target. The existing target is then a reference target of the target being    developed. This guide shows you how to develop a target using a MathWorks® reference target.

Targets support hardware at the processor or board level. A hardware board includes one or more processors, and perhaps external memory, I/O devices, and other electronic components.

A target for a processor provides features that are related to the processor, such as assembly language optimizations. A target for a hardware board provides features related to the board, including its processor and any of its additional components, such as I/O device drivers.

Each hardware board includes a processor. When a target for a hardware board is developed, the target for the hardware board's processor is often used as the reference target.

For example, a BeagleBone Black board includes an ARM Cortex-A8 processor. Assume a target for BeagleBone Black boards supports the BeagleBone Black board, and a target for ARM Cortex-A processors supports the processor. Then you can develop a target for BeagleBone Black boards using the target for ARM Cortex-A processors as its reference target.

