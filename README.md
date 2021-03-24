
## How To Setup MutiProject Workspace

1. Copy All Projects in "Projects/"
2. Add projects to settings.gradle 
  - [ ] addArchitecturyProject() for projects with common/fabric/forge
  - [ ] addLoomProject() for projects with forge loom
3. Add This to main build.gradle of you project "Project/TestProject"
>  String getProjectName(String projectName) {
> return getRootProject().getName().equalsIgnoreCase(getProject().getName()) ? ":" + projectName : ":" + getProject().getName() + ":" + projectName
> }

4. Fix calls of rootProject
	- [ ] All Calls to rootProject from common/forge/fabric should be replaced with parent
	- [ ] All Call to rootProject from the main build.gradle should be replaced with project
5. Replace https://unreal.codes/2021/3/24/JHWFH1616601288784-chrome_nL0GIwc0tm.png to https://unreal.codes/2021/3/24/OUVD61616601306788-idea64_3Twq1ks52E.png
6. Depending on architectury project 

 - [ ] Common
   > implementation (rootProject.project("TestProject").project("common")) { transitive = false }
 - [ ] Fabric
	> developmentFabric(rootProject.project("TestProject").project("common")) { transitive = false }
	> modImplementation (rootProject.project("FTB-Teams").project("fabric")) { transitive = false }
    > implementation (rootProject.project("FTB-Teams").project("common")) { transitive = false }
 - [ ] Forge
   >  modImplementation (rootProject.project("FTB-Teams").project("forge")) { transitive = false }
   > implementation (rootProject.project("FTB-Teams").project("common")) { transitive = false }
   > developmentForge(rootProject.project("FTB-Teams").project("common")) { transitive = false }
7. Depedning on a forge loom project
 - [ ] Add architectury plugin
    > plugins {
    >    id "architectury-plugin" version "3.0-SNAPSHOT"
    >}
    >
    >architectury {
	>minecraft = project.minecraft_version
	>platformSetupLoomIde()
	>forge() //or fabric()
    >}
 - [ ] for adding a project do the same you would for Fabirc or Forge above   




