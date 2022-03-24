# Everything You Need To Know About Microservices Design Patterns

## INTRODUCTION

The microservices case study that I will be covering in my presentation is the “Everything You Need to Know About Microservices Design Patterns” by Sahiti Kappagantula. This topic is particularly important because it challenges how and why we implement different patterns into our projects. Sahiti covers major design patterns at a high level that are commonly used in professional environments.

This study/blog covers 10 common microservices patterns, named Aggregator, Api Gateway, Chained or Chain of Responsibility, Asynchronous Messaging, Database or Shared Data, Event Sourcing, Branch, Command Query Responsibility Segregator, Circuit Breaker, and Decomposition. Additionally, this article discusses how they relate to the principles used to design Microservices, such as, Independency and Autonomously, Scalability, Decentralization, Resilient Services, Real-Time Load Balancing, Continuous delivery, Integration and continuous monitoring, failure isolation, and Auto provisioning. 

Because the provided resource is a blog, and some pattern descriptions are vague/short, I’ve used this one pager assignment to clarify, reword, and/or provide examples for the each of the 10 patterns using the provided resource along with a few others linked at the bottom.


## Terence's Rewrite of 10 Common Microservice Patterns
**The aggregator pattern** provides a division of responsibility, by handling multiple services that are capable of producing different data/outputs. As its name implies, the output from the differing services is combined via some ulterior/overarching ‘aggregator’ service, whose responsibility is to properly validate and then expose the varying datasets. This pattern is also important because it enables us to follow DRY principles by allowing us to have a parent service that is capable of producing desired results from multiple services, as opposed to implementing one for each service.

**The API Gateway Design Pattern** serves an entry point to multiple microservices by providing a plethora of abilities, not limited to reverse proxying, authorization, load balancing and aggregating. This design is an Aggregator variant and is responsible for mapping requests to the appropriate microservices, distributing them, and finally aggregating the results to be returned

**The Chained Responsibility pattern** generates a flow in which multiple services will perform an action, dependent on the result of the service preceding it. Since each service sends its results to the next, it creates a synchronous sequential process in which the client will wait for the completion or failure of the entire chain

**The Asynchronous Messaging Design Pattern** really shines when there would exist a large chain of services that would result in a longer waiting time for the client. This asynchronous pattern improves on the previous pattern by allowing services including the client to decouple by subscribing to one of two structures, a message queue or a message bus. This allows for all of the services to receive the same message from the client, without needing to wait for another service to perform work. Typically they will either subscribe to the changes completed by the other services to update itself, or be solely responsible for handling a type of request/message. To further clarify, this would omit a pattern such as REST in favor of the client subscribing to message updates from a message queue. 

**The Shared Data pattern** describes how to share responsibility of databases. The two cases that exist are when data should be shared amongst services, or should exist for a single service. When considering solutions for data duplication, differing storage requirements, or limited service interactions in your database you should use a database per service. When considering a solution for de-normalized/redundant data you should use shared. 

**The Event sourcing pattern** is used by developers to help discover event history, which is useful when logging interactions or debugging. In this pattern there exists an event store that consists of previously occurred events that have an associated state to describe what action took place and what data changed. 

**The Branch Pattern** is an extension of the Aggregator pattern, which we know to use aggregate data/results from multiple services. In this pattern, the aggregator can be structured to aggregate for multiple chains, multiple chains and services, or services.

**The Command Query Responsibility** Segregation pattern expands on both the event sourcing pattern and the shared data pattern. In all previous implementations we’ve discussed databases to be accessed in whatever method the service needs. In this pattern, focus is placed on associating models/flow with either command (write operations) actions or read (read operations) requests. This also allows our services to be more efficient, as we would only access the command flow when needing to update, and can continuously call the read flow for faster performance when only observing data (using event sourcing)

**The circuit breaker pattern** is used to solve service failures. When a service fails we may witness poor user experience and constant resource exhaustion. The circuit breaker service prevents these issues by monitoring the success and failure response types of other services (via proxy akin to api gateway). After too many consecutive failure types it will signal a downtime period. After this period has expired, the circuit breaker service will enter a test period and if successful will perform full functionality again 

**The Decomposition Design** pattern is a pattern for identifying how to decompose monolith architectures using two possible techniques. The first technique is division by business capability, where services are created for each capability (orders,payment,etc..). The second technique is decomposition using DDD, in which we identify an overall domain and divide it into sub-domains (ex/ ecommerce app domain → payments/store/account subdomains). Each sub-domain consists of bounded contexts which define a boundary around use cases and/or features (ex/ payments → selling context | listing context | support context). A service would then be responsible implementing/representing the bounded context

**The Vine pattern** solves one last issue that is decomposing already existing monolithic applications, which becomes a challenge granted their scale. Using this pattern, a replication is created at size 0 and features are strangled into microservices one at a time, increasing the size of the replication, and decreasing the size of the monolith. Over time the monolith grows smaller and the strangler application will grow larger

> ![Screen Shot 2022-03-24 at 1 17 28 PM](https://user-images.githubusercontent.com/54731009/159973443-c4e5d045-8acf-4d01-a301-0702d4d517a0.png)




Provided Resource: https://www.edureka.co/blog/microservices-design-patterns#CQRS

Additional Resources
https://docs.microsoft.com/en-us/dotnet/architecture/microservices/architect-microservice-container-applications/asynchronous-message-based-communication

https://vslive.com/blogs/news-and-tips/2018/02/go-fast-by-going-micro-microservices-design-patterns-you-should-know.aspx#:~:text=Branch%20Microservice%20Design%20Pattern%3A%20Branch,based%20upon%20the%20business%20needs.

https://dzone.com/articles/design-patterns-for-microservices-1

https://www.culttt.com/2015/01/14/command-query-responsibility-segregation-cqrs#:~:text=Command%20Query%20Responsibility%20Segregation%20(CQRS)%20is%20an%20architectural%20pattern%20that,Query%20cannot%20change%20the%20data.


