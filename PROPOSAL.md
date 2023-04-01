This website is live at [https://15418-s23.github.io/final-project-website/PROPOSAL.html](https://15418-s23.github.io/final-project-website/PROPOSAL.html)

# 15618-sp23 Final Project Proposal

## TITLE: Parallel Collision Detection and Minimum Distance Query Algorithm

- Author: Bo Ying, Su (boyings) and Yufei Shi (yshi2)

## SUMMARY

In this project, we will implement a parallel collision detection algorithm and a parallel minimum distance query algorithm. The collision detection algorithm will be used to detect whether two objects collide or not. The minimum distance query algorithm will be used to find the minimum distance between two objects. We will implement these two algorithms on the GPU with the CUDA library and compare the performance with the naive CPU implementation.

## BACKGROUND

Collision detection is a fundamental problem in various fields, including computer graphics, robotics, and physical simulations.
The tasks in these fields require efficient and accurate collision detection to ensure the correctness of the simulation results.
Especially, in tasks such as robot motion planning, the collision detection algorithm must be able to handle complex interactions between multiple objects in real-time so that bad things (such as damaging the robot or the environment) do not happen.

However, as the objects become more complex and the number of objects increases, the collision detection problem becomes more challenging as traditional serial algorithms struggle to provide real-time performance.
This project aims to address this limitation by harnessing the power of parallel computing, exploring GPU-based parallelism and/or thread-level parallelism.
The anticipated improvement in efficiency and accuracy could have significant implications for robotic applications, enabling more advanced and responsive manipulations.

## THE CHALLENGE

- Load Balancing: Ensuring that the workload is evenly distributed among the processing units to avoid idle resources and sub-optimal speedups.

- Spatial Partitioning: Dividing the space into smaller regions to reduce the number of comparisons between objects. Some acceleration structures should be explored.

- Data Synchronization: Ensuring that the communication between the processing units is efficient and correct, and does not cause bottlenecks.

## RESOURCES

- We need CUDA-capable gpu with mid-higher end cpu.
- We do not have a starter code for this project. We will start from scratch and implement the algorithms from scratch. It is simple enough though, since we are basically just processing triangle meshes. We will use the CUDA library to implement the algorithms on the GPU.

## GOALS AND DELIVERABLES

- A successfull project will have the following deliverables:
  - A parallel collision detection algorithm that can detect whether two objects collide or not.
  - A parallel minimum distance query algorithm that can find the minimum distance between any two objects in the scene.
  - A visualization of the collision detection and minimum distance query by displaying the distances between objects and the collision points in the scene.
  - A performance comparison (speedup) between the parallel algorithms and the naive CPU implementation.
  - (Extra Goal) Collision detection and minimum distance computation are used extensively in Safety Set Algorithm (SSA) in robotic arms. Currently, SSA is implemented on the CPU and simplfies the geometry of the objects and robot arm to a set of capsules, which is far from the real geometry of the objects. We hope to implement the SSA on the GPU and use the parallel collision detection and minimum distance query algorithms to compute the safety set of the robot arm.
  - (Extra Goal) Demonstrate real-time SSA with GPU acceleration on collision detection and minimum distance query on industrial robots. This requires the entire pipeline to run under 5ms (200Hz) due to the real-time requirements of the robot controller. This is achievable with the current capsule-based SSA implementation on the CPU.

## PLATFORM CHOICE

- We decided to use the GPU to implement our algorithms. We will use the CUDA library to implement our algorithms on the GPU because we believe most of our geometric querying would be about comparing meshes. These arithmetic operations are very suitable for the GPU and can be parallelized without too many branches that could cause significant overlead.

## SCHEDULE

- These are the milestones we plan to achieve:
  - Implement sequential collision detection and minimum distance query algorithm on CPU.
  - Implement naive parallel collision detection and minimum distance query algorithm on GPU that parallelizes over mesh triangles.
  - Explore optimization techniques to improve the performance of the parallel algorithms. For example, we might be able to parallelize over fixed grid cells in the space. Or, we can think about how to leverage the convexity of the objects to improve the performance.
  - Optimize out algorithm for the robotic arm application. This does not require all-to-all minimum distance query, but only distance query between the robot arm and the objects in the scene.
