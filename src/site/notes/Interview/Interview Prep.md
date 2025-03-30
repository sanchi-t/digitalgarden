---
{"dg-publish":true,"permalink":"/interview/interview-prep/"}
---


##### 1. Introduce yourself and your tech stack.

Hello, I’m Sanchit Sharma, a final-year Computer Science student at Bennett University, currently holding a CGPA of 9.41. Over the past few years, I've had the opportunity to work on some exciting projects and internships that honed my skills across the tech stack, particularly in web and software development. For instance, I interned with Fynarfin Tech, where I developed a new microservice for mobile money services and implemented BPMN workflows for efficient microservice interactions. I also contributed to the open-source community through Google Summer of Code with Zulip, enhancing user experience and developing new features. 
   
In addition to my internships, I’ve led and built projects like Learnify, an AI-driven course recommendation platform, where I applied my knowledge of Angular, Flask, and Kubernetes to create a seamless, data-driven user experience. I’m passionate about developing reliable, scalable applications and am excited to bring my technical skills and proactive approach to new challenges.
   
   
##### 2. Difference between framework and libraries (Javascript).

A **framework** serves as a blueprint, offering core functionalities and an established structure while allowing developers to customize and build upon it. In frameworks, the control flow is inverted: the framework manages the application's flow and calls the developer's code and functions as needed. This control inversion allows the framework to maintain consistency and handle high-level structure. Examples include Angular, Django, Express, Spring, and Next.js.

A **library**, on the other hand, is a collection of predefined functions and classes that developers can import and use directly in their code. Unlike a framework, a library does not dictate structure but instead provides the resources to build from scratch. Here, the developer has full control over the flow, deciding when and where to invoke library functions within the application. Examples include React, Three.js, Redux, Lodash, and jQuery.
   
   
##### 3. Difference between Javascript and Typescript.

The key difference between JavaScript and TypeScript is that JavaScript is **dynamically typed**. Although JavaScript uses keywords like `let`, `const`, and `var` and has types like `boolean`, `number`, `string`, `null`, and `undefined`, it doesn’t require explicit type definitions for variables or functions. This flexibility can lead to issues, such as inadvertently changing a variable’s type from its original one.

To address these issues, TypeScript was introduced as a **statically typed** language. In TypeScript, we explicitly define types for variables and functions, making it strongly typed. TypeScript enforces type consistency, preventing changes to a variable’s initial type and helping catch bugs related to data inconsistency. TypeScript also introduces **interfaces**, which JavaScript lacks. Interfaces define the structure a class should follow, acting as a blueprint without implementing methods. Finally, TypeScript code compiles down to JavaScript, ensuring compatibility with JavaScript environments.
   
   
##### 4. Difference between Flask and Django.

- **Type of Framework**: Django is a full-stack, batteries-included framework, while Flask is lightweight and minimalist.
- **Data Model**: Django uses object-relational mapping (ORM) for database interactions, whereas Flask relies on modular extensions like SQLAlchemy for database support.
- **Project Scope**: Django is ideal for multi-page applications; Flask is suited to single-page applications.
- **Flexibility and Control**: Django has less flexibility due to built-in modules, while Flask offers more control and flexibility with modular extensions
- **Template Engine**: Django uses a built-in template engine, while Flask uses Jinja2.
- **Debugging**: Flask includes an in-built debugger; Django does not.
- **Usage**: Django is preferred for complex, large-scale applications (e.g., Instagram, Udemy), while Flask is chosen for experimentation and simpler applications (e.g., Netflix, Reddit).
  
  
##### 5. How was the Experience at Fynarfin.

My experience at Fynarfin was incredibly rewarding. I had the opportunity to work on several new concepts and tools, which made it a steep but valuable learning curve. The initial weeks were challenging as I adjusted to the project and worked on meeting deadlines, often understanding only parts of the project at first. However, as I progressed, I gained a comprehensive understanding and could connect the various components to see the full picture.

My primary project was to develop a microservice called **Airtel-Connector**, designed to integrate Airtel Mobile Money with the Payment Hub. The Payment Hub, an orchestration of various microservices providing payment functionalities, was originally developed by the open-source organization Mifos. At Fynarfin, we customized and built upon this platform to meet client-specific needs. Additionally, I created a Helm chart for the deployment of this project and integrated the necessary existing microservices. I also developed a new BPMN using Zeebe to orchestrate the entire mobile money flow with Airtel.
   
   
##### 6. How was the Experience at Zulip (GSOC).

My experience with Zulip began well before GSoC officially started; I had been contributing to Zulip since December 2023. Contributing to Zulip was a fantastic learning opportunity, marking my first successful attempt at open-source contribution. The project setup was extremely smooth, thanks to Zulip's well-written and detailed documentation. However, navigating the large codebase and addressing initial issues was challenging, and my Git skills were initially lacking. With time, I improved in these areas and became more comfortable contributing to the project.

Open-source contributions teach more than just the technical stack; they build skills in collaboration, setting up PRs, writing clean code, communicating clearly, asking questions, and crafting meaningful commits. My project at Zulip involved completing unfinished PRs, where previous contributors were unable to continue. I chose this project because it allowed me to work across various aspects of Zulip rather than focusing on a single feature set. Each issue presented a unique challenge, as I often worked on new areas of the codebase, keeping the experience fresh and stimulating. The community was incredibly supportive, and it was a lot of fun to work on such diverse tasks. Many of the skills I gained at Zulip have since translated into my work at Fynarfin.
   
   
##### 7. What is helm? How is it different from kubernetes?
   **Kubernetes**:
    - Uses `kubectl` to manage resources directly through YAML files, which is straightforward for small applications but can become complex as projects scale.
    - Requires detailed configuration files for each resource (e.g., deployments, services, configmaps).
    - Ideal for small setups, but becomes cumbersome for large applications with numerous resources, requiring manual organization of multiple YAML files.
   **Helm**:
    - Acts as a package manager for Kubernetes, bundling multiple configurations into **Helm charts** that simplify deployment and management.
    - Provides reusable templates and version control, allowing easy updates, rollbacks, and parameterized configurations.
    - Suitable for both new and mature production clusters, enabling fast, scalable deployments and easy modifications.
      
For small-scale applications, Kubernetes YAML may suffice, but for larger, production-scale applications, Helm provides better organization, flexibility, and maintainability.


##### 8. Explain your projects.
   
   
##### 9. Why you chose PostgreSQL as database?

I chose an SQL database for Learnify instead of a NoSQL database to leverage its structured data model, which aligns well with the structured nature of the platform's course recommendations and user data. SQL databases like PostgreSQL offer robust relational capabilities, enabling complex queries and transactions that ensure data consistency, accuracy, and reliability across multiple tables (e.g., user preferences, course details, recommendations). The platform's dependency on strict relationships and the need for ACID compliance to maintain data integrity during interactions—such as managing user inputs and generating personalized recommendations—make an SQL database a more suitable choice over the flexible but schema-less nature of NoSQL. This approach also simplifies data analysis and integration with the AI/data science components used in Learnify. I already had used MySQL as databse for very small personal projects of mine and this time I wanted to try some other alternatives for MySQL as I like experimenting and working with new tech stack.
   
   
##### 10. Difference between React and angular.
   - **Type**:
    - **React**: A JavaScript library for building user interfaces, focused on the view layer (UI).
    - **Angular**: A full-fledged front-end framework developed by Google, offering a complete set of tools for building complex web applications.
- **Language**:
    - **React**: Primarily uses JavaScript (with JSX syntax) but also supports TypeScript.
    - **Angular**: Written in TypeScript, which offers static typing and additional tooling for error-checking and scalability.
- **Data Binding**:
    - **React**: Uses one-way data binding, where data flows in one direction from parent to child, making it easier to debug.
    - **Angular**: Utilizes two-way data binding, automatically syncing data between the model and the view.
- **DOM**:
    - **React**: Uses a virtual DOM to efficiently update and render only parts of the UI that have changed.
    - **Angular**: Operates directly on the real DOM, which can sometimes lead to slower performance in complex applications.
- **Learning Curve**:
    - **React**: Has a simpler learning curve focused on UI components, but requires additional libraries (e.g., Redux, React Router) for complete solutions.
    - **Angular**: Has a steeper learning curve due to its comprehensive features, such as dependency injection, directives, and services.
- **Component Architecture**:
    - **React**: Follows a component-based architecture with a focus on reusable UI components.
    - **Angular**: Also uses a component-based architecture but includes a full MVC (Model-View-Controller) setup, with integrated services and dependency injection.
- **Performance**:
    - **React**: Generally faster in handling UI updates due to the virtual DOM.
    - **Angular**: Can be slower for very complex UIs but is optimized for high-performance in enterprise-level applications.


##### 11. Soft Skill that are important.

I believe clear and open communication is one of the most important soft skills, and at times, it’s even crucial. I realized the importance of this through my previous work experiences. For instance, I thought I knew how to ask a question, which seemed simple and obvious before contributing to Zulip, but I soon learned that there’s more to it. When asking questions, it's essential to provide sufficient context and details to help the other person understand and respond effectively.
Questions like "I am unable to do this" are often unhelpful because they don’t mention what has already been tried, what recent changes were made, or include relevant output logs. Clear communication is especially important when working with a team in different time zones, as vague questions can delay the process significantly. 
Additionally, being clear with managers about potential delays is important. If you can’t meet a deadline, it helps to communicate early, so if the task is crucial, additional resources can be assigned. If someone is stuck, it’s better to be transparent rather than pretending everything is progressing smoothly.



##### 11. Weakness.

I believe I am still rapidly growing and learning as a developer. Of course, I'm not perfect, and I have my flaws. For example, I'm not an expert in any specific language, framework, or tool. I also make mistakes and sometimes overlook simple fixes, which leads me to spend more time than necessary on tasks. However, I see these areas as opportunities for improvement. With each work experience, I feel my skills getting sharper and better. Every time I work on something, I get a little better at it.


##### 12. Strengths.

I believe one of my strengths is my drive to constantly improve at what I do, as well as my eagerness to learn new things. There have been many times when I've been stuck on a problem for longer than others might take to solve it. However, I see persistence in those moments as a key factor in my growth. I learn the most when tackling challenges outside my comfort zone. During my GSoC experience, for example, I chose to work on completing unfinished pull requests because I wanted to explore new areas. For me, every issue I tackle is an opportunity to grow and face a new challenge.

##### 13. Difference between SDE intern and Fullstack intern.

As a subset of software engineering, full-stack web development shares a few similarities with software engineering.
- **SDE Intern**:
    - **Scope**: An SDE intern generally focuses on software development tasks related to specific areas of a project, which may include backend, frontend, or other specialized components.
    - **Focus**: The work is often more focused on writing, testing, and optimizing code for specific functionalities, algorithms, or system components. SDE interns may work with a variety of technologies depending on the project but are usually more specialized in one area (backend or frontend).
    - **Technologies**: They may work with backend technologies (e.g., Java, Python, C++, Node.js), system-level programming, APIs, databases, or other specialized tools.
    - **Role**: The role may involve implementing features, fixing bugs, improving performance, and writing automated tests for the software.

- **Fullstack Intern**:
    - **Scope**: A Fullstack intern works on both the frontend and backend of web applications or software projects. They are expected to understand the full technology stack, from database management to UI/UX design.
    - **Focus**: The work is broader, involving both the user interface (UI) and the server-side logic. Fullstack interns bridge the gap between frontend and backend development, meaning they need to handle both client-side and server-side programming tasks.
    - **Technologies**: Fullstack interns typically work with technologies like HTML, CSS, JavaScript (React, Angular, etc.), Node.js, Express, databases (e.g., MongoDB, PostgreSQL), and backend programming languages (e.g., Java, Python).
    - **Role**: Their role involves developing, testing, and maintaining the entire software application, both client-side (UI) and server-side (API, database). They need a broad understanding of the entire tech stack.
      
      
##### 14. Any optimization problems you ever faced? How you fixed that?

Yes, I have encountered optimization problems in the past. One such problem arose when I was working at Fynarfin. The issue I faced involved installing a Helm chart in CircleCI. The CircleCI image tier used by Fynarfin did not have enough memory to fully deploy the Helm chart, as it contained many microservices and their associated pods. Even after reducing the number of services in the chart to a minimum for testing purposes, the memory required still exceeded what was available in CircleCI.
To solve this problem, I consulted with my mentor, and we both observed the deployment of a smaller chart locally on our systems. We noticed that the pods required slightly more memory during initialization compared to when they were running. A large number of pods being initialized at once was likely causing the memory issue.
Based on this observation, we devised a solution: we deployed the Helm chart in two phases. In the first phase, only half of the services were enabled. Once all the pods from the first phase were running, we deployed the second half of the services. This approach resolved the memory issue and allowed the chart to deploy successfully.

##### 15. Team conflicts?

During academic group projects, disagreements among team members can sometimes arise. One such instance occurred during a hackathon I participated in with my team. As hackathon deadlines are usually very tight, we faced a disagreement about one of the features we were developing. Some team members felt that the feature would take too long to complete before the deadline and suggested dropping it.

To resolve this, we revisited our problem statement and carefully analyzed it. We identified the most critical features that were essential for the success of our project. After this analysis, we concluded that the feature in question was indeed important to include. We then had a quick discussion on how we could partially complete the feature in a way that it would still appear functional and contribute to the project’s overall success. In the end, we decided to proceed with a partial implementation of the feature, which allowed us to meet the deadline without compromising the integrity of our project.

##### 16. How did you managed working on two project (Fynarfin, GSOC) at the same time? How did you manage when the deadlines overlapped?

I was able to successfully manage both the Fynarfin and Zulip projects simultaneously by organizing my time effectively. During Fynarfin’s office hours, I focused solely on the Fynarfin project, and after work hours, I dedicated my personal time to the Zulip project. There were days when things became incredibly hectic, and I found myself feeling exhausted, which impacted the quality of my work on Zulip. Recognizing this, I spoke with my mentor at Zulip about extending the project timeline. As a result, I was granted an additional 4 weeks, which reduced the number of hours I needed to commit each week. This extension significantly helped me manage both projects without feeling overly stressed or exhausted.
    
Additionally, both organizations offered a flexible work culture, allowing me to work at any hour of the day as long as it didn’t interfere with collaborative tasks. I made sure to meet all deadlines, and this flexibility allowed me to work after office hours or on weekends, ensuring that neither of the projects was impacted and both progressed smoothly.

##### 17. SQL vs noSQL databases. When to use when?
1. Structure
     - **SQL Databases**: These are table-based and store data in rows and columns. SQL databases follow a **relational model** where data is structured with a predefined schema, and the relationships between different data points are clearly defined.
    - **NoSQL Databases**: NoSQL databases are more flexible and can be categorized into various types:
	    - **Document-Oriented**: Stores data in documents (e.g., JSON, BSON).
	    - **Key-Value Stores**: Data is stored as key-value pairs.
		- **Column-Family Stores**: Data is stored in columns rather than rows.
	    - **Graph Databases**: Used for storing data with relationships, typically represented as nodes and edges.
	    - These structures allow for nested and unstructured data, which makes them more flexible than the rigid table format of SQL databases.
	      
2. Scalability
	   - **SQL Databases**: SQL databases typically scale **vertically** by increasing the capacity of a single server (e.g., adding more CPU or memory). This can become costly and inefficient when handling large volumes of data, as it requires significant hardware upgrades.
	   - **NoSQL Databases**: NoSQL databases scale **horizontally** by adding more servers to distribute the load. This makes NoSQL a better fit for modern cloud-based architectures, where scaling out (rather than scaling up) is more cost-effective and efficient.
3. Language
	   - **SQL Databases**: Use **SQL (Structured Query Language)**, a standardized language for managing and querying relational data. SQL databases are strict about the schema, and any changes to the data structure require altering the schema.
	 - **NoSQL Databases**: NoSQL databases use flexible formats like **JSON**, **XML**, **YAML**, or **binary** for data representation. The data models are schema-less, which makes NoSQL databases well-suited for unstructured or semi-structured data and easy to evolve without rigid constraints.
	   
4. Support
	   - **SQL Databases**: SQL is a well-established and widely used technology, so it benefits from broad community support, extensive documentation, and a large number of tools and resources available.
	 - **NoSQL Databases**: While NoSQL databases are growing in popularity, they are still relatively new compared to SQL. As a result, NoSQL databases may have varying levels of support across different systems, and users might find fewer resources, tools, and community-driven help when facing challenges.
	   

##### 18. Why docker and kubernetes required for Learnify?

In my third year, we had a subject called **Cloud Computing**, where we were required to create a project and deploy it on AWS. The project was assessed based on the cloud services used and how well we demonstrated its functionality. I was working on a project called **Learnify**, which seemed like a promising idea for a team of three. 

After completing Learnify, I needed to deploy it on AWS. I was particularly interested in using **EKS** and **ECR** for deployment due to my interest in a cloud-native approach. To achieve this, I started learning more about **Docker** and **Kubernetes**, creating images for the various services used in Learnify, and preparing the necessary YAML files for deployment and Kubernetes services.

However, when I tried to deploy the project on AWS, I realized that services like EKS and ECR were restricted to us since the university had only provided access to the **free tier**. So, I decided to use an **EC2 instance** and deploy the project using **Minikube** within the instance. Additionally, I integrated other AWS services such as **Elastic Load Balancers**, **Elastic IP**, AutoScaling and **CloudWatch** to complete the deployment.
   
   
##### 19. Difference between Spring and SpringBoot.

The reason why we need Spring Boot is we are changing or shifting towards applications like microservices and with microservices, one of the most important thing aim is we would want to be able to develop applications very quickly. So instead of building one large application, we would like to build ten small microservices, which have their own scope and their own capabilities. Spring-based applications have lots of configurations. It can be of ****XML configuration****, Java configuration or annotations, etc. For example, If we want to use Spring MVC, we need to use ****@ComponentScan**** annotation, ****Dispatcher servlet****, ****view resolver****, ****web jars,**** etc. This kind of configuration makes it slow to develop an application. So, in this place, ****Spring Boot Autoconfiguration**** comes in. It looks at what types of frameworks are available at the classpath and it looks at what configurations are provided by the programmers or what configurations are provided already for the application. It will look at both of them. Data is not configured but there is hibernation on the classpath, so it will configure the data source automatically. It will configure the ****in-memory**** database, it will configure the dispatcher servlet automatically. This is called autoconfiguration. Spring Boot creates a starter project by which all the XML configurations and dependencies get by default.

##### 20. What is Ecmascript?

**ECMAScript** (often abbreviated as **ES**) is a standardized specification that defines the scripting language upon which several programming languages are based, including **JavaScript**, **JScript**, and **ActionScript**. The specification outlines the core features of the language, including syntax, types, operators, control flow, and methods for working with objects like arrays and functions.


##### 21. What is the difference between static and dynamic languages?

Typing involves specifying the data type of a variable or allowing the programming language to deduce it automatically. It plays a role in ensuring the integrity of data and the reliability of code.

###### Static Typing
Static typing is a typing system where variables are bound to a data type during compilation. Once a variable is assigned a data type it remains unchanged throughout the programs execution. This binding promotes type safety and detects errors at an early stage.
One of the advantages of typing is ensuring type safety which reduces the chances of runtime errors caused by mismatches in data types.
Another benefit is error detection. Since the compiler knows the data types during the development process it can catch errors before runtime resulting in reliable software.
Static typing also offers performance benefits. The compiler can optimize code effectively in languages with typing potentially leading to faster execution.

Examples of Statically Typed Languages:
- **C++**
- **Java**:
- **Rust**

###### Dynamic Typing
In contrast, dynamic typing allows variables to be bound to data types at runtime instead of during compilation. This flexibility enables concise code and ease of use. It compromises on type safety as a trade-off.
One of the advantages of typing is its flexibility. In dynamically typed languages variables have the ability to change their data type during runtime. This allows for adaptability in situations.
Another benefit is the ease of use that dynamic typing provides. Unlike static typed languages developers in dynamic typed languages don’t need to explicitly specify data types when coding. This simplifies the coding process. Makes it more intuitive.
Runtime variable type re-checking is another feature offered by dynamic typing. During runtime the type of a variable is checked which means any errors related to type mismatches might only be discovered at that point. While this can lead to issues it also offers flexibility in handling data types on the fly.

Examples of Dynamically Typed Languages:
- **Python**
- **JavaScript**
- **Ruby**


#### 22. What is circular dependency?

Circular dependencies occur when two or more components depend on each other, creating a loop that can be difficult to break because each component needs the other to function properly. This can lead to code that is hard to maintain and can cause issues when trying to make changes.

Dependency relationships can happen at various levels.

- _Class-level dependencies_, where a class `imports` another.
- _Module-level dependencies_, where a module declares that it depends on another. In Android development, we can find these in our Gradle files (`build.gradle`).
- _Project or service-level dependencies_, which are dependencies that are external to your application’s project. Unlike class-level and module-level dependencies, project or service-level dependencies are not typically needed to build your app. Instead, these dependencies are readily available at runtime via some protocol, like an Internet connection to access a Web API, or a connection to a specific Bluetooth device that your app might need to function.

>[!tip]
>Check out circular dependency and how to fix it in Node Js [[Interview/Backend/Backend Role#13. What is circular dependency in nodejs and how to fix it?\|here]].
