
## How To Setup MutiProject Workspace

1. Copy All Projects in "Projects/"

2. Add This to main build.gradle of you project "Project/TestProject"
>  String getProjectName(String projectName) {
> return getRootProject().getName().equalsIgnoreCase(getProject().getName()) ? ":" + projectName : ":" + getProject().getName() + ":" + projectName
> }

3. Fix calls of rootProject
	- [ ] All Calls to rootProject from common/forge/fabric should be replaced with parent
	- [ ] All Call to rootProject from the main build.gradle should be replaced with project
4. Replace https://unreal.codes/2021/3/24/JHWFH1616601288784-chrome_nL0GIwc0tm.png to https://unreal.codes/2021/3/24/OUVD61616601306788-idea64_3Twq1ks52E.png
5. Depending on project

 - [ ] Common
   > implementation (rootProject.project("TestProject").project("common")) { transitive = false }
 - [ ] Fabric
	> developmentFabric(rootProject.project("TestProject").project("common")) { transitive = false }
	> modImplementation (rootProject.project("FTB-Teams").project("fabric")) { transitive = false }
    > implementation (rootProject.project("FTB-Teams").project("common")) { transitive = false }
 - [ ] Forge
   >  modImplementation (rootProject.project("FTB-Teams").project("common")) { transitive = false }
   > implementation (rootProject.project("FTB-Teams").project("common")) { transitive = false }
   > developmentForge(rootProject.project("FTB-Teams").project("common")) { transitive = false }




