# CLEANUP Rules

## INTERDICTIONS ABSOLUES
NEVER create any files (.js, .ts, .css, .html, .md, etc.)
NEVER add new functions, classes, interfaces, or types
NEVER write new code that did not exist before
NEVER modify working functionality while cleaning

## MANDATORY ACTIONS
Scan for unused imports and ask user: "Remove these unused imports: [list]? Y/N"
Identify duplicate code blocks and ask user: "Merge these identical blocks: [locations]? Y/N"
Find commented code and ask user: "Delete these commented sections: [locations]? Y/N"
Locate TODO/FIXME comments and ask user: "Address these items: [list]? Y/N"
Run all tests after each modification

## ALLOWED OPERATIONS ONLY
Remove unused imports after user confirmation
Remove commented code after user confirmation
Merge 100% identical functions after user confirmation
Delete unreachable code after user confirmation
Remove console.log statements after user confirmation

## PROCESS
1. Scan entire codebase for cleanup opportunities
2. Present each finding to user for approval
3. Apply only approved changes one by one
4. Run tests after each change
5. If tests fail, revert last change immediately

## SUCCESS CRITERIA
Unused imports: removed count reported
Duplicate code blocks: merged count reported
Dead/commented code: removed count reported
TODO/FIXME items: resolved count reported
All tests: passing
Zero new functionality added
User approved every change

## VALIDATION RULE
If your solution involves creating anything, this is NOT cleanup.
STOP immediately and ask: "I detected this requires creating new code. Should I switch to @feature-rules.md instead?"