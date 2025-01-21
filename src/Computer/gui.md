
传统的拖拽式 GUI 开发通常依赖于固定的布局，难以实现响应式设计。
现代框架通过数据绑定、状态管理等机制，使得开发者可以更轻松地管理复杂的 UI 逻辑。
现代 IDE 提供了更好的代码编辑、调试、版本控制集成等功能，通常支持多种编程语言和框架，开发者可以在同一个环境中处理多个项目。
低代码和无代码开发平台（如 OutSystems、Microsoft Power Apps、Adalo、Bubble、Webflow）通过拖拽式界面快速构建应用程序，而无需编写大量代码。
低代码和无代码平台提供了内置的响应式布局系统，一套预构建的响应式组件，提供了可视化编辑器中的响应式预览功能。

Any given application will have a set of requirements. Is Web one of the main deployment targets? Will there be embedded video? Is there a need to integrate with some other subsystems, such as a game engine? Each of these has profound implications.

Some problem spaces (compilers are an example) are “smooth,” in that continual refinement will lead to fairly similar outcomes no matter the starting point, but over time I’ve come to the conclusion that UI is especially lumpy. I believe this contributes to the continuing pattern of new UI toolkits coming out every couple months or so; the author surveys what’s available, finds none that match the specific set of requirements, and creates a new one.

We’re trying to be systematic about finding the best ways to do things, which ideally will make some solutions more general. And, increasingly, we’re designing things as modular layers that can be swapped out.

The trend in UI programming has been overwhelmingly away from a soup of mutable objects with interlinked references and toward various declarative or reactive patterns. One of the central questions is: 
which approach to declarative UI is best? It’s possible a clear winner will emerge, or perhaps there will be a different answer depending on the use case, or it might just come down to a matter of personal style, with a number of viable contenders (arguably that’s where JavaScript is). 

