# Class 6: Branch Prediction & Exceptions
## Branch Prediction
- Could we predict the branch?
	- Most branches have a bimodal distribution: tend to always be taken or not taken
	- For example: while(i < 1000)
		- Branch will be taken 1000 times
		- You could predict taken or untaken
			- As long as the next instructions will not change the state of the processor
- To make prediction easier we move PC calcualtion to the ID stage so we know the result earlier
	- Having it in the EX stage is a way to save on hardware
- ![[Pasted image 20220612231549.png]]
### Branch Delay Slot
- Could we put that idle slot to use?
- Ideally choose an instruction which is:
	- Independent of the branch instruction
	- Will be executed regardless
- If neither is possible, make sure it doesn't affect the rest of the program
- Like when you do:
	- ```cpp
	  if(foo) {
		  x += 5
	  }
	  y -= 4
	- That `y -= 4` would still be performed and could replace that slot
- ![[Pasted image 20220614184218.png]]
### Improving Branch Prediction
- There are two main classes of branch prediction schemes:
	- Static
	- Dynamic
- Based on the notion that history repeats itself
	- What did you on monday will happen next monday
- Two categories
	- Static
		- Untaken/Taken
	- Dynamic
		- N-predict buffer
#### Static Prediction
- Choose a direction throughout the program
	- Taken/Untaken
	- Helps decide how to fill the branch delay slot
- You want to pick the most probable case
	- Predicting taken averages 60% accuracy on SPEC benchmarks
	- Chose according to the statistics per branch
	- Direction based prediction
		- Forward vs. Backward
#### Dynamic Prediction
- History Repeats itself
- You are using past branch behavior to predict the future
	- This is the cornerstone of architectural design
	- Accurate speculation leads to a better look ahead
- Update the branch statistics in real time and make decisions based on these updates
- Simplest form is the branch prediction buffer
	- small memory indexed by lower portion branch instruction
	- Memory contains a bit which says whether the branch was most recently taken or not
	- Prediction is a hint and fetching starts in direction of prediction
	- If prediction is wrong hint is inverted
##### Simple Predictions
- 1-bit: whatever the last branch did, predict for this time
	- Branch decision based on bit
	- If bit is wrong branch result is taken and bit is inverted
	- Prediction will likely be wrong twice
- 2-bit: saturating counter; associate a strength
	- ![[Pasted image 20220615215512.png]]
#### Accuracy
- As the buffer is located in memory, it is possible to have branches index to the same entry (aliasing)
	- It is necessary to increase the number of entries possible to reduce the chances of this happening
	- However studies show that an infinite entry buffer would still have about the same prediction rate as 4096 entries
#### 2-Level Predictors/Correlating Predictors
- 2 bit predictors look at the branch to predict that branch's behavior
- However, looking at other branches in addition might help improve accuracy
- Predictors that use the behavior of other branches to predict branches are called correlating predictors
	- Existing predictors provide information about the most recent branches
	- Each predictor has two fields, taken or not taken, that predicts what the branch should do in that case
- A (1, 2) predictor uses the 2 bit prediction from the last branch to help predict the current branch
	- (m, n) predictor uses the last m branches to predict the current branch using n bits
##### Hardware
- (m, n) predictor uses the last m branches to predict
	- This means you need 2^m predictors
	- Each field has N bits
- This is built using an m bit shift register connected to $2^mn$ bit buffers
	- Think mux where inputs are the n bit buffers and selects come from the m bit register
#### Hybrid Predictors
- (0, 2) improved prediction but are not able to see the big picture
- Global predictors improve prediction, however,
	- If there is little correlation then we get noise
	- They also require a bit of set up time
- What about if we combine the two: Tournament Predictor
#### Tournament Predictor
- Tournament use multiple predictors
- Typically they have
	- One based on global information
	- One based on local information
- They use a 2-bit saturating counter to pick between local or global or a mix based on what was most successful
	- Counter requires two misprediction before changing predictor
- Tournament predictors have been used in Alpha processors (were the pioneers) as well as some AMD processors
##### Intel I7 Predictor
- ![[Pasted image 20220615224004.png]]
### Branch Target Buffer
- If we predict a branch was taken, we need to know the PC.
	- We will not know the PC until the ID stage
- Alternatively; as soon as we know a branch is coming we can predict it and calculate the possible PC:
	- A branch prediction cache that stores the predicted next PC is called a branch target buffer (or branch target cache)
	- Stores the PC of the branch as well as the predicted next PC
		- Ensures that we do not branch on the wrong instruction
- Is the current instruction a taken branch?
	- Provides answer in the IF stage
- If branch what is the predicted next PC?
	- Ensures that we can fetched the predicted next instruction in the next cycle
- ![[Pasted image 20220615224848.png]]
## Pipeline Implementation Issues
### Exceptions/interrupts
- Exceptions are unexpected events that acffect the normal execution order of instructions
- Two types
	1. Traps - typically synchronous and are internal to the CPU (think internal interrupt)
		- Breakpoint
		- Integer arithmetic overflow
		- Misaligned memory access (if alignment is requirement)
	2. Interrupts - typically asynchronous and from an outside source
		- I/O requests
		- Power failure
#### General Characteristics
- Syncrhonous vs. Asynchronous
	- In this case, synchronous means predictable. Happens in the same place each time, with the same memory access
	- Asynchronous is typically caused by devices external to CPU
- User requested vs. coerced 
	- User requested are asked for by the user program, coerced caused by some hardware event not usually under the control of a user program
- User maskable vs. not
	- Maskable can be disabled by a user task
	- Determines whether the hardware should respond
- Within vs. between instructions
	- between allows instructions to complete first
	- within occurs in the middle of an instruction
		- hardest to deal with
- Resume vs. terminate
	- resume continues after the interrupt, terminate does not
### Exceptions
- The most difficult expressions have two characteristics
	- They occur within instructions
	- The instruction within which it occured is restartable
- If the pipeline can be stopped so that:
	- Instructions before can complete
	- Those after can be restarted
	- Then it is referred to as a precise exception
		- These are a requirement in many systems
- ![[Pasted image 20220615231158.png]]
#### What happens during an exception
- The pipeline has to:
	- Stop executing the offending instruction in midstream
	- Let all preceding instructions complete
	- Flush all succeeding instructions,
	- Set a register to show the cause of the exception,
	- Save the address of the offending instruction, and
	- Then jump to a prearranged address (the address of the exception handler code)