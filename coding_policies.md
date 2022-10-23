# Before start coding:
READ THE DOCUMENTATION AND DESCRIPTIONS CAREFULLY! Almost half of your mistakes is you due to forgetting or carelessly skimping
over important details in the descriptions

## IDE format option
Before coding, set up your format option in the IDE. This will prevent you from jumping back and forth between different code styles and making code formatting so much easier.

# Strucrture

## Class
Typically the question you should as is: "Is there shared data?"

Class is a group of functions (in a class called methods). If it is (data-speaking) beneficial to make a class so that they use the same data or similar reasons, put them in a class.

If it isn't, just keep them as separate functions.

Other attributes:
- one method performs only one functionality
- write comments and docstrings for readability
- arguments that should be immutable should be designaed final or constant
- test your code

## Order
- Global variables should always be at the top, since it is a custom to always declare them as global variables
- private methods and utilities should always be mentioned first. The methods that makes use of these should be declared and implemented last
- Generate class order in a story-like setting. 

## Modules
- Decouple as much as ossible

## Case vs if-statements

## String vs Enum
Cases when specific number of attributes, use Enums instead of Strings for safety

# Names
Naming conventions set by industry standard

Stick to the following naming convention:

(optional)[project] - [platform] - [repository name] - (optional)[description]

Terms:
- project: project name which the repository is a part of
- platform: where the project is hosted
- repository name: title of the repository
- description: extra details regarding the repository
- 'project' is set as optional to define repositories that are clearly only for that specific project and can't be reused.

ex)
UbiOps_Crop_Image
UbiOps_Face-Detection
UbiOps_Hash_Image
UbiOps_Analayse_Image
UbiOps_Download_Image
Lambda_DeepfakeProof_API
Lambda_DeepfakeProof_Analysis
Browser_DeepfakeProof_Extension

## Files
- short but descriptive (<25 characters) (Briney, 2015)
- avoid special characters
- make file and directory names lowercase
- use hyphens, not underscores, to separate words—for example, query-data.html. Use only standard ASCII alphanumeric characters in file and directory names.
- if date format is necessary, use the ISO 8601: YYYYMMDD. This makes it easier for platforms to sort files based on date

## Code
- aim for readability; use meaninful identifiers so that the name by itself should be clear and descriptive. This often requires multiple words
- Names shouldn't be too long (more than 80 chrs), especially if what they actually do isn't even complex. This is because simple code and functions can be obscured by unnecessarily long names

### Variables
- Should sound "nouny". 
- Environment variables should always be global variables (thus should always be at the top)
- Convention:

(optional)[adverb] - (optional)[adjective] - [noun]
- 
- The distinguishing trait (adverb, adjective) should be at the beginning, not the end.
Good example: ignoredTargets (better than toIgnoreTargets), reusedTargets 
Bad example: targetsToIgnore, targetsToReuse

- Use unmodified nouns for variable names unless you have a clear need for extra specificity. Add specificity modifiers in front of the core noun, and only when necessary to distinguish a variable from another of a similar type.
- Add specificity modifiers in front of the core noun, and only when necessary to distinguish a variable from another of a similar type
- Prefer whole-word nouns to abbreviations

### Methods/Functions
- Should soud "nouny". 
- Convention:

# Tests
On the automated unit tests, that one depends on whether or not the said part of the deployment. 

Questions to ask:
- Can be unit tested?
- Should be unit tested?

Not everything can be unit tested (think databases) and other things will likely only slow down production more than it takes to fix. 

Treat it case by case. Unit testing is great to do, but sometimes it's just too slow.

## Floats and Double
Avoid direct float or double comparision. 

## Paths
If the current directory is the tests directory, the relative filepath must be from the tests point of view.
If the current directory is the parent directory, the relative filepath must be from parent directory point of view.