# About Me 👋

Hi! I'm a passionate web developer from Brazil, and I've been coding since I was 13 years old. Over the past few years, I’ve focused heavily on Ruby and have had the privilege of contributing to over 30 projects. My journey in software development has always been driven by a desire to solve problems, build innovative solutions, and share knowledge with the developer community. One way I’ve embraced this is through maintaining open-source projects that aim to make programming more efficient and enjoyable for everyone.

By supporting my work, you're helping me dedicate more time to open-source contributions and tools that benefit developers worldwide. Your sponsorship allows me to focus on improving existing projects, developing new tools, and contributing to the tech community in a meaningful way. Every bit of support makes a huge difference, and I’m excited to continue this journey with your help!

# What I'm Working On 💻

This is a list of my current published and ongoing open-source work, along with my short-, mid-, and long-term goals for each project.

## Torque PostgreSQL

<a href="https://github.com/crashtech/torque-postgresql">
  <img src="https://carlosfsilva.com/assets/images/sponsor/gh-torque-postgresql.png" alt="Torque PostgreSQL - The seamless RoR interfaces to empower your PG queries - Unlock these advanced features under the same DSL" />
</a>

This is my 8-year-old project, built with the vision of being the go-to gem for leveraging advanced PostgreSQL features on top of ActiveRecord. While Rails offers robust support for PostgreSQL, there are certain advanced functionalities that Rails doesn’t cover natively. Torque PostgreSQL fills this gap, offering a seamless way to work with complex queries that ActiveRecord alone can't produce.

### Short-term - Views and Functions
For views, I aim to simplify the integration process by allowing `schema.rb` to store just the view’s filename and version, with views stored in a `db/views` folder. No additional migration files would be required. Views can be written in plain SQL or Ruby, using a simple interface similar to migrations.

For functions, I want to create a system where PostgreSQL functions are recognized and accessible through a configurable constant like `PG::Fn.lower(:email)`. This will convert arguments into the appropriate attributes and bindings, integrating seamlessly with Arel. Developers will also be able to declare custom functions in the `db/functions` folder, which is similar to the views solution.

### Mid-term - Composite Types and RBS
I've experimented with implementing composite types before, and a long-standing PR is open on this. My goal is to fully integrate composite types with [`ActiveRecord::Store`](https://api.rubyonrails.org/classes/ActiveRecord/Store.html), enabling developers to create custom handler classes under `app/models/types`. I also plan to support arrays of composite types.

One feature I’m particularly excited about is improving `created_at` and `updated_at` by introducing a more ergonomic composite type, `Type::Timestamps`, which would include `action, user_id, timestamp`, enabling better record change tracking.

Additionally, I plan to implement RBS types for all the gem's features. I believe that adding types to Ruby not only helps developers write better code but also makes it easier to explore new approaches and reduces the learning curve for any gem they use.

### Long-term - Multi-tenancy 🚀
Imagine a system where your models and database are designed from the ground up for multi-tenancy. I've been laying the foundation for this for a while, starting with [Physical Inherited Tables](https://github.com/crashtech/torque-postgresql/wiki/Inherited-Tables) and [Multiple Schemas management](https://github.com/crashtech/torque-postgresql/wiki/Multiple-Schemas). Now, the goal is to combine these to create a novel approach to multi-tenancy.

The concept is simple: use schemas to isolate tenants, allowing each tenant to have their own tables/models without risking collisions with the `public` schema or other tenants. To achieve this, I’ll introduce model callbacks and configurations to control tenant handling.

By leveraging inherited tables, we’ll unlock unique capabilities: tenants can have custom columns for personalized data, while administrators can still query the root table to access all tenant records. This level of flexibility is something I haven’t seen implemented before, and I’m excited to explore it further.

I'll be soon releasing an article about this.

## Rails GraphQL

<a href="https://github.com/virtualshield/rails-graphql">
  <img src="https://carlosfsilva.com/assets/images/sponsor/gh-rails-graphql.png" alt="Rails GraphQL - GraphQL reimagined the RoR way - Built with productivity and code quality in its core" />
</a>

Rails GraphQL is a 4-year-old project, written from scratch, with its own C-parser and a full GraphQL server for Rails applications. This has been one of the most enjoyable projects I've worked on, as it tackles one of the oldest challenges on the web: seamlessly connecting back-end servers with front-end clients. I believe GraphQL remains an incredible solution to this problem, and I'm excited about the continued potential it holds.

While the list of features I want to add to this gem is extensive, these are the most well-defined goals that I’m committed to implementing.

### Short-term - Rate Limiters, HTML Viewer, and Services
Firstly, one of the main concerns developers have with GraphQL is its potential complexity, especially in handling queries that could overwhelm a server. To address this, I plan to implement rate-limiting strategies such as `MaxDepth`, `MaxFields`, `MaxLength`, and `MaxComplexity` to ensure better control over query execution.

Secondly, the gem already includes a `/describe` endpoint that displays the Schema description, but I aim to improve this by adding an HTML viewer. This enhancement will provide better navigation and documentation of available resources, all while supporting I18n for descriptions.

Thirdly, the concept of Services is a short-term goal with far-reaching implications. Imagine being able to call your GraphQL mutations and queries from within your application without needing to go through the full GraphQL request-response cycle. Services could serve as both your Service Layer and API Layer, simplifying the process with a clean interface, like: `service = CreateUserMutation.call(email: 'john.doe@mail.com', name: 'John Doe')`. This approach will also improve testing by allowing direct interaction with business logic, bypassing GraphQL overhead.

### Mid-term - Definition Parser and Hot Generators
The current parser frees this gem from any dependencies other than Rails, focusing solely on the definition side of GraphQL. The goal now is to implement the translation of GraphQL definitions into proper Rails classes and folders. Directives like `@sourcedBy(model: "User")` will help streamline resource management by connecting definitions to the corresponding model/source, further simplifying the schema description process.

Hot generators will be a game-changer for TypeScript developers and teams working in stricter environments. The server will generate types dynamically without relying on external tools to read the introspection output. This feature, combined with Rails' native hot reloading, will enable seamless integration of types, including dynamic `.js`/`.ts` routes that deliver hot types in real time.

### Long-term - New Event Architecture 🏗️
Directives are one of the most powerful yet underrated aspects of GraphQL, and I love how I implemented them using an event-driven approach. However, I see room for improvement and plan to dive deeper into refining the event architecture. This could involve further integrating Rails’ [`ActiveModel::Callbacks`](https://api.rubyonrails.org/classes/ActiveModel/Callbacks.html) or developing a unique event system tailored to GraphQL’s needs, with features like indexed and "serializable" procs.

The long-term goal is to dramatically improve request performance while maximizing flexibility in how events are handled.

There’s a wealth of potential in GraphQL, and I look forward to sharing my thoughts on its strengths, weaknesses, future improvements, and what experiments I can add to this gem in an upcoming article.

## Torque Admin (Coming Soon)

<a href="https://github.com/crashtech/torque-admin">
  <img src="https://carlosfsilva.com/assets/images/sponsor/gh-torque-admin.png" alt="Torque Admin - Combining the newest of HTML, with your favorite CSS library and fully dynamic with Hotwire" />
</a>

Torque Admin is my latest open-source endeavor, and it’s a project I’ve been excited about for a long time. After extensive research, planning, and architectural work, it’s finally taking shape. Compared to my previous projects, Torque Admin is the most accessible yet also the most challenging. I believe it's time to provide a tool that fully leverages the best of HTML, CSS, Native JavaScript, and Hotwire, all under one roof.

### Short-term - CSS Libraries for Stimulus
The entry point for this project aims to excite the community and promote the power of Stimulus. The goal is to rewrite the JS side of popular CSS frameworks like Bootstrap, Tailwind, MaterialUI, Bulma, and FomanticUI (formerly SemanticUI) using Stimulus controllers.

The benefits are clear: these libraries currently depend on various JavaScript solutions—some still using jQuery—but they essentially aim to solve problems that Stimulus handles perfectly. If you're using Stimulus, why not use it entirely and cut down on unnecessary dependencies?

### Mid-term - A Pure CSS Library with Zero JavaScript
In order to explore the potential of modern HTML and CSS, I plan to build a CSS library named `@torque/ui` that will ship with **zero** JavaScript. The idea is to create dynamic experiences typically handled by JavaScript, using just HTML and CSS.

It’s a challenging yet feasible goal. I want to explore how much we can achieve using advanced HTML elements like [`<details>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details), [`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup), [`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist), and CSS features like [`:has(:checked)`](https://developer.mozilla.org/en-US/docs/Web/CSS/:has). The aim is to push the limits of what browsers can do natively, offloading complexity from JavaScript to CSS.

### Long-term - A Modern Admin Framework 👑
This is where all the pieces come together. Having worked extensively with [ActiveAdmin](https://activeadmin.info) and deeply customized it for various projects, I’ve gained firsthand experience of its strengths and shortcomings. While solutions like Rails [Rails Admin](https://github.com/railsadminteam/rails_admin) and [Avo](https://avohq.io) exist, they often fall short of modern standards and rely on rigid, proprietary components that hinder flexibility and adaptation.

My vision is clear: Torque Admin **must** look like Rails, you **will** pick your favorite CSS library, it **will** be powered by Hotwire, and it **will** be modern. It’s astonishing that developers still need libraries to handle something as simple as a [`<dialog>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dialog) element, and this project aims to change that. Custom admin behavior should not involve tedious workarounds or learning new component libraries.

This has been a long-term passion project, and I’m confident it’s something the community needs and deserves. I’ll be writing extensively about it, collecting feedback, and working towards a tool that fits developers’ needs while maintaining a modern, streamlined experience.

# Why Your Sponsorship Matters 🤝

Your sponsorship empowers me to create tools and resources that can significantly boost the productivity of Ruby teams, helping them work more efficiently and effectively.
