# FEATURE Rules

## INTERDICTIONS ABSOLUES
NEVER copy-paste existing code to create similar functionality
NEVER create new files if existing files can be extended
NEVER ignore existing naming conventions, folder structure, or patterns
NEVER create files larger than 800 lines

## MANDATORY ACTIONS
Search entire codebase for existing functionality with same responsibility
Identify exact file with matching single responsibility to extend
Document why new file needed if extending would mix different concerns
Follow existing import patterns, naming conventions, and folder structure exactly
Write tests covering only new functionality added

## ALLOWED OPERATIONS ONLY
Add new functions to existing files
Extend existing classes with new methods
Add new properties to existing interfaces or types
Create new files only when extending existing ones is technically impossible
Modify existing functions only to add new parameters with default values

## PROCESS
1. Search codebase for functionality with matching responsibility scope
2. If same responsibility exists, extend that file maintaining SRP
3. If extension would mix concerns, create new file with single responsibility
4. Create new files following existing project structure exactly
5. Write tests for new functionality only, do not modify existing tests

## SUCCESS CRITERIA
New functionality: working and tested
Code reuse: maximum achieved (report existing functionality extended)
New files: justified with documented technical reasons
Pattern consistency: maintained (follows existing conventions)
Duplication: zero introduced
All existing tests: still passing
New tests: covering new functionality only

## VALIDATION RULE
If extending preserves single responsibility, extend existing code.
If extension would violate SRP or mix concerns, STOP and ask: "Extension would mix responsibilities. Should I create new file to maintain SOLID principles?"