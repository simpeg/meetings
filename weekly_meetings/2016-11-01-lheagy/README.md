# The State of SimPEG
Presented by: [Lindsey Heagy](http://github.com/lheagy)

[![2016-11-01](https://img.youtube.com/vi/gU9cKu4Ulmg/0.jpg)](https://youtu.be/gU9cKu4Ulmg)

# Notes

## Who
- Joe C. - Fluid flow, coupled inversion
- Andrew - IP, Regularizations
- Qian - Inversion of time-lapse gravity data at Prudhoe Bay
- Andy - Thermal
- Aline - Interpretation and inversion of inversion models, Sus from EM data!
- Liz - K means clustering.
- Craig - SFU > volcano, time lapse gravity and mag data
- Dom - Potential fields, dcip, regularization
- Sarah - EM for SagD
- Dikun - Em inversions
- Mike - DC res data, tunnel environments
- Tue - 2D TD & FD codes
- Seogi - IP (TEM)
- Rowan - Framework, Richards eqn

## Why
The future of geoscience will require many disciplines - geology, geophysics, hydrology - to work together. This includes involving multiple data types, methods, and … people!

## Geophysics into one place
- Working towards integrated interpretation
- Lots of work on a single inversion style
- The next step is building faster more rapidly, building together
- Creating a solid foundation
- No one person/research group has all of the time or expertise to do all of these methods!

## How do we...
- integrate these geoscience fields?
- work together as a community?
- get multiple research groups talking!!!?!!

## The future of geoscience requires…
- open, collaborative developments
- a foundation that is extensible to new problems
- lots of methods documented and implemented

## Goals
- Create a toolbox and framework for geophysics 
- Toolbox -> set of resources, utilities
- Need a framework -> structure and organization
- Not just a bucket of util codes
- Need some structure
- Need to make things look the same so that we can actually integrate methods!
- Focus on flexibility and speed for the researcher 
- There are lots of things lying around
- Build a community
- Promote a culture of reproducible work
- There are heuristics!
- Inversions are math-y-art
- Need to capture these things quantitatively
- There is a lot of knowledge (e.g. in doms head.) Need to get that out so andrew can use it… e.g.
- Want to share quantitatively
- Things need to be open
- Information is lost when the code is hidden in a black box, there’s more to an inversion than just a model file
- If things are not open, there is no way to make these things reproducible

## Not Goals
- Black box inversion codes
- E.g. this is not data in model out.
- Focused more 
- Initial focus on algorithm speed (starting to change)
- Not starting by focusing on the speed.
- We have interfaces to decent solvers e.g.
- Will be a focus of optimizing things in a bit. Really now…

## Ideals
- Modular: building blocks organized in a framework pieces available to manipulation 
- Declarative: express intent write what you mean looks like the math 
- Extensible: new research quantitative communication built in feedback loops
- Open: for the future reproducible opportunities for collaboration

## Parts of SimPEG

![parts of SimPEG](http://simpeg.xyz/s/img/simpeg/workflow.png)

- **Mesh** Organizes and stores numerical information. Provides operators. 
- **Model** Organizes your concept of a model, not necessarily on a mesh.
- **Map** Translates a model into a physical property on a mesh, has derivatives.
- **Properties** Relevant phys props for the problem
    - Properties ← Map1 ← Map2 ← Model
- **Problem** Describes and implements the physics of a PDE, has derivatives.
    - Where are your physical properties
- **Survey**      Sets up a geophysical survey based on source, receivers.
- **Source**      Describes how your survey is setup → RHSs of a PDE, has derivatives
- **Receiver**        Samples continuous fields, repeated over sources, has derivatives.
- **Fields**          Stores, organizes and access to fields and aliased products, has derivatives.
- **Data**            Organizes your data set by source/receiver pairs
- **Solver**      Linear algebra interface (iterative or direct)
- **DataMisfit**      Measure between prediction and reality, has derivatives (or MVP).
- **Regularization**  Measure between nice models and crappy models, has derivatives.
- **InvProblem**      Combines multiple DM + Reg, has constraints, gradients, hessians
- **Optimization**        Derivative based optimization.
- **Inversion**       Runs a series of optimization problems, conducts inversion through 
- **directives**
- **Directive**       Fiddle with things as an inversion progresses, print things, save 
- **Things**


## What we have

- FV Meshing
    - Mature!
    - Tensor mesh
        - Good IO to ubc mesh
        - VTK - talk to gudni
    - CylMesh
    - OcTree
        - Does not have all the utils to make the mesh
        - IO to UBC
    - Logically Rectangular Mesh
        - Curvy

- Problems - The physics
    - EM
        - FDEM
            - Very mature
            - Inverting for mu
            - 1-3D
            - Works with all meshes
        - TDEM
            - Recently updated
            - Still needs some work
            - Airborne works well
            - 1-3D
        - MT
            - Builds on FDEM
            - 1D and 3D
            - Need 2D
            - https://github.com/simpeg/simpeg/issues/452
            - Post doc at Mines! JiaJia Sun
                - Fuzzy c means!
        - Static
            - Talk to seogi and mike!
            - DC
            - 2.5 D
            - 3D
        - IP
            - Uses the DC code
        - Spectral IP
            - Not quite mature yet
            - Works for inverting for multiple parameters in 3D
        - MMR
            - On a branch, needs some work
            - Talk to Thibaut
    - Potential Fields
        - Grav
            - Integral formulation
            - PDE formulation coming soon
        - Mag
            - Integral
            - PDE by Seogi
            - Amplitude and Vector (MVI, cartesian)
    - Seismic
        - Not fully integrated
        - Talk to brendan
    - Fluid flow
    - Richards equation
        - 1-3D
        - Works for inverting for inverting for saturated hydraulic conductivity
- Integrating the various problems
    - Better objective functions
        - See https://github.com/simpeg/simpeg/issues/474 
        
## Who to talk to.
- Rowan/Lindsey - Routers
- Seogi - DC, IP, EM
- Gudni/Thibaut - MT
- Gudni - VTK stuff
- Thibaut - MMR
- Mike - DC
- Lindsey - TDEM, FDEM, mu inversions, education
- Rowan - Richards equation, meshing, joint inv, visualization
- Brendan - Seismic, Parallel, Web Visualization, Python


## Process
- Issues 
   - Write one!
   - Someone has already fixed your thing! Probably! Joe, probably.
   - E.g. https://github.com/simpeg/simpeg/issues/444 
- Conversations 
   - Slack
     - http://slack.simpeg.xyz 
     - Let’s do DC on the EM channel, for now
   - Meetings
- Version control
    - Use the github
        - Issues
        - Pull requests
- Development meetings
    - They are on youtube
- Branch updates happen about every month
    - Try to be backwards compatible, give deprecation warnings
    - Dev branch will sit a few weeks to give community a chance to look before merged to main truck
    - Big changes will be advertised on Slack


## Resources 
- Website: http://simpeg.xyz
  - The development of the website is here:
  - https://github.com/simpeg/website
      - Feel free to make an issue there.
      - There are a few issues….
- Tutorials: http://tutorials.simpeg.xyz
- Docs: http://docs.simpeg.xyz
- Slack: http://slack.simpeg.xyz 
- Talks
  - Scipy 2016 - https://www.youtube.com/watch?v=yUm01YsS9hQ 
- Education
  - http://geosci.xyz 
  - Scipy 2016 - https://www.youtube.com/watch?v=IW2LDsevvDk 
