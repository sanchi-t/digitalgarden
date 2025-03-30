---
{"dg-publish":true,"permalink":"/interview/backend/backend-role/"}
---


# Generic

## Theoretical Questions:

### 1. What is callback?

A callback is a mechanism or function passed as an argument to another function, often used to handle specific tasks once a predefined operation completes. Callbacks are commonly utilized in asynchronous programming, event-driven systems, or frameworks where the backend needs to execute code after an event or action occurs.


### 2. Difference between put, post, and patch methods?

What is `POST`?
- `Create` in `CRUD`
- A method to create a new (subordinate) resource into the collection of resources
- When creating a new resource, the server will automatically assign an ID to this new resource.
- If successfully created, will return the HTTP status code `201 (CREATED)` and return a location-header with a link, like `https://www.example.com/recipes/1`.
- This method is neither **safe** nor **idempotent**. In other words, invoking two identical `POST` requests will result in two different resources containing the same information

What is `PUT`?
- `Update` in `CRUD`
- A method to primarily update existing resource. If the resource does not exist, the API may decide to create a resource.
- If successfully updated, will return the HTTP status code `200 (OK)`, or `204 (No Content)` if nothing is updated. If successfully created, will return the HTTP status code `201 (CREATED)`.
- This method is **not safe**, since it modifies (or creates) states within the resource.
- It is however **idempotent**, since the resource will be the same and has the same state as it did in the same call if it is created or updated a resource with the same call again.

 What is `PATCH`?
- (Also) `Update` in `CRUD`
- A method to make partial update on the resource.
- If successfully updated, will return the HTTP status code `200 (OK)`, or `204 (No Content)` if nothing is updated.
- This method is **neither safe nor idempotent**.

>[!info]-
>So why is PATCH not **idempotent** compared to PUT? It's because it matters how you apply your changes. If you'd like to change the `name` property of a resource, you might send something like `{"name": "foo"}` as a payload and that would indeed be idempotent since executing this request any number of times would yield the same result: The resources `name` attribute is now "foo".
>
>But PATCH is much more general in how you can change a resource (check [this](https://www.rfc-editor.org/rfc/rfc6902) definition on how to apply a JSON patch). It could also, for example, mean to move the resource and would look something like this: `{ "op": "move", "from": "/a/b/c", "path": "/a/b/d" }`. This operation is obviously not idempotent since calling at a second time would result in an error.


### 3. What is idempotent and safe in context of API?

Idempotence is a property of an operation that ensures that, if the operation is repeated once or more than once, you get the same result.

>[!faq]- Wanna hear something fun?
> Apply it once or more and the outcome's the same, idempotence is the name.

An HTTP method is **safe** if it doesn't alter the state of the server. In other words, a method is safe if it leads to a read-only operation. Several common HTTP methods are safe: [`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET), [`HEAD`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/HEAD), or [`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS). All safe methods are also [idempotent](https://developer.mozilla.org/en-US/docs/Glossary/Idempotent), but not all idempotent methods are safe. For example, [`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT) and [`DELETE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE) are both idempotent but unsafe.


### 4. Difference between Authentication and Authorization?

#### Authentication:
**Authentication** is the process of verifying the identity of a user or system. It answers the question, “Who are you?” and ensures that the user or system is genuine. Common methods include passwords, biometrics, and multi-factor authentication (MFA). For example, when a user logs in with a username and password, they are being authenticated. Authentication occurs before authorization and focuses on validating credentials.

#### Authorization:
**Authorization**, on the other hand, determines what actions or resources an authenticated user is allowed to access. It answers the question, “What are you allowed to do?” For instance, a user might be authenticated to access a system but authorized to view only certain files or perform specific actions. Authorization typically happens after authentication and involves assigning permissions based on roles, policies, or access levels.

### 5. Difference between dependency and dev-dependency?

#### Dependency
Dependencies are the packages that are required for the application to run in the production environment.

#### Dev-dependency
DevDependencies are the packages that are only needed for development and testing purposes. These packages include tools, libraries, and utilities that are used during the development, testing, and build process, but are not required for the application to function in the production environment.


### 6. What is SOP?

The **Same-Origin Policy (SOP)** is a security mechanism implemented by web browsers to prevent malicious scripts from accessing data on a different origin than the one that served the web page. An **origin** is defined by the protocol (e.g., `http` or `https`), domain (e.g., `example.com`), and port (e.g., `:80` or `:443`) of a URL. SOP ensures that a script running on `https://example.com` cannot interact with resources from `https://another-domain.com`.

For instance:

- A webpage at `https://example.com` can make requests to `https://example.com/api` without restrictions.
- However, requests to `https://api.example.com` or `http://example.com` would violate the SOP due to differences in the domain or protocol.

SOP protects sensitive data, like cookies and local storage, from being accessed by unauthorized scripts. While it enhances security, it also limits legitimate interactions between applications hosted on different origins.

### 7. What is CORS?

**CORS**(Cross-Origin Resource Sharing) is a protocol that allows servers to relax the restrictions imposed by SOP and enable controlled access to resources across origins. It is a server-side configuration that determines whether a web page on one origin can access resources on another. CORS works by sending HTTP headers that indicate what cross-origin requests are allowed.

For example:

- A frontend hosted on `https://example-frontend.com` might need to fetch data from an API hosted at `https://example-api.com`. Without CORS, this request would be blocked by SOP.
- By configuring CORS on the server at `https://example-api.com`, it can allow requests from `https://example-frontend.com` by including the header:
	```js
	Access-Control-Allow-Origin: https://example-frontend.com
	```


**How CORS Works**:
When a browser detects a cross-origin request, it performs a **CORS preflight request** in some cases. This is an HTTP OPTIONS request sent before the actual request to check whether the server permits it.

For example:

1. Preflight Request
	```bash
	OPTIONS /api/data HTTP/1.1
	Origin: https://example-frontend.com
	Access-Control-Request-Method: GET
	```

2. Server Response
	```bash
	HTTP/1.1 200 OK
	Access-Control-Allow-Origin: https://example-frontend.com
	Access-Control-Allow-Methods: GET, POST
	```

3. Actual Request: If the preflight succeeds, the browser sends the actual request.


### 8. Difference between thread and process?

#### Process
Processes are basically the programs that are dispatched from the ready state and are scheduled in the CPU for execution. PCB ( [Process Control Block](https://www.geeksforgeeks.org/process-table-and-process-control-block-pcb/) ) holds the context of process. A process can create other processes which are known as Child Processes. The process takes more time to terminate, and it is isolated means it does not share the memory with any other process. The process can have the following [states](https://www.geeksforgeeks.org/states-of-a-process-in-operating-systems/) new, ready, running, waiting, terminated, and suspended.

#### Thread
Thread is the segment of a process which means a process can have multiple threads and these multiple threads are contained within a process. A thread has three states: Running, Ready, and Blocked.

The [thread](https://www.geeksforgeeks.org/thread-in-operating-system/) takes less time to terminate as compared to the process but unlike the process, threads do not isolate.



### 9. Difference between REST and SOAP?

#### REST (Representational State Transfer)
REST is an architectural style used for designing networked applications. It is resource-oriented, meaning that each entity in the system is represented as a resource, identified by a unique URI (Uniform Resource Identifier). Communication in RESTful systems primarily leverages HTTP methods:

- **GET**: Retrieve data from a resource.
- **POST**: Create a new resource.
- **PUT/PATCH**: Update an existing resource.
- **DELETE**: Remove a resource.

RESTful APIs support multiple data formats such as JSON (commonly used due to its lightweight nature), XML, HTML, and plain text. REST is stateless, ensuring that each client request contains all the information needed for processing, which makes it scalable and suitable for distributed systems. REST also leverages HTTP features like caching, compression, and authentication mechanisms (e.g., OAuth, API keys). Its simplicity, flexibility, and compatibility with modern web standards make REST widely adopted in web and mobile app development, IoT systems, and microservices architecture.

Usage: Mobile apps, microservices, public APIs.

#### SOAP (Simple Object Access Protocol)
SOAP is a protocol specification for exchanging structured information in web services. It uses XML exclusively for message format and requires a detailed contract defined in WSDL (Web Services Description Language). A typical SOAP request consists of an **Envelope** (identifies the message structure), **Header** (optional metadata), and **Body** (actual content). SOAP is transport-independent and can operate over protocols like HTTP, SMTP, or even custom protocols.

SOAP has built-in specifications for features like:

- **WS-Security**: Ensures secure message exchanges through encryption, digital signatures, and authentication.
- **Reliability**: Supports features like message acknowledgment and delivery assurance, making it suitable for mission-critical systems.
- **Transactions**: Ensures compliance with ACID properties, making it a preferred choice for systems needing high integrity (e.g., banking and healthcare).

While SOAP provides robustness and reliability, it is considered heavyweight due to its verbose XML payloads, which can impact performance.

Usage: Banking, healthcare, enterprise systems requiring high reliability and security.

### 10. Difference between synchronous and asynchronous?

#### Asynchronous Operations

Asynchronous operations are non-blocking, meaning a task can be initiated, and the system does not wait for its completion before proceeding to the next task. Instead, the system continues to execute other operations while the initiated task runs in the background. Notifications like callbacks, promises, or events are used to handle the task's result once it is complete.

Characteristics of Asynchronous Operations:
- **Concurrency**: Multiple tasks can run concurrently.
- **Efficiency**: Improves resource utilization by allowing the system to perform other tasks while waiting for an operation to complete.
- **User Experience**: Enables smoother user interactions as the system remains responsive.
- **Example**: Fetching data from an API in JavaScript using `fetch()` or `axios`, where the data retrieval happens in the background while the UI remains responsive.

#### Synchronous Operations

Synchronous operations are blocking, meaning a task must complete before the next task begins. The system executes operations in a step-by-step manner, and other operations must wait until the current one is finished.

Characteristics of Synchronous Operations:
- **Sequential Execution**: Tasks are executed one at a time in order.
- **Blocking Behavior**: The system halts subsequent operations until the current one finishes.
- **Simplicity**: Easier to implement and debug due to the predictable sequence of operations.
- **Example**: Reading a file using Python's `open()` function in a single-threaded context, where subsequent code execution halts until the file is fully read.


### 11. What is the difference between a virtual machine and a container?

#### What Is Virtualization?

Virtualization is the process of creating a virtual version or representation of computing resources like servers, storage devices, operating systems (OS), or networks that are abstracted from the physical computing hardware. This abstraction enables greater flexibility, scalability, and agility in managing and deploying computing resources. You can create multiple virtual computers from the hardware and software components of a single machine.

#### What Is a Hypervisor?

The software that enables the creation and management of virtual computing environments is called a hypervisor. It’s a lightweight software or firmware layer that sits between the physical hardware and the virtualized environments and allows multiple operating systems to run concurrently on a single physical machine. The hypervisor abstracts and partitions the underlying hardware resources, such as central processing units (CPUs), memory, storage, and networking, and allocates them to the virtual environments.  You can think of the hypervisor as the middleman that pulls resources from the raw materials of your infrastructure and directs them to the various computing instances.

There are two types of hypervisors: 

1. Type 1, bare-metal hypervisors, run directly on the hardware. 
2. Type 2 hypervisors operate within a host operating system. 

Hypervisors are fundamental to virtualization technology, enabling efficient utilization and management of computing resources.

#### VMs and Containers

##### What Are VMs**?**

The computer-generated computers that virtualization makes possible are known as virtual machines (VMs)—separate virtual computers running on one set of hardware or a pool of hardware. Each virtual machine acts as an isolated and self-contained environment, complete with its own virtual hardware components, including CPU, memory, storage, and network interfaces. The hypervisor allocates and manages resources, ensuring each VM has its fair share and preventing interference between them.

Each VM requires its own OS. Thus each VM can host a different OS, enabling diverse software environments and applications to exist without conflict on the same machine. VMs provide a level of isolation, ensuring that failures or issues within one VM do not impact others on the same hardware. They also enable efficient testing and development environments, as developers can create VM snapshots to capture specific system states for experimentation or rollbacks. VMs also offer the ability to easily migrate or clone instances, making it convenient to scale resources or create backups.

Since the advent of affordable virtualization technology and cloud computing services, IT departments large and small have embraced VMs as a way to lower costs and increase efficiencies.

![A how virtual diagram of virtual machines interact with and are stored on a server.](https://www.backblaze.com/blog/wp-content/uploads/2021/10/Backblaze_What-Are-VMs.png)

VMs, however, can take up a lot of system resources. Each VM runs not just a full copy of an OS, but a virtual copy of all the hardware that the operating system needs to run. It’s why VMs are sometimes associated with the term “monolithic”—they’re single, all-in-one units commonly used to run applications built as single, large files. (The nickname, “monolithic,” will make a bit more sense after you learn more about containers below.) This quickly adds up to a lot of RAM and CPU cycles. They’re still economical compared to running separate actual computers, but for some use cases, particularly applications, it can be overkill, which led to the development of containers.

##### Benefits of VMs

- All OS resources available to apps.
- Well-established functionality.
- Robust management tools.
- Well-known security tools and controls.
- The ability to run different OS on one physical machine.
- Cost savings compared to running separate, physical machines.

##### What Are Containers?

With containers, instead of virtualizing an entire computer like a VM, just the OS is virtualized.

Containers sit on top of a physical server and its host OS—typically Linux or Windows. Each container shares the host OS kernel and, usually, the binaries and libraries, too, resulting in more efficient resource utilization. Shared components are read-only.

Why are they more efficient? Sharing OS resources, such as libraries, significantly reduces the need to reproduce the operating system code—a server can run multiple workloads with a single operating system installation. That makes containers lightweight and portable—they are only megabytes in size and take just seconds to start. What this means in practice is you can put two to three times as many applications on a single server with containers than you can with a VM. Compared to containers, VMs take minutes to run and are an order of magnitude larger than an equivalent container, measured in gigabytes versus megabytes.

Container technology has existed for a long time, but the launch of Docker in 2013 made containers essentially industry standard for application and software development. Technologies like Docker or Kubernetes to create isolated environments for applications. And containers solve the problem of environment inconsistency—the old “works on my machine” problem often encountered in software development and deployment.

Developers generally write code locally, say on their laptop, then deploy that code on a server. Any differences between those environments—software versions, permissions, database access, etc.—leads to bugs. With containers, developers can create a portable, packaged unit that contains all of the dependencies needed for that unit to run in any environment whether it’s local, development, testing, or production. This portability is one of containers’ key advantages.

Containers also offer scalability, as multiple instances of a containerized application can be deployed and managed in parallel, allowing for efficient resource allocation and responsiveness to changing demand.

Microservices architectures for application development evolved out of this container boom. With containers, applications could be broken down into their smallest component parts or “services” that serve a single purpose, and those services could be developed and deployed independently of each other instead of in one monolithic unit. 

For example, let’s say you have an app that allows customers to buy anything in the world. You might have a search bar, a shopping cart, a buy button, etc. Each of those “services” can exist in their own container, so that if, say, the search bar fails due to high load, it doesn’t bring the whole thing down. And that’s how you get your Prime Day deals today.

![A diagram for how containers interact with and are stored on a server.](https://www.backblaze.com/blog/wp-content/uploads/2021/10/Backblaze_What-Are-Containers.png)