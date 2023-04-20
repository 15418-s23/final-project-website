## Project Milestone Report (due Wednesday, April 19, 9:00am)
The milestone exists is to give you a deadline approximately halfway through the project. The
following are suggestions for information to include in your milestone write-up. Your goal in the
writeup is to assure the course staff (and yourself) that your project is proceeding as you said
it would in your proposal. If it is not, your milestone writeup should emphasize what has been
causing you problems, and provide an adjusted schedule and adjusted goals. As projects differ,
not all items in the list below are relevant to all projects.

## Project schedule
Make sure your project schedule on your main project page is up to date with work
completed so far, and well as with a revised plan of work for the coming weeks. As by this
time you should have a good understanding of what is required to complete your project,
I want to see a very detailed schedule for the coming weeks. I suggest breaking time down
into half-week increments. Each increment should have at least one task, and for each task
put a person’s name on it.

- 04/19 - 04/21: Finish implement the sequential version of the minimum distance between mesh algorithm verifying the correctness. (Bo)
- 04/22 - 04/25: Parallelizing the support function of the GJK algorithm. (Bo & Yufei)
- 04/26 - 04/28: Parallelizing the minkowski sum of two meshes. (Bo & Yufei)
- 04/29 - 04/30: Benchmarking and scaling to thousands ob objects, writing report  (Bo & Yufei)
- 05/01 - 05/02: Video, Presentation, and Poster (Bo & Yufei)

## Summarize the work that you have completed
Our milestone progress is primarily focused on implementing the sequential version of the minimum distance between mesh algorithm. We obtained a 3D mesh for a FANUC robot, and created a basic mesh manipulation library for it. As for the sequential algorithm, we focus on two approaches, the naive version that uses a brute force approach to find the minimum distance between two meshes by calculating the distance for each pair of vertices. In this attempt, we are still working on optimizing it by calculating the minkowski sum of the two meshes, and then finding the minimum distance between the two meshes. However, we are still fixing some bugs here. In another approach, where we are trying to implement the gjk algorithm with minimum distance calculation, we are still halfway through.

## Describe how you are doing with respect to the goals and deliverables stated in your proposal
In the proposal, we stated that we would implement the sequential version of the minimum distance between mesh algorithm and parallelize it using CUDA. Our goad has not changed, as we did find some opportunities in parallelizing the algorithm. For example, the minkowski sum of two meshes can be parallelized by calculating the sum of each vertex in the first mesh with each vertex in the second mesh. The support function in the second approach is also parallelizable for mesh. We also found that it would be interesting to see how the hill climbing optimization (which has to be sequential) would compare with the parallelized version of brute force approach. We do still believe we can produce all the deliverables. However, the "nice to haves" (integrating it with SSA) would be too much for us to do in the remaining time.

## What do you plan to show at the poster session? Will it be a demo? Will it be a graph?
We expect to have a multi object moving around with real time minimum distance calculation demo. It would be a video.

## List the issues that concern you the most
The issues we concern the most is the correctness of the algorithm. Even with the sequential version, we are already struggling with edges cases like division of 0 when the objects are extremely close. We belive this would be harder to debug in CUDA.