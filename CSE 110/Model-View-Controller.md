Software Design Pattern that splits an application into three components

A program has requirements, and it's responsible to make sure that requirement is met, but sometimes requirements are coupled.

Being coupled means changing one requirement requires changing the other one as well.

Elements/requirements can be unnecessarily coupled, which makes changing it costlier.

By minimizing coupling, which is done by separating different elements and keeping them independent of each other, we can divide up responsibilities and change them without affecting others, thus reducing cost/time.

We can either:
- Minimize relationships among elements in different modules
- Cohesion: Maximize relationships among elements in the same module

## Model-View-Controller (MVC)
- Model represents the state that might be updated, data and logic, backend
- View translates the model to pixels, displays, front end
- Controller implements interaction, receives user input, updates the model and select which view to show, middle end?

![[Screen Shot 2026-10-14 at 4.26.31 PM.png]]

There's a variant called the Model View Presenter (MVP), which also feeds model data into the view from the presenter
