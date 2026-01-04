# TC: Spec Format Compliance

Verify that specs follow META and RULE requirements.

## TC-001: File Naming

**Given** a specs directory with markdown files
**When** checking file names
**Then** each file shall match `<kebab-case-component>.md` pattern (META-001)

## TC-002: Item ID Format

**Given** a specification file
**When** checking item IDs
**Then** each ID shall match `<COMP>-NNN` format (META-002)

## TC-003: Item ID as Heading

**Given** a specification file
**When** checking item structure
**Then** each item ID shall be a markdown heading (META-003)

## TC-004: EARS Pattern Usage

**Given** a specification item
**When** checking its content
**Then** it shall use one of the EARS patterns with "shall" keyword (META-006)
