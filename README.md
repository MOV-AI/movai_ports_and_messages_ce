# repository-template-ros-component


## Target ROS Distributions

When you instantiate your repository, one of the first questions you should be doing yourself is, "to what ROS distribution am I contributing to?".
The pipelines provided by this repository template will support you in whatever you decide as you will parameterize the distributions to which you want the package to be installed into.
How ?

Go to your pipeline folder (.github/workflows/) and update your pipelines that build and package ROS components (You do not need to adapt the release pipeline, as it simply publish generated artifacts).
Pipelines that you need to change:
- TestOnPR.yml
- DeployOnMergeMain.yml

In them you will find the input **ros_distro** where you will specify the target ROS distros.

![Screenshot from 2021-12-14 10-32-51](https://user-images.githubusercontent.com/84720623/146040977-773efcf5-e007-4d9f-89e2-55caf1b51013.png)

If you specify multiple distributions, the pipeline will build for each one of the specified distros the packages in your project.

## R&D Guidelines in terms of ROS distribution 

(if you are seing this after Mov.ai 3.0 please contact your captains as this might be outdated)

So this has to take in consideration the distribution our platform is currently supporting, and the migration to noetic (next supported distro).
If your ROS component:

- Still going for **2.2**, you must target for melodic and if by default it passes in noetic, you have a plus there.
- Not going to be included in **2.2**, you only target noetic.
- Currently being migrated to the next distro, you have 2 options.
  - Code supports both distros 
  - Split into different branches as the code differs for each ROS distro (Have main, and main-noetic branches).


### Branching model for a smooth transition of ros distro


![Screenshot from 2021-12-16 15-27-46](https://user-images.githubusercontent.com/84720623/146399979-5506e9cb-d210-4047-8b53-8a4d1c04e3ee.png)


Consider the 2.2 the current release you are working towards, and it only supports melodic, and after that the platform switching to projects on noetic.

## [DELETE ME ON INSTANTIATION] Template Description

Template to be used if you are going to create a ROS component.

This repository will provide you the following:
- Dummy component structure, even though you can have a multi project as long as you follow the ROS project structure, so we dont break the capabilities of rosdep installations.
- Project structure for your source. tests and CI/CD pipelines
- CI/CD that builds, validates and deploys your component to Nexus. The versioning and branching model follows the universal Mov.AI development guidelines.

To adapt the project to your needs, follow the TODOs placed throughout the project source and tests.



## Versioning and branching

The branches and meanings:
- branches derived from dev (feature/ or bugfix/): Its where developements should be introduced to. Its lifetime should be as should as the developments time. 
- dev: The most recent version of the code should be here as its the source of the feature branches. The purpose of this branch is the first point of integration from all features.
- main/ main*: The branch where you will find the most stable version of the component. Its a "deploy" of dev version to an internal release. This deploy must create an artifact that is avaiable to all other teams to use it and provide feedback to it.
- branches derived from main (hotfix/): Its where your hotfixes should be implemented. Do not forget to propagate your hotfixes to the other release versions and the main development release line.
![Screenshot from 2021-10-14 16-29-53](https://user-images.githubusercontent.com/84720623/137349613-368ea252-3c05-460c-8eef-20bb6c4b94f4.png)

In terms of versioning, we basically use semantic versioning but with a 4th digit, automatic incremented by our CI systems:
**{Major}.{Minor}.{Patch}-{buildid}**

If your component has a straight relation with a centralized system, we suggest keeping a relation with it in terms of major,minor and patch to ease support.

## Testing



## Component packaging
The ROS component is packaged through the framework **mobros**.

mobros pack

## Component version bumping
To bump the version you need to change your package.xml version attribute.

You don't need to worry about the 4th digit, as the CI system does the automatic bump of it.
