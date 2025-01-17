# Instructor Notes On Project 0

Hello there! Some quick things to get out of the way:

- **To create a handout tarball, run `make handout`**
- **If you add files that you want the students to receive, you need to modify
  the bottom of the Makefile to include them in the tarball**.

Alright. Welcome to the repository for Project 0! This contains the main Project
0 files for CS439, as adapted from an exercise in OSTEP.

The advertised parts of the repository are pretty well-explored by the students,
so let me give you some quick insight into the not-as-well explored portions.

### Files of Note

#### Argprinter

This is primarily intended to help debug issues with passing `argv` in `execv`.
Specifically, students often do one of the following:

- Clobber their `argv` entries before the `execv` call.
- Improperly terminate an entry in `argv`.
- Improperly terminate `argv` itself.

In all cases, the mistake usually becomes obvious if the exec-ed program prints
out the arguments it got, but most programs do not do this. At best, they will
print out a garbled fragment of an argument. The argprinter can be used to
debug these cases.

#### Shellspec

For students who really prefer a short, succinct version of the spec, we have
`.shellspec.md` which specifies the behavior of UTCSH in a breezy 150 lines.

I suspect what students really want is to be able to understand the spec
without having to spend like 2 hours reading it, which I am sympathetic to,
but doesn't really work well in this course...

Note: as of time of writing, this short-form is not included in the handout
because it is what is known in the professional world as "a little troll."

### Make Rules

There are several Makefile rules which are intended to assist in instructor
workload or student debugging. These include:

##### make handout

Used to generate the handout for the students. Avoids putting in files like this
one, or autogenerated stuff.

##### make grade

Used in grading (clearly). Prints the score to screen, as well as dumping a
hidden file (`.utcsh.grade.json`) into the project directory. This hidden
file can be parsed by a grading script to get info about points.

##### make fixtestscriptperms

Forcibly sets script permissions on all scripts in the test directory. Can be
useful if people are transferring in data from Windows machines and execute bits
are not being appropriately set.

### Tooling In-Use

Obviously, you need copies of `make` and `gcc` in order to build the project.

Formatting for C files and header files is done by `clang-format`, with the
default settings on the UTCS machines.

Markdown and JSON formatting is done using [dprint](https://dprint.dev/). Python
formatting is provided by `black`.
