## Gartner Microservices Blog

What I found most interesting about this article was the different justifications for using  microservices, miniservices and macroservices. The situation for which we should actually use microservices only seems to present itself in large prodcution environments, and I still struggle to understand how refactoring from miniservices is the recommended course to scale to a microservice. It seems rather inefficient to not optimize or design for this architecture style beforehand. Bringing it along only when it's convenient for your scale of application probably means there would be a lot of restructuring, making for a concerning tradeoff


Companies such as Amazon, Netflix and Twitter helped make MSA famous to deal with their ever growing scalability concerns, as the main benefit is agility. Microservice implies small, but it’s more importantly defining packaging and deployment than size. The constraints for a microservice are usually defined by the granularity as smaller details allow for more relaxed approach, while conversely larger ones require more agility and look less like a microservice 

### Microservice vs Miniservice vs Macroservice:

Microservice implies single responsibility and independently deployable application components. Miniservice serves a larger scope than a microservice and serves more than one feature and might be published for external consumption. Lastly, macroservices Aka SOA within a monolithic application expose a published API. This requires redeployment to make changes to the service and the entire application must be altered to scale it too.

> <img width="605" alt="image" src="https://user-images.githubusercontent.com/54731009/150430684-d6f9fed3-c780-4c4b-9741-9606d03066df.png">


API mediator or gateway is a single point of access that serves the service(s) themselves. The microservices allow for continuous delivery in that each feature can be changed without taking down the entire application. Miniservices focus more on domain and are at a slightly larger scale than feature driven, which means changing a feature could take down the functionality it fits within. Nonetheless, miniservices are the preferred way to implement a new service, while macroservice implementations are recommended to be scaled down only when there exists a reason to refactor 


