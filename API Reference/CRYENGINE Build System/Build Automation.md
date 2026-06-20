# Build Automation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/56655881
- Page ID: 56655881
- Breadcrumb: CRYENGINE Build System > Build Automation
- Parent: CRYENGINE Build System

## Content

##
PAK files

PAK files are compressed archive files, very similar to .zip archive files. The PAK file format is used to compress large files or volumes of files into a single archive folder.; this makes it easier to distribute the files or download the files from the internet.

For example, if you have fifteen different files that you would like to send to someone, you can send them in a PAK file archive rather than email the files as fifteen different attachments.

The PAK file format is commonly used for video games, like the Quake and Half-Life computer gaming applications. These game file archives contain the graphics, sounds, objects, textures and other game details that are needed to run the game on the computer.

**
Advantages
**

-

-
Initial download of builds is relatively faster when in PAK format.

-
All (necessary) assets are available in one place.

-
A fully working project is obtained (projects can also be flagged as "not working", "stable", etc.).
**
Disadvantages
**

-

-
Can be tricky to identify  which files are present inside the PAK file, and perform copy/pastes, renames, etc.

-
Not easy to submit PAK files to a version control system.

##
Working with PAK Files

Crytek uses a combination of Python scripts

running into our Continuous Integration (CI) system with the
[Resource Compiler](../../Manual/System%20Utilities/System%20Utilities%20Overview/Resource%20Compiler.md)

in order to generate PAK files. This allows us to easily manage the content and configuration of a PAK file using an XML file

-
To generate PAK files, you need to run the Resource Compiler (
*
Tools/rc/rc.exe
*
in your CRYENGINE project) and pass a few arguments.

-
An example config XML file is
*
game_assets.xml
*
 (
*
../Tools/CryVersionSelector/rc_jobs/game_assets.xml),
*
which specifies the assets and how they are packaged.
Here is an example python script,
*
buildAssets.py
*
, which contains multiple arguments and serves as the first step in building assets and generating a PAK file:

```

`
py -3.6 _crybuild/buildAssets.py --platform=pc --deploytempdir2p4 --deployresults2p4 --deployfilesets=templates,cryproject
`

```

Next is a real sample from the
*
rc.exe
*
 command line where:

-
The first argument passed is the path of Resource Compiler;

-
The
`
/job
`
 argument passes the XML file for configuration;

-
`
/src
`
 and
`
/trg
`
 specify the source of the original assets and the destination of the packaged assets respectively, followed by other arguments for configuration.

```

`
Command line:
       "Tools\rc\rc"
       "/threads=processors"
       "/p=pc"
       "/game=GameSDK"
       "/job=_crybuild\project\gamesdk\rcjob_game.xml"
       "/engine=Engine"
       "/l10n=localization"
       "/src=D:\jk\workspace\gamesdk_main"
       "/trg=D:\jk\workspace\gamesdk_main\gamesdk_pc_rc_out"
       "/pak_root=D:\jk\workspace\gamesdk_main\gamesdk_pc_pak_out"
       "/logprefix=_logs\gamesdk_rcjob_game_asset_"
       "/verbose=0"
       "/SkipEditorMetaData=0"
       "/TargetHasEditor=1"
`

```

And finally an example
*
build
*
 function from source code that:

-
Calls the Resource Compiler;

-
Checks the Version Control System and syncs the code;

-
Checks if you use CMake or WAF as a build system, calling the corresponding script to run the build;

-
Packages the 'code' and 'asset' targets, and runs the necessary scripts to include them in the correct directories.

```

`
#python 3

from task.config import cfg
from task import args, bootstrap, cmake, easyanticheat, io, meta, p4, pakencrypt, rc, samba2, tbd, waf

def build(self):
        if cfg.buildrc:
            if cfg.jk_vcs == 'p4':
                bootstrap.force_run()
            if cfg.rc_buildsystem == 'cmake':
                cmake.run_script('win_x64_rc')
            elif cfg.rc_buildsystem == 'waf':
                waf.configure(cfg.waf_parameters)
                waf.build(target='win64', project_spec='resource_compiler', compilemode=cfg.rc_compilemode,
                          waf_parameters=cfg.waf_parameters)
            else:
                log.info('Unsupported buildsystem')

        for target in rc.get_targets('code', 'asset'):
            rctask = rc.RC(platform=cfg.platform, project=target['project'], gamedir=target['gamedir'],
                           jobfile=target['jobfile'], pc_has_editor=cfg.rc_pc_has_editor, branch=target['branch'])
            if cfg.rc_trace_assets and rctask.branch == 'asset':
                tbd.trace_assets(gamedir=target['gamedir'])
            rctask.compile_resources()
            if rctask.branch == 'code':
                pakencrypt.run(io.join(rctask.pak_dir, 'Engine'))
            if rctask.branch == 'asset':
                pakencrypt.run(io.join(rctask.pak_dir, rctask.game_dir))
                pakencrypt.run(io.join(rctask.pak_dir, rctask.localization_dir))

        if cfg.easyanticheat_generate_catalogue:
            easyanticheat.generate()

`

```

##
How to Build a CRYENGINE Game?

It is recommended that you familiarize yourself with the following pages to learn how to develop and compile your own projects in code:

-
[Getting Started with Game Code](../CRYENGINE%20Game%20Code/Getting%20Started%20with%20Game%20Code.md)

-
[Guide to releasing CRYENGINE V project](Guide%20to%20releasing%20CRYENGINE%20V%20projects.md)
The following chart shows the Jenkins build pipeline used for The Climb:

![Image](https://www.cryengine.com/docs/static/attachments/65438796)

*
The climb
*

The main steps in this pipeline are:

-
**
Kick:
**
 Project Configuration;

-
**
Build:
**
Divided into four sub-steps for building assets, shaders, and the code for the target system (PC in this example);

-
**
Complete
**
: This is where we check if everything was compiled correctly, before they are uploaded to the correct location on the network.

##
Build types

In Crytek we work with the following types of builds:

-
**
Local Development Build
**

Local Development builds are generally used while developing features, to make sure the current implementation is working.

They simplify the workflow for developers that have to compile and run the code without needing the CI system, usually for tests or validation purposes; this is done using the Integrated Development Environment (IDE) or Command Line Interface (CLI) tools on the developer's machine, or on a remote machine which isn't a distributed system.

-
**
Debug/Profile Build
**

Debug/Profile builds are slower builds with symbols that help the developer identify errors, attach breakpoints where necessary, debug on a PC or a console, analyze performance and have a better understanding of what is happening within the code. This is usually considered as a a performance/reliability build.

-
**
Release Build
**

A Release build is a fully featured binary that is ready for distribution. It contains no symbols and debug or breakpoint information, but might include obfuscation, encryption and even compression.

Release builds are a reliable measure of performance; since they depend on optimized settings, i.e., the defined settings/configuration, you can achieve an optimized build that will run on the target platform with the best performance possible.

See this
[documentation](https://docs.microsoft.com/en-us/cpp/build/optimizing-your-code?view=vs-2019)
 by Microsoft about optimization for a better understanding on the subject.

-
**
[Extra] Trybuilds
**

For every code submission into our Version Control System (VCS), we run a "lightweight" build to check if everything works as expected and to confirm that the code change did not introduce new problems.

-
**
[Extra] Nightly Builds
**

 A full build of our engine and/or the game that runs during the night. This one is heavily used by our QA team in order to test the current status of the product.

##
Automation

One of the biggest reasons to automate the build and deploy process is to speed up your development workflow and to reduce the number of possible failures. Below are some recommendations for your environment in order to have a healthy build system:

-
Use a CI system like Jenkins.

-
Do Test Driven Development (TDD) as much as possible and run the tests in parallel with your builds.

-
Use your CI to deploy your game.

-
Have a development, a stage and a production environment.

-
Use cloud services if possible; host your infrastructure if needed.

-
Containers are nice; ask your DevOps Team.

-
Avoid Python 2.x and use Python 3.x. It is a good language for automation that we use in our production workflow.

##
Code Samples

Below you can find a simple example of our pipeline code that can be used as reference.

-
The
**
pipeline.groovy
**
 script is the starting point of the CI job:

```

`
def jk

stage('Kick') {
    node("master") {
        checkout scm
        workspace = pwd()
        jk = load "${YOUR_WORKSPACE}@script/jk.groovy"
    }

    node('BUILD18') {
        jk.WS = 'climb_ce5__pc'
        jk.notify_recipients = 'build_team@YourCompanyEmail'
        jk.kick('project', 'project_pipeline_name')
    }
}

stage('build') {
    def build_steps = [:]

    build_steps["win64_code"]  = {
        node('BUILD_MACHINE_NAME') {
            jk.runjob("../build_script.py --build_step=build_binary --platform=pc --target=win64 --cleantempdir")
        }
    }

    build_steps["win64_tools"] = {
        node('BUILD_MACHINE_NAME') {
            jk.runjob("../build_script.py --build_step=build_binary --platform=pc --target=win_x64 --cleantempdir")
        }
    }

    build_steps["assets: pc"]  = {
        node('BUILD_MACHINE_NAME') {
            jk.runjob("../build_script.py --build_step=build_assets --platform=pc --deployfilesets=techart")
        }
    }

    build_steps["shaders: pc"] = {
        node('BUILD_MACHINE_NAME') {
            jk.runjob("../build_script.py --build_step=build_shadercache --platform=pc")
        }
    }

    parallel build_steps
}

stage('complete') {
    node('BUILD_MACHINE_NAME') {
        jk.complete_build('pc', false)
    }
}
`

```

-
The
**
jk.groovy
**
 script contains common functions that you can load into other scripts:

```

`
def notify(message, subj_result) {
    // notify slack, mattermost channel
    // email notification
}

def run_python(script) {
    if (isUnix()) {
        return sh(script: "python3.6 ${script}")
    } else {
        return bat(script: "py -3.6 ${script}")
    }
}

def runjob(script, notify_on_success = false) {
    timeout(time: 120, activity: true, unit: 'MINUTES') {
        echo "Running on ${NODE_NAME}."
        update()
        dir("../${YOUR_WORKSPACE}")
        {
            unstash "kick"
            try {
                run_python(script)
            } catch (Exception e) {
                notify("Command failed: '${script}': ${e}", "failure")
                throw e
            }
        }
        if (notify_on_success) {
            notify("<font color=green>Success:</font> '${script}'", "success")
        }
    }
}
`

```

-
The following Python script is where we have the heavy logic required for our builds.

```

`
#! python3

# your imports, check that
from task import args, bootstrap, cmake, fileset, io, meta, msbuild, p4, samba2, symbols, tbd
from task.config import cfg
from task.job import CodeJob

class BinariesJob():
    """
    Base class for project compilation.
    To add a new build system, subclass BinariesJob and override those methods that deal directly with the new system.
    """
    pass

class CmakeJob():
    """
    Compile projects using CMake.
    This launches a python script in Tools/build_meta/jenkins with the same name as the target.
    The output directories are configured in the project's filebook.yaml under 'binaries_<target>'.
    """
    pass

class MSBuildJob():
    """
    Compile projects using MSBuild/XBuild as appropriate.
    This calls MSBuild/XBuild directly.
    Output directories are registered in the project's filebook.json under 'binaries_msbuild_<target>'.
    """
    pass

class BuildStep()
  """
  Run the step requested into your pipeline.groovy file.
  Get the step from the config and run specific code.
  Eg.: shaders, assets, win64_code, win64_tools
  """
  pass

 if __name__ == '__main__':
    log = tbd.get_logger(__file__)

    parser = args.ArgumentParser(description='Build Binaries.')

    parser.add_argument('--build_step',
                        action='',
                        default='',
                        help='the step you want to execute the build')

    parser.add_argument('--platform',
                        action='',
                        default='pc',
                        help='')

    parser.add_argument('--target',
                        action='',
                        default='',
                        help='')

    parser.add_argument('--deployfilesets',
                        action='',
                        default='',
                        help='')

    parser.add_argument('--cleantempdir',
                        action='store_true',
                        default=False,
                        help='Clean temp directory.')

    parser.add_argument('--nocleantargetdir',
                        dest='cleantargetdir',
                        action='store_false',
                        default=True,
                        help='Clean target directory.')

    args = args.Args(parser=parser)

    if not cfg.scriptname:
        cfg.scriptname = cfg.target

    jobs = dict(cmake=CmakeJob, msbuild=MSBuildJob)
    job = jobs[cfg.buildsystem](cfg)
    job.exec()
`

```

Also in this example,
**
jk.groovy
**
 and
**
build_script.py
**
 are imported into the
**
pipeline.groovy
**
 script and used in there.

##
Related Information

-
[C++ Coding Standards](Accessing%20CE%20Source%20Code%20via%20GitHub/Coding%20Guidelines/C%2B%2B%20Coding%20Standard.md)

-
[Build Configuration](/docs)

##
Table of Contents

[PAK files](#pak-files)
[Working with PAK Files](#working-with-pak-files)
[How to Build a CRYENGINE Game?](#how-to-build-a-cryengine-game)
[Related Information](#related-information)
