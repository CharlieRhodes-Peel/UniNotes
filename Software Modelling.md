### 3 Main types of software to design for:
- Project Based - Has a client with a commission (UML commonly used)
- Product Based - Has a target end user ([[Agile]] commonly used (iterative))
- Safety Critical Systems - Safety and reliability of code comes before all else, think nasa

# Main Stages of Project Based:
1. [[Requirement Gathering]] - Extraction what the client wants and what the system must do
2. Specification - Abstract representation of the system as a whole ([[Analysis]])
3. Design - More detailed representation of pieces outlined in spec (refine models)
	- (Diagram specified in [[Analysis]])
4. Implementation - Actual coding
5. Testing - Checking over code to verify it works
6. Review - Looking at the www ebi of shit ig :)

## Model vs Design
Model:
- Worked out with a **client**
- Try to figure out **WHAT** the system will do
- This is where good [[Software Design Patterns]] comes in
Design:
- Worked out with the **developers**
- Trying to figure out how the **model** will be **made**
- This is where good [[Software Design Principles]] comes in

# Main Issues With Software Modelling
- Main specification errors are only detected after a lot development has been done!
	- This is very costly
	- "Requirements and Architecture defects contribute to 70% of errors in development" with 80% of those only being found a lot later in development
### Why is this the case?
- Lack of precision in specification: Ambiguities and inconsistencies with 1 and 2 different parts of the spec
- Can also have **TOO** much complexity, which compounds the blindness of inconsistencies in this stage
### Testing vs Proof - (We need both !)
- Testing provides evidence of software faults (**negative** evidence)
- Proof provides **positive** evidence of software correctness