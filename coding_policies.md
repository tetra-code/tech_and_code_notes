# Coding Policies
This policy is to help you establish good codin practices. Most of them are derived from the industry standards, which stems from logical decisions

## Markdown
in markdown
variable, class names are **
file and directory names are ****

## Structure

### Order
- Global variables should always be at the top, since it is a custom to always declare them as global variables
- private methods and utilities should always be mentioned first. The methods that makes use of these should be declared and implemented last
- Generate class order in a story-like setting. 

### Modules
- Decouple as much as ossible

### Classes




## Names
Naming conventions set by industry standard

### Files
- short but descriptive (<25 characters) (Briney, 2015)
- avoid special characters
- make file and directory names lowercase
- use hyphens, not underscores, to separate words—for example, query-data.html. Use only standard ASCII alphanumeric characters in file and directory names.
- if date format is necessary, use the ISO 8601: YYYYMMDD. This makes it easier for platforms to sort files based on date

#### Structure
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

### Code
- aim for readability; use meaninful identifiers so that the name by itself should be clear and descriptive. This often requires multiple words
- Names shouldn't be too long (more than 80 chrs), especially if what they actually do isn't even complex. This is because simple code and functions can be obscured by unnecessarily long names

#### Variables
- Should soud "nouny". 
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

#### Methods/Functions
- Should soud "nouny". 
- Convention:


#### Classes
readable variable and class names
one method performs only one functionality
write javadoc comments for readability
make necessary attributes final
test your code