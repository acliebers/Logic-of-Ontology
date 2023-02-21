# Project 2

Your second project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

```
Tip #1: Carefully study the Baader, et. al. selections assigned on bisimulation; it is deceptively subtle, and quite powerful. 
Tip #2: Google is still your friend. So is stackexchange...
Tip #3: Work together to solve these problems, even for initial submissions and when you do, document this in github. 
Tip #4: Work together as a team. 
```

1. Let V be a vocabulary of ALCI consisting of a role name "P". Interpret part_of as "x is a part of y". Using this role name, define the following formulas in this language:
```
  (a)  PP that says that x is a proper part of y
        I can't do  this because I don't have the resources to discuss individuals or identity. 
  (b)  iPP that says that y is a proper part of x
        I can't do  this because I don't have the resources to discuss individuals or identity. 
  (c)  iP that says that y has x as part 
        iP ≡ ∀part_of-.C
  (d)  O that says that x overlaps y
        I can't do  this because I don't have the resources to discuss individuals or identity. 
  (e)  D that says that x and y are disjoint 
        I can't do  this because I don't have the resources to discuss individuals or identity. 
```

2. Use your axioms from question 1 as the basis of an ALCI T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

3. Translate the following first-order logic axioms into ALCI: 
```
(a) ∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
    I can't translate this because I don't have the resources to talk about individuals or identity in ALCI. 
(b) ∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))
    I can't translate this because I don't have the resources to talk about individuals or identity in ALCI.
(c) ∀y(R(x, y) → ∃x(R(y, x) ∧ ∀y(R(x, y) → A(y))))
     I can't translate this because even if we imagine that this is a wff and the unbound variable, x, is implicitly bound by a universal quantifier, I don't think I can translate the second conjunct into a statement of DL, since while it should look something like ∀r.(¬C 

(d) (∀y)(R(x, y) → A(y)) ∧ (∃y)(R(x, y) ∧ B(y))
    This is not a wff, so I can't translate it. 
```
4. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that demonstrates ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming. 

5. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that _does not_ demonstrate ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming. 


6. Explain the difference - using natural language - between the description logic expressions:
  ```
  (a) ∃r.C and ∀r.C
      The first one means, roughly, that there is an r-filler which is a member of C, and the second one means, again roughly, that all r-fillers are members of C.
      
  (b) ∃r-.C and ∀r-.C
      The first one means, roughly, that there is a member of C which is an r-filler, and the second means that C's members contain all r-fillers. 
      
  (c) <=nr and <=nr.C
      The first one is a schema for a number restriction, which is a concept description meaning something like "There are less than or equal to n r-fillers". The second one is a schema for a qualified number restriction, which means somethign like "There are less than or equal to n r-fillers in C"
      
  (d) ∃r-.C and ∃r-.{a} 
      The first one means that there exists a member of C which is an r-filler, while the second specifies that a is an r-filler. 
```

7. There is a delightfully helpful subreddit called "ELI5" which stands for something like "explain it like I'm 5" where users post conceptually challenging questions and other users attempt to provide explanations in simple, jargon-free, terms that presumably a 5 year-old could understand. Using this as a model, explain the _finite model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 
```
_finite model property_

A logic has the finite model property if and only if all of the non-theorems of that logic can be falsified with finite models of that logic. 

That is:

A logic is the combination of a vocabulary of symbols, rules for combining those symbols in different ways, and a set of axioms. Axioms are like statements using the logic's vocabulary (and combining rules) which are assumed to be true. For example, a good candidate for an axiom in some logic might be something like "If P, then P," where P can symbolize any sentence you might imagine. This seems at first blush like it is a statement that is always true. Here's an example of a sentence that takes that form:

        "If there is a red dog, then there is a red dog."
        
Even though the sentence is kind of boring and uninformative, it's hard to disagree with. I can't imagine any situation in which there would be a red dog, but there also wouldn't be a red dog. And I have the same feeling concerning each other sentence that I could come up with, which has this structure. 

Now, every logic has theorems. Theorems are simply further statements that you can get by applying a logic's vocabulary and rules for symbol combination to the logic's axioms (or to other theorems). And, on the flip side, a non-theorem is just a statement using the logic's vocabulary in an appropriate way, but which you cannot obtain by applying that logic's rules for symbol combination to the logic's axioms (or any further theorems). 

A model of a logic is like an interpretation of that logical system, a set of imaginary objects and relations between them that we can imagine in order to better understand and visualize how the logical system operates. 


```

8. Following up on the preceding , explain the _tree model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 

9. Open the Protege editor and create object properties for each of the role names that you constructed in question 1. You should have at least 6 object properties. Assert in the editor that P is a sub-property of O, that P is transitive, and that O is symmetric. Next, add individuals - a, b, c - to the file and assert that c is part of a and that c overlaps b. Running the reasoner should reveal - highlighted in yellow if you select the individual c - that c overlaps a. Using the discussion in the selections from chapter 4 of the Baader, et. al. text as a guide, explain how the tableau algorithm is generating this inference. Also, provide a screenshot of the results of your reasoner run with c highlighted. 

10. Following up on your work in question 9, adjust/add/remove/etc. object properties and individuals in your Protege file so that when you run a reasoner in Protege, you return the following consequences: 
```
  (a) a is a proper part of b and disjoint from e
  (b) a overlaps c
  (c) a is part of b, b is part of f, and a is part of f
  (e) There are no parts between a and g in common
```
Provide a screenshot of your results here. 
