# General CS Topics

* Http Headers
    * CSP content security policy
    * same site cookies
    * cache control header (immutable)
    * Brotli Compression
    * accept-CH header: accept client hints, query for “width” and “viewport width” to easily implement responsive images (in most browsers, check safari support)
    * save data header
    * link rel=preload (no-push: to check the cache first) to tell the browser to preload resources it is gonna need in the future and minimize future load times
    * Feature-policy header
    * [Webhint](https://webhint.io/): tool to test your website for various problems, best practices
    * [Securityheaders](https://securityheaders.com/): check your headers
    * more Infos: [Slides](https://schepp.github.io/HTTP-headers/#/)
    * [YT talk](https://www.youtube.com/watch?v=II9m9_esNZc)
* Parallel Sub
    * Singleton
    * Delegate
    * Lazy Initialisation to boost startup performance
    * Adaptors
    * Factories
* threaded programming:
    * mutex
    * semiphore
* CSP: Communication Sequential Processes
* Shared-nothing architecture
* ACID: Atomicity, Consistency, Isolation, Durability
* Paxos Algorithm (Consensus)
* Multiversion Concurrency Control
* REST APIs
* gRPC: Google Remote Procedural Call (grpc.io)
* GIT
* Aggregation vs Composition
* OSI Model, TCP IP
* Google Cloud Functions
* !!! RegEx
* Aspect Processing
* Encryption and Cyphers
* Hash functions and their time space complexities, know when to use them
* Concurrent Processing, Threads and Locking
* Lambdas
* Code Review
* Design patterns: simplicity and one way data flow
    * Pub Oriented Programming (AOP)
* Cache Coherence
* Dynamic Dispatch
* Composition over Inheritance
* cron jobs
* GRASP Principles
* build a compiler
* CSS Animations
* CSS animation-timing-function: cubic-bezier
* CSS :before and :after
* user input validation: applicative-style (declarative) validation
* Trees
    * B-Trees
* Systems Design
    * Clarify load and usage cenarios, ask questions!
        * don’t scale unnecessarily, keep it simple!
    * Load Balancing, to scale Web Servers
        * NginX
        * DNS load balancing (simpler but less customisable)
    * Caching, to scale reading DB Servers
        * Redis, Memcache, Cassandra
        * CDNs, to scale Asset Servers (ie Image, Videos, etc)
            * pull vs push
        * Distributed File Systems
    * Indexes, to scale reading DB Servers
    * DB Sharding, to scale writing to DB Servers
        * vertical: put different tables on different servers
        * horizontal: split tables up and distribute over servers
        * NoSQL DBs make sharding easy by design
    * API Design
        * how do client and server communicate
            * what are the functions and methods they use
            * what is the data transport mechanism
            * json or protoccol buffers
        * what does the data look like
        * security
        * offline usage?
        * how to make it fast
        * 
* Microservices architecture

Python



1. Learn the language basics, such as data storage, keywords, decision making, and looping instructions.
2. Learn the language used to perform specific tasks.
3. Discover how libraries augment the language.
4. Delve into the language details and build an understanding of how the language works at a lower level.
5. Experiment with the language to see how interrelated changes affect each other.
6. Use the techniques learned to begin building simple applications.
7. Continue to build skills by creating progressively more complicated applications and researching additional language resources.
* DSP (https://www.youtube.com/watch?v=SrJq2AzXZME)
* Variable Scope
* Profiling with timeit, cProfile, line-profiler + kernprof, memory_profiler (exercises on https://missing.csail.mit.edu/2020/debugging-profiling/)
* Metaclasses
* Error Handling and (input)validation, exceptions
* Decorators
* List comprehension
* mutable types
* how to monitor performance
* map() and filter()
* dunder methods
* meta classes
* contextmanagers: with … as
* working with environment variables (anaconda)
* making modules
* build and manipulate packages
* Testing
* !!! Logging (?sentry), to aquire metrics
* how to make Python fast
* ML
    * Clustering
        * Fuzzy C-means
        * K-Means
* Authentication, Authorisation, Security
* DBs
* UIs, drag&drop
* Debugging
* Sockets (https://www.youtube.com/watch?v=3QiPPX-KeSc)
* actual Class implementation in Python
* Best Practices when working with user input
* Class initialise vs set attributes
* Python Interfaces
* Python Design Patterns
* None
* Scraping
* Cython
* Scripting, Tooling, write your own tools
* Modules:
    * time
    * timeit
    * threading
    * itertools
    * async I/O
    * for Web Developement:
        * Django
        * Flask (like Django but easier and more lightweight)
        * requests
        * twisted (online game dev)
        * BeautifulSoup (scraping)
        * Selenium
    * for Data Science:
        * numpy
        * pandas
        * matplotlib
        * nltk (natural language toolkit)
        * openCV (image and video data processing)
    * Machine Learning & AI
        * TensorFlow
        * Keras (higher level API for TensorFlow, easier)
        * PyTorch (like TensorFlow but a little more lightweight)
        * scikit-learn (an much simpler and easier to use library)
    * GUI
        * kivy (all platforms)
        * pyQT5 (very mature and lots of features)
        * tkinter (a little older than pyQT5, less capabilities but easier to use)
    * pygame (lightweight game engine, not too powerfull but nice for getting started)

Javascript / Typescript



* DOM Tree
* Meteor
* React/Redux
* Webpack
* see everything in Python

Dev-Ops



* NginX
* GraphQL
* Docker, (Vagrant)
* Kubernetes, Skaffold, Lens
* GCP, AWS
* Continuous Integration (github actions), Continuous Delivery

Databases



* MySQL
* !!! PostgresQL (Relational)
* !!! SQLite
* MongoDB, Dynamo DB, Firebase Firestare (Document)
* Neo4j (graph)
* Elastic Search, Solr, MeiliSearch (search engine)
* FaunaDB (multi model)
* MariaDB
* BigTable
* Caching
    * Redis (in memory)
    * Cassandra (wide, in memory)
    * Memcache

Audio



* real-time programming
* fast & efficient DSP
* lock-free thread synchronisation
* embedded systems in music hardware
* SIMD and memory alignment
* cross-platform challenges
* Fourier Analysis, FFT Fast Fourier Transformation, Cepstrum
* PulseAudio
* C++ Memory Management
* C++ Memory Model
* JUCE
* Reaktor
* MaxMsp
* MIXXX (open source contribution?)
* Game Audio
    * Fmod

Languages (Focus on a few, don’t spread too wide)



* Python (Backend, APIs, ML, Dataengineering)
* NodeJS (Backend, APIs)
* !!!SQL (DBs)
* XML
* Javascript, HTML, CSS (Frontend)
* Kotlin / Java (Android)
* Swift (iOS)
* C++ (Audio + Games)
* Markdown (Documentation)
* Typescript
* Rust

Misc



* 101 Graphic Design: Photoshop, Vector Graphics
* learn fast typing without looking at the keyboard
* Design Documentation
    * Summary of what you re trying to do
    * Motivation, why are you doing this?
    * ggf Screenshots, get a quick impression
    * Design alternatives
        * pros n cons
        * highlight the favourite
    * other considerations
        * experiments, prototypes
        * logging
        * accessibility to other interfaces
    * after the project is launched / failed it is a nice way to learn from it
    * nice documentation to put online, eg on a website, creates a story of what you did
    * helps communication if you re working in a team
    * functions as a contract for teams

Projects



1. With Design Patterns, Architectural Patterns
2. Professional UI
3. Database, CRUD functionality
4. Security
5. Handle a real business problem
* A MERN stack Project (MongoDB, Express, React, Node)
* Full Stack Project Planning: [https://dev.to/thecodepixi/fullstack-project-planning-3jml](https://dev.to/thecodepixi/fullstack-project-planning-3jml)
* a list of python project ideas: [https://www.theinsaneapp.com/2021/06/list-of-python-projects-with-source-code-and-tutorials.html](https://www.theinsaneapp.com/2021/06/list-of-python-projects-with-source-code-and-tutorials.html)
