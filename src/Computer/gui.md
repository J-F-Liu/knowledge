Any given application will have a set of requirements. Is Web one of the main deployment targets? Will there be embedded video? Is there a need to integrate with some other subsystems, such as a game engine? Each of these has profound implications.

Some problem spaces (compilers are an example) are “smooth,” in that continual refinement will lead to fairly similar outcomes no matter the starting point, but over time I’ve come to the conclusion that UI is especially lumpy. I believe this contributes to the continuing pattern of new UI toolkits coming out every couple months or so; the author surveys what’s available, finds none that match the specific set of requirements, and creates a new one.

We’re trying to be systematic about finding the best ways to do things, which ideally will make some solutions more general. And, increasingly, we’re designing things as modular layers that can be swapped out.

The trend in UI programming has been overwhelmingly away from a soup of mutable objects with interlinked references and toward various declarative or reactive patterns. One of the central questions is: 
which approach to declarative UI is best? It’s possible a clear winner will emerge, or perhaps there will be a different answer depending on the use case, or it might just come down to a matter of personal style, with a number of viable contenders (arguably that’s where JavaScript is). 

