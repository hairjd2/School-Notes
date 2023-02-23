
- Status reports 
- Technical papers 
	- Informal tech notes or memos 
	- Working papers 
	- Formal technical papers for conferences & journals 
- Requirements Documents 
- Statements of Work 
- Proposals
# Rule 1: Know your purpose
- Capture knowledge and rationale (documentation)
- Propose solution (proposal)
- Provide rationale or persuasion (tech notes)
- Provide status (status report)
- Inquiry (request for information)
- Provide a process of instructions (process or owner's manual)
# Rule 2: Know your audience
- Status reports: management or customer
- Informal tech notes or memos: yourself or close team
- Working papers: experienced practitioners
- Formal technical papers for conferences and journals: experienced practitioners and theorists
- Requirements documents: user community or customer, some of whom may not be experts
- Statements of work: management and customer
- Proposals: customer
# Rule 3: Clarity Counts
- Should include:
	- Organization
	- Graphics
	- Logic
	- Language
	- Math
- Style should be "informally formal" unless specifically instructed otherwise
- **Use active voice**, avoid passive voice where possible
# Rule 4: Do Your Graphics First
- ==He can't emphasize this enough!== (must be important)
- A picture is worth 1000 words
# Rule 5: Write your math well
- Use an Equation Editor, not special font! (Eq. Ed, LaTek)
- Use in-line or independent equations, as necessary
- Number independence equations for future reference
# How to write
- Should take time to think before writing
- Use our graphical artifacts:
	- SBD, MSD, IEM, DFD, Control Flow (if you have it), FFBD
- Write for your audience: the people building thing (will be us but write like someone else has to build it)
## Specifications = Requirements
- In a spec or requirements document the purpose to clearly describe **what** the product must do...
	- ...without describing **how** the product will do it
	- ...unless the method is specfically determined by a stakeholder
- A good spec will let two competing teams create different, compliant designs
- Your audience is the people (engineers) who will actually design and build the equipment
## Defining the "requirement verbs"
- "Shall": mandatory items that will be tested
- "will": frequently used to describe intent or establish context; not for requirements
- "must": used to describe user actions, but occasionally used as synonym for "shall"; will not be used for this class
- "should": indicates a desired action or function or a recommended, but not required, attribute
	- "Shoulds" may become requirements due to higher level documents: "shall perform all the recommended actions in document xxx".
- "may": is permissive, and is generally used to specfically allow certain implementation options.
# Function Requirements
- What actions must your "verb phrase" perform
- Describe "what", not "how", unless "how" is necessary
# Performance Requirements
- How well must the function be performed
- Performance requirements must be quantitative
- When you establish the requirement, sketch out the test method as well.
- If you can't envision a test, it isn't a requirement
# Test Requirements
- Set the conditions and procedures for testing that a requirement is met
- Generally, test requirements are pass/fail, and are not designed to quantify performance.
- Quantifying performance falls in the realm of engineering tests, part of assuring that the design works as intended.
- Different from smaller engineering tests, which ensure that the pieces all work as they're supposed to.
# Verification
- Test: quantitative measurement of repeated performances
- Demonstration: qualitative measurement of repeated performances
- Inspection: repeatable, qualititative, usually just visual
- Analysis: mathematial extrapolation of system performance based on design details, meant for requirements that are hard to measure.
# General Outline for SRS
## Introduction
- Includes:
- purpose
- scope
- overview of the system being specified
- reference documents
- rough road map to the specification document
- ==**DO NOT USE SHALL!!!!!**==
## Functional Requirements
- "do this", "don't do that"
- not "how"
## Performance Requirements
- must contain quantifiable, testable values
## Interface Requirements
- Sometimes a separate document called an Interface Control Document (ICD)
## Test Requirements
- Indicate how the device or system is to be tested and performance and functions verified.
## Design requirement
- Indicate specific, usually standardized process that must be employed in the design, development, assembly, and verification
## Installation Requirements
- Gonna be none
- "When you put this receiver in your airplane, don't use a cable longer than 15m"