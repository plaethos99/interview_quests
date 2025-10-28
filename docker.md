



### Category 1: Core Concepts & Commands (1-10)

1.  What is the fundamental difference between an **image** and a **container**?
2.  Explain the difference between `docker run`, `docker start`, and `docker create`.
3.  What is the difference between `docker attach` and `docker exec`? Provide a practical use case for each.
4.  How would you find the IP address of a running container *without* `exec`-ing into it and running `ifconfig` or `ip a`?
5.  What's the difference between `docker rm` and `docker rmi`?
6.  You have a container that has exited. What single command can you run to remove it?
7.  What is a "dangling" image, and how can you remove all of them at once?
8.  When you run `docker run alpine echo "hello"`, why does the container immediately exit after printing "hello"?
9.  What does the `-d` flag do in `docker run -d ...`?
10. Explain the difference between the `restart: always` and `restart: unless-stopped` restart policies.

---

### Category 2: Dockerfiles & Image Building (11-20)

11. How does Docker's layer caching work during an image build? How should you structure your Dockerfile to best take advantage of it?
12. What is the difference between the `COPY` and `ADD` instructions in a Dockerfile? When is it appropriate to use `ADD`?
13. Explain the difference between `CMD` and `ENTRYPOINT`. How do they interact when both are used in the `exec` form?
14. What is a multi-stage build and what is its primary benefit?
15. Why is it considered a best practice to run a container process as a non-root user?
16. What is the purpose of the `.dockerignore` file?
17. You have a `RUN` instruction that installs many packages. How can you make the layer smaller by cleaning up in the same instruction?
18. What is the `SHELL` instruction used for?
19. If you build an image without a tag (e.g., `docker build .`), what tag does Docker assign to it by default?
20. How can you pass build-time variables to a Docker build? What instruction is used to consume them?

---

### Category 3: Docker Compose (21-30)

21. What is the primary purpose of Docker Compose?
22. In a `docker-compose.yml`, what does the `depends_on` directive do? What is a common misconception about what it guarantees?
23. Describe two different ways to pass environment variables to a service in a `docker-compose.yml` file.
24. By default, how can services defined in the same `docker-compose.yml` file communicate with each other?
25. What is the difference between `docker-compose up` and `docker-compose start`?
26. How would you scale a specific service to run 3 instances using Docker Compose?
27. What is the purpose of a `volume` declaration at the top-level of a `docker-compose.yml` versus inside a service definition?
28. How can you override the command for a service defined in a `docker-compose.yml` from the command line?
29. What does the `docker-compose down` command do? What is the difference between `docker-compose down` and `docker-compose down -v`?
30. How can you see the aggregated logs of all services defined in your `docker-compose.yml` file?

---

### Category 4: Networking (31-40)

31. What is the default network a container is attached to when you run it without specifying a network?
32. What is a "bridge" network in Docker?
33. How do you create a custom user-defined bridge network? Why would you want to?
34. Explain the concept of "port publishing" (e.g., `-p 8080:80`). What is happening at the host level?
35. What is the difference between `docker run -p 80:80` and `docker run -P`?
36. Can two containers listening on the same port (e.g., port 80) be running on the same host without port conflicts? Explain how.
37. How does DNS resolution work for containers on the same custom bridge network?
38. What is the "host" network mode and when might you use it?
39. What is a "macvlan" network and what problem does it solve?
40. How can you inspect a Docker network to see which containers are attached to it?

---

### Category 5: Volumes & Data Persistence (41-50)

41. What is the primary difference between a **bind mount** and a **named volume**?
42. When would you choose to use a bind mount over a named volume?
43. How do you create a named volume independently of any container?
44. What happens to the data in a volume if you remove the container that was using it?
45. What is a "tmpfs" mount and what is its main use case?
46. You are using a bind mount to your source code. You notice that changes you make on the host are not reflected inside the container. What is a likely cause?
47. How can you back up the data from a Docker named volume?
48. Explain the difference between the `ro` (read-only) and `rw` (read-write) options for volumes.
49. What is the purpose of the `VOLUME` instruction in a Dockerfile?
50. If you run a container with a bind mount to a directory on the host that doesn't exist, what does Docker do?

---

### Category 6: Optimization & Best Practices (51-60)

51. Why is it bad practice to use `:latest` as a tag in production?
52. What is the primary benefit of using a minimal base image like `alpine` or `distroless`?
53. How can you reduce the final size of a Docker image?
54. Explain the concept of "squashing" layers. Is it always a good idea?
55. Why should you group related `RUN` commands together using `&&`?
56. What is a healthcheck and how do you define one in a Dockerfile or `docker-compose.yml`?
57. How can you limit the amount of memory a container can use?
58. How can you limit the amount of CPU a container can use?
59. What is the purpose of the `--no-cache` flag during a `docker build`?
60. Why is it important to put `COPY` commands that change frequently (like copying source code) as late as possible in a Dockerfile?

---

### Category 7: Debugging & Troubleshooting (61-70)

61. A container is constantly restarting. What are the first two commands you would run to investigate why?
62. How do you view the logs of a container that has already exited?
63. You `exec` into a container and try to use `vim` or `ping`, but the command is not found. What is the most likely reason?
64. How can you inspect the filesystem of a container that will not start?
65. Your `docker build` fails on a `RUN` step. How can you debug the state of the image right before that step failed?
66. What does the `docker system df` command show you?
67. What does the `docker system events` command do?
68. You get a "port already allocated" error. What command would you run to find out which container is using that port?
69. A container is running but you cannot access the application via the published port. What are three potential things to check?
70. How do you copy a file *from* a running container to your host machine?

---

### Category 8: Security (71-80)

71. Why is running a container as the `root` user considered a security risk?
72. How do you specify a non-root user to run a container process in a Dockerfile?
73. What is a "secrets" management system in the context of Docker?
74. What is the purpose of Docker Content Trust (DCT)?
75. How can you scan a Docker image for known vulnerabilities?
76. What is the `--read-only` flag for `docker run` and why would you use it?
77. What is the `--user` flag for `docker run` and how does it differ from the `USER` instruction in a Dockerfile?
78. What is the principle of least privilege and how does it apply to Docker?
79. Why should you avoid putting sensitive information like API keys or passwords directly in a Dockerfile?
80. What is the purpose of the `--cap-drop` and `--cap-add` flags?

---

### Category 9: Registries & Distribution (81-90)

81. What is a Docker Registry?
82. What is the difference between Docker Hub and a private registry?
83. How do you tag an image in preparation for pushing it to a private registry at `my-registry.com:5000`?
84. What command do you use to push an image to a registry?
85. Before you can push to a private registry, what must you do first?
86. What is the difference between a public repository and a private repository on Docker Hub?
87. How do you pull a specific image tag from a registry?
88. What is an "OCI" (Open Container Initiative) image and why is it important?
89. Explain the process of what happens when you run `docker pull ubuntu:22.04`.
90. How can you log out of a Docker registry from the command line?

---

### Category 10: Miscellaneous & Next Steps (91-100)

91. What is the difference between Docker Community Edition (CE) and Docker Enterprise Edition (EE)?
92. What is Docker Swarm and how does it differ from Kubernetes?
93. What is the primary purpose of the `Dockerfile` named `Dockerfile.prod` in a project with multiple Dockerfiles?
94. What is the Moby project?
95. Explain the concept of "BuildKit". How do you enable it?
96. What is a "container runtime"?
97. What is the purpose of the `docker context` command?
98. What is the `docker init` command designed to do?
99. What is a "service" in the context of Docker Swarm?
100. You have a project with a `docker-compose.yml` for development. What's the next logical step for deploying this to a single production server?
