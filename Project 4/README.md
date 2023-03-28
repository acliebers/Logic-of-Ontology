**The SPARQL Library of Buffalo**

[Codewars](https://www.codewars.com/dashboard) is a website designed to facilitate algorithmic training for various programming languages. Users supply problem statements and others provide coding solutions to those problems. For example, you might find a problem for Python such as: 

```
Define a function that returns the length of a given string. 
```

With a solution like: 

```
def length_of_string(s):
	return len(s)
```
	
Codewars is not limited to traditional programming languages like Python, but also facilitates training for languages like SQL. As you have learned, SQL and SPARQL are both query languages, but what might surprise you is that there is currently no option for training SPARQL in Codewars. This project will go some way to remedy that. 

For this project, you will be tasked with constructing SPARQL problems for the codewars site. 

```
Note #1: Completion of this task will not require you to actually have your SPARQL problems successfully posted to codewars. Adding problems to codewars takes more time than we have for this project. Additionally, you are only allowed to add propose problems to codewars if you have a certain amount of experience (specifically, you need 300 of what they call 'honor points', which is acquired by solving problems). At some point, assuming you permit it, I will post your problems to codewars (giving you credit of course). 
Note #2: The potential for this project to directly impact the ontology community is clear. SPARQL can be challenging, and there are few opportunities for drill practice like this. 
Note #3: You will not be required to learn a programming language, though you will likely need to expand your comfort with computer science jargon; if you hit a wall, ask your peers for help; if the wall persists, ask me. 
Note #4: Codewars provides a guidebook - https://docs.codewars.com/authoring/tutorials/create-first-kata/ - for creating problems; I strongly encourage you to read it, since the standard provided there is how I will be evaluating success. 
```
**Assignment Details**

Problems on Codewars are ranked in terms of difficulty. The lowest "kata" - 8 - indicates a rather easy problem, while the highest kata - 1 - indicates a very challenging problem. 

For our purposes, harder kata will be worth more points than easier kata, and you are required to submit enough kata to acquire 100 points according to the following point system: 

  |   **kata**    |  **points**   |
  | ------------- | ------------- |
  |       1       |      35       |
  |       2       |      25       |
  |       3       |      20       |
  |       4       |      10       |
  |       5       |       5       |
  |       6       |       3       |
  |       7       |       2       |
  |       8       |       0       |

You're probably thinking, "why would I submit a level 8 kata if they're not worth any points?" Great question. Because everyone had to submit at least one level 8 kata. Otherwise, you're permitted to submit kata in any distribution you choose. For example, you might submit 2 problems for kata one (70 points), one for kata 3 (20 points), one for kata 4 (10 points), and one for kata 8 (0 points but required). 

It is your responsibility and the responsibility of your peers reviewing your submission in PR to determine whether your submission is ranked appropriately. In the event that consensus is reached that your kata is ranked inappropriately, you must work with your peers to revise the submission so that it is either more or less challenging, accordingly. You are not permitted to submit new problems with different strengths after PRs are open, but must instead revise your PRs. So, think hard about how challenging your submission is. 

There is one other option for those desiring a different sort of challenge. If you provide alongside your SPARQL submission a translation of the same problem into SQL, complete with documentations, solution, etc. then you may receive half points extra at that kata level (rounded up). For example, if you submit a SPARQL problem that is kata rank 1 and also submit a SQL version of that same problem, you  will receive 35+18=53 points. 

1. What types are there? (8 Kyu)

	Write a query which returns each rdf:type used in an ontology. 
	
	example answer:
		
		SELECT ?t
		WHERE
		{ 
		?s rdf:type ?t
		}
		
2. How many classes are there? (7 kyu) 															2
	
	Write a query which returns the rdfs labels in an ontology, and the number of resources tagged with each label.
	
	Example answer:
	
		PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
		
		SELECT DISTINCT ?label (COUNT(?s) AS ?labelcount)
		WHERE
		{
		?s rdfs:label  ?label
		}
		GROUP BY ?label
		
3. How many artists died in 1973, according to DBPedia? (7 Kyu)												2

	Write a query for the DBPedia public endpoint which returns the names of all artists who died in 1973 C.E., in chronological order.
	
	Example answer:

		PREFIX rdf: <http://www.w3.org/2000/01/rdf-schema#>
		PREFIX dbo: <http://dbpedia.org/ontology/>

		SELECT ?artist							
		WHERE
		{
		?artist a dbo:Artist;
		dbo:deathDate ?date
		FILTER (regex( ?date, "1973"))
		}
		ORDER BY ?date
	
4. What is Edward Snowden's date of birth, according to DBPedia? (7 Kyu or 8 Kyu?)										2 or 1?

	Write a query for the DBPedia public endpoint which returns the date of birth for famed whistleblower Edward Snowden.
	
	Example answers:

		PREFIX dbo: <http://dbpedia.org/ontology/>

		SELECT ?bday
		WHERE
		{
		?snowden dbo:birthDate ?bday
		FILTER (regex( ?snowden, "Edward_Snowden"))
		}
		
				OR 
				
		
		PREFIX dbo: <http://dbpedia.org/ontology/>

		SELECT ?bday
		WHERE
		{
		<http://dbpedia.org/resource/Edward_Snowden/> dbo:birthDate ?bday
		}

5. Which individual does the most? (6 Kyu)   															3

	Write a query which returns an individual in an ontology which occupies the subject position in the most triples where object properties occupy the predicate 
	position, and the number of those relations in which the individual in question occupies the subject position. 
		
		Example answer: 
	
		PREFIX owl: <http://www.w3.org/2002/07/owl#>
		
		SELECT ?individual (MAX(?p) AS ?propcount)
		WHERE
		{
		?individal a owl:NamedIndividual;
		?p ?o .
		?p a owl:ObjectProperty .
		}
		GROUP BY ?individual
		LIMIT 1
		
		
6. What is the total ratio of classes to subclasses? (6 Kyu)													3  
	
	Write a query which returns 3 columns: The number of OWL classes in an ontology, the number of classes in that ontology which are subclasses of other classes, 
	and then a column which contains the ratio of classes to subclasses in that ontology. 
	
		Example answer: 
		
		PREFIX owl: <http://www.w3.org/2002/07/owl#>
		PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
		
		SELECT  (COUNT(?c) AS ?classes) (COUNT(?s) AS ?subclasses) (?classes / ?subclasses AS ?classsubratio)
		WHERE {
		?c a owl:Class .
		?o a owl:Class . 
		?s rdfs:subClassOf ?o;
		a owl:Class . 
		}
		
		
7. US President birthday and death day chart (7 Kyu)														1							

	Write a query for the DBpedia public endpoint which constructs a set of triples for every president of the United States in which the president takes the 
	subject position, dbo:birthDate takes the predicate position, and that president's birth date takes the object position.
	
		Example answer:
		
		PREFIX dbo: <http://dbpedia.org/ontology/>
		PREFIX dbc: <http://dbpedia.org/resource/Category:>
		
		CONSTRUCT {?president dbo:birthDate ?bday}
		WHERE 
		{
		?president dbo:wikiPageWikiLink dbc:Presidents_of_the_United_States;  
		dbo:birthDate ?bday .
		}
		
8. 
