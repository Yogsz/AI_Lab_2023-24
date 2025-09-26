# Ex.No: 11  Planning –  Block World Problem 
### DATE: 26.09.2025                                                                           
### REGISTER NUMBER : 212223060312 
### AIM: 
To find the sequence of plan for Block word problem using PDDL  
###  Algorithm:
Step 1 :  Start the program <br>
Step 2 : Create a domain for Block world Problem <br>
Step 3 :  Create a domain by specifying predicates clear, on table, on, arm-empty, holding. <br>
Step 4 : Specify the actions pickup, putdown, stack and un-stack in Block world problem <br>
Step 5 :  In pickup action, Robot arm pick the block on table. Precondition is Block is on table and no other block on specified block and arm-hand empty.<br>
Step 6:  In putdown action, Robot arm place the block on table. Precondition is robot-arm holding the block.<br>
Step 7 : In un-stack action, Robot arm pick the block on some block. Precondition is Block is on another block and no other block on specified block and arm-hand empty.<br>
Step 8 : In stack action, Robot arm place the block on under block. Precondition is Block holded by robot arm and no other block on under block.<br>
Step 9 : Define a problem for block world problem.<br> 
Step 10 : Obtain the plan for given problem.<br> 
     
### Program:

domain.pddl
(define (domain blocksworld) <br>
(:requirements :strips :equality) <br>
(:predicates (clear ?x) <br>
(on-table ?x) <br>
(arm-empty) <br>
(holding ?x) <br>
(on ?x ?y)) <br>
(:action pickup <br>
:parameters (?ob) <br>
:precondition (and (clear ?ob) (on-table ?ob) (arm-empty)) <br>
:effect (and (holding ?ob) (not (clear ?ob)) (not (on-table ?ob)) <br>
(not (arm-empty)))) <br>
(:action putdown <br>
:parameters (?ob) <br>
:precondition (and (holding ?ob)) <br>
:effect (and (clear ?ob) (arm-empty) (on-table ?ob) <br>
(not (holding ?ob)))) <br>
(:action stack <br>
:parameters (?ob ?underob) <br>
:precondition (and (clear ?underob) (holding ?ob)) <br>
:effect (and (arm-empty) (clear ?ob) (on ?ob ?underob) <br>
(not (clear ?underob)) (not (holding ?ob)))) <br>
(:action unstack <br>
:parameters (?ob ?underob) <br>
Ex.No: 11 Implementation of Block World Problem using PDDLDate : <br>
:precondition (and (on ?ob ?underob) (clear ?ob) (arm-empty)) <br>
:effect (and (holding ?ob) (clear ?underob) <br>
(not (on ?ob ?underob)) (not (clear ?ob)) (not (arm-empty))))) <br>


### Input 

Problem 1: Problem.pddl <br>
(define (problem pb1) <br>
(:domain blocksworld) <br>
(:objects a b) <br>
(:init (on-table a) (on-table b) (clear a) (clear b) (arm-empty)) <br>
(:goal (and (on a b)))) <br>

Problem 2: Problem2.pddl <br>
(define(problem pb3) <br>
(:domain blocksworld) <br>
(:objects a b c) <br>
(:init (on-table a) (on-table b) (on-table c) <br>
(clear a) (clear b) (clear c) (arm-empty)) <br>
(:goal (and (on a b) (on b c)))) <br>



### Output/Plan:

<img width="947" height="691" alt="image" src="https://github.com/user-attachments/assets/c9f3a1e0-5c53-4beb-a894-d60569c3a2ee" />

<img width="502" height="449" alt="image" src="https://github.com/user-attachments/assets/bfac2872-c825-4818-a7a3-004974550dfd" />





### Result:
Thus the plan was found for the initial and goal state of block world problem.
