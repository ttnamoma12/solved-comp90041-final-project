Download Link: https://assignmentchef.com/product/solved-comp90041-final-project
<br>
This is your final project for COMP90041. It is equivalent of a final exam and, therefore, counts 60% towards your final grade. Consequently, the total number of points you can collect by completing this final assessment is 60 points. The number of points available is listed for each Section. All the best!

<h1>Moral Machines</h1>

The idea of Moral Machines is based on the <em>Trolley Dilemma</em>, a fictional scenario presenting a decision maker with a moral dilemma: choosing ”the lesser of two evils”. The scenario entails an autonomous car whose brakes fail at a pedestrian crossing. As it is too late to relinquish control to the car’s passengers, the car needs to make a decision based on the facts available about the situation. Figure 1 shows an example scenario. In this project, you will create an <em>Ethical Engine</em>, a program designed to explore different scenarios, build an algorithm to decide between the life of the car’s passengers <em>vs. </em>the life of the pedestrians, audit your decision-making algorithm through simulations, and allow users of your program to judge the outcomes themselves.

<h1>1         Build an Ethical Engine</h1>

Go to <em>https://classroom.github.com/a/ZLuymdEg </em>and accept the final project assignment. For details on how to check out the repository, make sure to consult the Lab 3 Materials<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

Your program should consist of seven core classes:

<table width="601">

 <tbody>

  <tr>

   <td width="601">ethicalengine/ |– Persona.java|– Human.java|– Animal.java|– Scenario.java|__ ScenarioGenerator.javaAudit.java EthicalEngine.java welcome.ascii</td>

  </tr>

 </tbody>

</table>

You can create additional classes if needed. <em>EthicalEngine.java </em>contains the <em>main </em>function and coordinates the program flow. <em>Scenario.java </em>contains a list of passengers, a list of pedestrians, as well as additional scenario conditions, such as whether pedestrians are legally crossing at the traffic light. The decision-making algorithm is implemented as a <em>static </em>method with the name <em>decide(Scenario scenario) </em>in <em>EthicalEngine.java</em>. The <em>welcome.ascii </em>file contains a text message that needs to be imported by your program and printed to the console to introduce the user task (interactive mode). Start by implementing the classes <em>Persona.java</em>, <em>Human.java</em>, <em>Animal.java</em>, and <em>Scenario.java</em>. <em>SenarioGenerator.java </em>is explained in detail in Section 2 and <em>Audit.java </em>in Section 3.

Figure 1: Scenario example: a self-driving car approaches a pedestrian crossing but its breaks fail. Your algorithm needs to decide between two cases. <em>Left</em>: The car will continue ahead and drive through the crossing resulting in one elderly man, one pregnant woman, one boy, and one dog losing their lives. <em>Right: </em>The car will swerve and crash into a concrete barrier resulting in the death of its passengers: one women, one man, and one baby. Note that the pedestrians abide by the law as they are crossing on a green signal (image source: http://moralmachine.mit.edu/).

<strong>The classes </strong><em>Persona</em><strong>, </strong><em>Human</em><strong>, </strong><em>Animal</em><strong>, </strong><em>Scenario</em><strong>, and </strong><em>ScenarioGenerator </em><strong>must be part of the package </strong><em>ethicalengine</em><strong>. The classes </strong><em>Audit </em><strong>and </strong><em>EthicalEngine </em><strong>should not be within a package.</strong>

<h2>1.1         The Abstract Class <em>Persona</em></h2>

<em>Persona </em>is an <em>Abstract Class </em>from which all Persona types inherit. This base class should be implemented as depicted in Figure 2. The class further comprises two enumeration types:

<ol>

 <li><em>Gender </em>must include the types <em>FEMALE </em>and <em>MALE </em>as well as a default option <em>UNKNOWN</em>, but can also include more diverse options if you so choose.</li>

 <li><em>BodyType </em>includes the types <em>AVERAGE</em>, <em>ATHLETIC</em>, and <em>OVERWEIGHT </em>as well as a default option <em>UNSPECIFIED</em>.</li>

</ol>

The <em>Persona </em>Class should implement the constructors as depicted in Figure 2. Make sure the empty constructor initializes all attributes with appropriate default values.

Age should be treated as a <em>class invariant </em>for which the following statement always yields true: <em>age &gt;</em>= 0.

<h2>1.2         Classes Inheriting from <em>Persona.java</em></h2>

Create at least two concrete classes that directly inherit from the abstract class <em>Persona</em>:

<ol>

 <li><em>java</em>: scenarios are inhabited by people who exhibit a number of characteristics (e.g., age, gender, body type, profession etc.). In the scenarios, each human is either considered to be a passenger or a pedestrian. Only a human can be <em>you</em>.</li>

 <li><em>java</em>: animals are part of the environment we live in. People walk their pets so make sure your program accounts for these.</li>

</ol>

<table width="351">

 <tbody>

  <tr>

   <td width="351"><strong>Persona</strong></td>

  </tr>

  <tr>

   <td width="351">–  age: int–  gender: Gender–  bodyType: Bodytype</td>

  </tr>

  <tr>

   <td width="351">+ Persona()+ Persona(age: int, gender: Gender, bodyType: Bodytype)+ Persona(otherPersona: Persona)+ getAge(): int+ getGender(): Gender+ getBodyType(): Bodytype+ setAge(age: int)+ setGender(gender: Gender)+ setBodyType(bodyType: Bodytype)</td>

  </tr>

 </tbody>

</table>

Figure 2: UML Diagram for <em>Persona.java</em>

<strong>1.2.1            The Class </strong><em>Human.java</em>

This class represents a human in the scenarios. On top of its parent methods, the class <em>Human </em>must at least include the following public methods:

<ul>

 <li>the constructor <em>Human(int age, Profession profession, Gender gender, BodyType bodytype, boolean isPregnant)</em>.</li>

 <li>the copy constructor <em>Human(Human otherHuman)</em>.</li>

 <li><em>getAgeCategory()</em>: returns an enumeration value of the type <em>AgeCategory </em>depending on the Human’s age with one of the following values:

  <ul>

   <li><em>BABY </em>: a human with an age between 0 and 4.</li>

   <li><em>CHILD</em>: a human with an age between 5 and 16.</li>

   <li><em>ADULT</em>: a human with an age between 17 and 68.</li>

   <li><em>SENIOR</em>: a human with an age above 68.</li>

  </ul></li>

 <li>the public method <em>getProfession()</em>: returns an enumeration value of the type <em>Profession</em>, which must include the following values: <em>DOCTOR</em>, <em>CEO</em>, <em>CRIMINAL</em>, <em>HOMELESS</em>, <em>UNEMPLOYED</em>, or <em>NONE </em>(as default). Only ADULTs have professions, other age categories should return the default value <em>NONE</em>. Additionally, you are tasked with coming up with at least two more categories you deem feasible.</li>

 <li>the public method <em>isPregnant()</em>: returns a boolean indicating whether the human is pregnant. For all instances of <em>Human </em>whose gender is not <em>FEMALE </em>this should return <em>false</em>.</li>

 <li>the public method <em>setPregnant(boolean pregnant)</em>: sets the value returned by <em>isPregnant() while preventing invalid states, such as a pregnant male</em>.</li>

 <li><em>isYou()</em>: returns a boolean indicating whether the human is representative of the user, <em>g.</em>, you are one of the passengers in the car.</li>

 <li>the public method <em>setAsYou(boolean isYou)</em>: sets the value of whether the human is representative of the user.</li>

 <li>the public method <em>toString() </em>must output a human’s characteristics according to the format shown below.</li>

</ul>

Pregnancy should be treated as a <em>class invariant </em>for which the following statement always yields true: if the human’s gender is not female, the human cannot be pregnant. Also, only humans who belong to the age category <em>ADULT </em>have a profession.

The public method <em>toString() </em>must return the following <strong>output format </strong>when printed to the commandline:

[you] &lt;bodyType&gt; &lt;age category&gt; [profession] &lt;gender&gt; [pregnant]

Note that attributes in brackets [] should only be shown if they apply, <em>e.g.</em>, a baby does not have a profession so therefore the profession is not displayed. Here is an example:

athletic adult doctor female

or

average adult doctor female pregnant

Similarly, here is an example if the human is you:

you average baby male

Note that words are in lowercase and separated by single <em>spaces</em>. Age is ignored in the output.

<strong>1.2.2            The Class </strong><em>Animal.java</em>

This class represents animals in the scenarios. On top of its parent methods, the class <em>Animal </em>must include the following public methods:

<ul>

 <li>the constructor <em>Animal(String species)</em>.</li>

 <li>the copy constructor <em>Animal(Animal otherAnimal)</em>.</li>

 <li>the public method <em>getSpecies()</em>: returns a String indicating what type of species the animal represents.</li>

 <li>the public method <em>setSpecies(String species)</em>: sets the value returned by <em>getSpecies()</em>.</li>

 <li>the public method <em>isPet()</em>: returns a boolean value depending whether the animal is a pet or wild animal.</li>

 <li>the public method <em>setPet(Boolean isPet)</em>: sets the value returned by <em>isPet()</em>.</li>

 <li>the public method <em>toString() </em>must output a pet’s Personaistics according to the format shown below.</li>

</ul>

The public method <em>toString() </em>must return the following <strong>output format </strong>when printed to the commandline:

&lt;species&gt; [is pet]

Here is an example:

cat is pet

Here is another example where <em>isPet() </em>returns <em>false</em>:

bird

Note that words are in lowercase, separated by single <em>spaces</em>, and that gender, age, and bodyType are ignored in the output.

<h3><strong>1.3         The Class </strong>Scenario.java</h3>

This class contains all relevant information about a presented scenario, including the car’s passengers and the pedestrians on the street as well as whether the pedestrians are crossing legally.

Each scenario can have only one instance of <em>Human </em>for which <em>isYou() </em>returns true. The following public methods must be implemented:

<ul>

 <li>the constructor <em>Scenario(Persona[] passengers, Persona[] pedestrians, boolean isLegalCrossing)</em>: you can use Arrays or ArrayLists in your class, but you need to make sure this constructor takes a Human array as an argument.</li>

 <li>the public method <em>hasYouInCar()</em>: returns a boolean indicating whether you (the user) is in the car.</li>

 <li>the public method <em>hasYouInLane()</em>: returns a boolean indicating whether you (the user) are in the lane, <em>e.</em>, crossing the street.</li>

 <li>the public method <em>getPassengers()</em>: returns the cars’ passengers as a Persona[] array.</li>

 <li>the public method <em>getPedestrians()</em>: returns the pedestrians as a Persona[] array.</li>

 <li>the public method <em>isLegalCrossing()</em>: returns whether the pedestrians are legally crossing at the traffic light.</li>

 <li>the public method <em>setLegalCrossing(boolean isLegalCrossing)</em>: sets whether the pedestrians are legally crossing the street.</li>

 <li>the public method <em>getPassengerCount()</em>: returns the number of passengers in the car (in <em>int</em>).</li>

 <li>the public method <em>getPedestrianCount()</em>: returns the number of pedestrians on the street (in <em>int</em>).</li>

 <li>the public method <em>toString() </em>must output the scenario according to the format shown below.</li>

</ul>

The public method <em>toString() </em>must return the following <strong>output format </strong>when printed to the commandline:

<table width="601">

 <tbody>

  <tr>

   <td width="601">====================================== # Scenario======================================Legal Crossing: &lt;yes/no&gt;Passengers (&lt;getPassengerCount&gt;) – &lt;Persona.toString&gt; ..Pedestrians (&lt;getPedestrianCount&gt;) – &lt;Persona.toString&gt; ..</td>

  </tr>

 </tbody>

</table>

Here is an example for a legal crossing (green light):

======================================

# Scenario

======================================

Legal Crossing: yes

Passengers (4)

<ul>

 <li>cat is pet</li>

 <li>overweight child male</li>

 <li>average senior female</li>

 <li>athletic adult ceo female pregnant</li>

</ul>

Pedestrians (3)

<ul>

 <li>average baby male</li>

 <li>average adult doctor male</li>

 <li>overweight adult homeless female</li>

</ul>

Here is another example with you in the car and a (non-pregnant) women and pedestrians crossing the street at a red light (illegal crossing):

======================================

# Scenario

======================================

Legal Crossing: no

Passengers (2)

<ul>

 <li>you average baby male</li>

 <li>average adult criminal female</li>

</ul>

Pedestrians (2)

<ul>

 <li>average senior male</li>

 <li>average senior female</li>

</ul>

Note that a persona’s characteristics are written in lower case and separated by single <em>spaces</em>. Your output <strong>must match </strong>the output specifications.

<h3><strong>1.4          The Class </strong>EthicalEngine.java</h3>

This class holds the <em>main </em>method and manages your program execution. It takes care of program parameters (see Section 4) as well as user input (see Section 5).

This class also houses the <em>decide(scenario) </em>method, which implements the decision-making algorithm outputting either <em>PEDESTRIANS </em>or <em>PASSENGERS </em>depending on whom to save.

<strong>Decision Algorithm </strong>Your task is to implement the <em>public static </em>method <em>decide(Scenario scenario) </em>that either returns a value of the Enumeration type <em>Decision</em>, which is either <em>PEDESTRIANS </em>or <em>PASSENGERS</em>. Your code must choose whom to save for any scenario.

To make the decision, your algorithm needs to consider the characteristics of the personas involved as well as the situation. You can take any of the personas’ characteristics (age, body type, profession, pets, etc.) into account when making your decision, but you must base your decision on at least 5 characteristics– from the scenario itself (<em>e.g.</em>, whether it’s a legal crossing) or from the personas’ attributes. Note that there is no right or wrong in how you design your algorithm. Execution is what matters here so make sure your code meets the technical specifications. But you may want to think about the consequences of your algorithmic design choices.

<h1>2       Scenario Generator</h1>

The class <em>ScenarioGenerator.java </em>will be the basis of your simulation and shall be used to create a variety of scenarios. To guarantee a balanced set of scenarios, it is crucial to randomize as many elements as possible, including the number and characteristics of humans and animals involved in each scenario as well as the scenario itself.

To be able to properly test your scenarios and make sure your results can be replicated, you must apply <em>pseudorandomness</em>. Therefore, you need to familiarize yourself first with the class <em>java.util.random </em><a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> and especially with the function <em>setSeed(long seed)</em>.

<em>ScenarioGenerator.java </em>must, therefore, include the following methods:

<ul>

 <li>the empty constructor <em>ScenarioGenerator()</em>: this constructor should set the seed to a truly random number</li>

 <li>the constructor <em>ScenarioGenerator(long seed)</em>: this constructor sets the seed with a predefined value</li>

 <li>the constructor <em>ScenarioGenerator(long seed, int passengerCountMinimum, int passengerCountMaximum, int pedestrianCountMinimum, int pedestrianCountMaximum)</em>: this constructor sets the seed as well as the minimum and maximum number for both passengers and pedestrians with predefined values</li>

 <li>the public method <em>setPassengerCountMin(int min)</em>: sets the minimum number of car passengers for each scenario</li>

 <li>the public method <em>setPassengerCountMax(int max)</em>: sets the maximum number of car passengers for each scenario</li>

 <li>the public method <em>setPedestrianCountMin(int min)</em>: sets the minimum number of pedestrians for each scenario</li>

 <li>the public method <em>setPedestrianCountMax(int max)</em>: sets the maximum number of pedestrians for each scenario</li>

 <li>the public method <em>getRandomHuman() </em>which returns a newly created instance of <em>Human </em>with random age, gender, bodyType, profession, and state of pregnancy</li>

 <li>the public method <em>getRandomAnimal() </em>which returns a newly created instance of <em>Animal </em>with random age, gender, body type, species, and whether it is a pet or not</li>

 <li>the public method <em>generate() </em>which returns a newly created instance of <em>Scenario </em>containing a random number of passengers and pedestrians with random characteristics as well as a randomly red or green light condition with you (the user) being either in the car, on the street, or absent.</li>

</ul>

The method <em>generate() </em>will need to abide by the minimum and maximum counts previously set for passengers and pedestrians in the scenario. If these values have not been explicitly set they need to be implicitly (<em>i.e., </em>by default) set to 1 and 5 respectively. A minimum may never be larger than its corresponding maximum.

<h1>3         Audit your Algorithm</h1>

An audit is an inspection of your algorithm with the goal of revealing inherent biases that may be built in as an (un)intended consequence. In this task, you will simulate a variety of scenarios and have your <em>EthicalEngine </em>decide on their outcomes. The class <em>Audit.java </em>should:

<ol>

 <li>create a specific number of random scenarios,</li>

 <li>allow your <em>EthicalEngine </em>to decide on each outcome,</li>

 <li>and summarize the results for each characteristic in a so-called <em>statistic of projected survival</em>.</li>

</ol>

The following methods must, therefore, be implemented:

<ul>

 <li>the empty constructor <em>Audit()</em></li>

 <li>the public method <em>run(int runs)</em>: runs the simulation by creating <em>N </em>= <em>runs </em>scenarios and running each scenario through the <em>EthicalEngine </em>using its <em>decide(Scenario scenario) </em> For each scenario you need to save the outcome and add the result to your statistic</li>

 <li>the public method <em>setAuditType(String name)</em>: sets the name of the audit type. For example: <em>Algorithm </em>for an audit of your algorithm.</li>

 <li>the public method <em>getAuditType()</em>: returns the name of the audit. Default should be <em>Unspecified</em>.</li>

 <li>the public method <em>toString()</em>: returns a summary of the simulation in the format depicted below. If no simulation has been run, this method returns ”no audit available”.</li>

 <li>the public method <em>printStatistic()</em>: prints the summary returned by the <em>toString() </em>method to the command-line.</li>

</ul>

<h2>3.1        Statistic of Projected Survival</h2>

Your statistic should list a number of factors, including:

<ul>

 <li>age category</li>

 <li>gender</li>

 <li>body type</li>

 <li>profession</li>

 <li>pregnant</li>

 <li>class type (human or animal)</li>

 <li>species</li>

 <li>pets</li>

 <li>legality (red or green light)</li>

 <li>pedestrian or passenger</li>

</ul>

Your statistic should account for each value of each respective characteristic, that are present in the given scenarios. For example, if you had scenarios with overweight body types, <em>overweight </em>must be listed in the statistic. If none of your scenarios included this particular body type, it must not be listed there. Also, make sure that you only update the statistic for, let’s say <em>cats</em>, if a cat was present in the tested scenario. If there is no cat in a given scenario, you must not change the % of cats that survived in your audit. Here is an example of how the statistic for cats is calculated:

where <em>C </em>is the number of cat survivors and <em>N<sub>c </sub></em>the total number of cats in scenarios. Here is another example for body types:

where <em>B </em>represents the number of humans with body type <em>b </em>and <em>N<sub>b </sub></em>represents the total number of body types <em>b </em>occurring in all the scenarios. You will need to construct the corresponding formulas for the remaining characteristics yourself. The test outputs will give you some hints.

The default values unknown (gender), unspecified (body type), and none (profession) should not be listed in the statistic. Further, the following characteristics should only make it into the statistic if they are related to a human:

<ul>

 <li>age category</li>

 <li>gender</li>

 <li>body type</li>

 <li>profession</li>

 <li>pregnant</li>

</ul>

Animals are not represented in the statistic of these characteristics. Animals should only be counted for the following:

<ul>

 <li>class type (human or animal)</li>

 <li>species</li>

 <li>pets</li>

 <li>legality (red or green light)</li>

 <li>pedestrian or passenger</li>

</ul>

This is the <em>output format </em>(with pseudocode) of the statistic:

<table width="601">

 <tbody>

  <tr>

   <td width="601">====================================== # &lt;auditType&gt; Audit======================================– % SAVED AFTER &lt;int run&gt; RUNS &lt;for each characterstic:&gt;&lt;characterstic&gt;: &lt;survival ratio&gt;-average age: &lt;average&gt;</td>

  </tr>

 </tbody>

</table>

Here is an example output for running the <em>config.csv </em>(note that your algorithm may make different decisions and thus lead to a different statistic):

<table width="601">

 <tbody>

  <tr>

   <td width="601">====================================== # Algorithm Audit======================================– % SAVED AFTER 2 RUNS animal: 1.00 bird: 1.00 cat: 1.00 ceo: 1.00 child: 1.00 dog: 1.00 pedestrians: 1.00 pet: 1.00 senior: 1.00 athletic: 0.67 red: 0.67 male: 0.60 green: 0.58 average: 0.50 baby: 0.50 doctor: 0.50 human: 0.50 pregnant: 0.50 female: 0.40 adult: 0.34 criminal: 0.00 overweight: 0.00 passengers: 0.00 unemployed: 0.00 you: 0.00 -average age: 30.40</td>

  </tr>

 </tbody>

</table>

The list of characteristics must be sorted in descending order of the survival ratio. All ratios are displayed with two digits after the decimal place (<em>round up </em>to the second decimal). If there is a tie, make sure to continue sorting in alphabetical order. Note that the last two lines are not part of the sorted statistic but are at a fixed position in the output. The average age is calculated across all survivors of class <em>Human </em>(animals are excluded) and rounded in the same way.

<strong>3.1.1             Update your Statistic within an Audit</strong>

If you run multiple scenarios within a particular audit, make sure to update your statistic rather than overwrite it. For example, you may run an audit subsequently over 10 (<em>audit.run(10)</em>), 50 (<em>audit.run(50)</em>), and 100 (<em>audit.run(100)</em>) scenarios and print an updated statistic after each run to the command-line. The result on the command-line should be three statistic outputs: the first with 10, the second with 60, and the last with 160 runs.

<h2>3.2       Save your Audit Results</h2>

To save the results of your audit to a file, add the public method <em>printToFile(String filepath) </em>to your <em>Audit </em>class. The method prints the results of the <em>toString() </em>method to a target file specified by the <em>filepath </em>variable. The <em>filepath </em>value (<em>e.g.</em>, ’logs/results.log’) is set by the command-line flag −<em>r </em>or −− <em>results </em>and includes both the target directory (<em>logs/</em>, in this case) and the filename (<em>results.log</em>). If <em>results.log </em>already exists in the target directory, you should <em>append </em>the new data rather than overwrite the existing file. If the file does not exist, your program should create it. If the directory specified by the <em>filepath </em>variable does not exist, your program should print the following error message to the command-line and terminate:

ERROR: could not print results. Target directory does not exist.

If the <em>filepath </em>variable is not set by the command-line flag, your program must print the results of algorithm audits by default to the <em>’results.log’ </em>file in the default directory. The results must be saved in ASCII code, <em>i.e.</em>, human-readable.

<h1>4          Import Scenarios from a Configuration File (10 points)</h1>

Instead of generating scenarios solely randomly, you need to make sure in this task that your program can import scenarios from a data file. This will allow you to run audits on a consistent set of scenarios. In this task, you need to extend your <em>EthicalEngine </em>class to allow it to create scenarios based on data it reads from a configuration file.

<h2>4.1          Specify the Configuration File as Command-Line Argument</h2>

The config file should be specified when your program is launched. In this task, you need to create a command-line option. Command-line options or so-called <em>flags </em>specify options that modify the operation of your program. Options follow the program execution command on the command-line, separated by spaces. Options can be specified <em>in any order</em>. The following program calls are equivalent and should be supported by your program:

$ java EthicalEngine –config path/to/config.csv and $ java EthicalEngine -c path/to/config.csv

The command line argument following the flag −−<em>config </em>or −<em>c </em>respectively specifies the filepath where the configuration file (<em>config.csv</em>) is located. Your program should check whether the file is located at the specified location and handle a <strong>FileNotFoundException </strong>in case the file does not exist. In this case, your program should terminate with the following error message:

ERROR: could not find config file.

<strong>Default behaviour: </strong>If your program is run without specifying a config file (and without indicating the interactive mode), your program should run an algorithm audit with 100 truly, randomly generated scenarios writing its results to <em>results.log </em>in the default folder.

<h2>4.2       Parsing the Configuration File</h2>

Next, your program needs to read in the config file. Table 1 lists the contents of <em>config.csv</em>, a so-called <strong>comma-separated values </strong>(CSV) file. The file contains a list of values, each separated by a comma. As can be seen in Table 1, the first line contains the headers, <em>i.e.</em>, the names (and description) of each data field and can therefore be ignored by your program. Each subsequent row presents an instance of <em>Persona</em>. Scenarios are preceded by a single line that starts with <em>scenario: </em>and indicates whether the scenario depicts a legal (green) or illegal (red) crossing. In this case, the first scenario describes a legal crossing

scenario:green

with 3 passengers and 4 pedestrians (one of which is a dog). In fact, the first data set describes the scenario depicted in Figure 1. The second scenario describes an illegal crossing with 4 pedestrians (2 animals) and 2 car passengers.

Your <em>EthicalEngine </em>class needs to be able to read in a config file as depicted in Table 1 and create a <em>Scenario </em>instance for each scenario the file contains. Note that a config file can contain any number of scenarios with any number of passengers and pedestrians. You can assume that all config files follow the same format with the columns ordered as shown in Table 1.

<h2>4.3       Handle Invalid Data Rows</h2>

While reading in the config file line by line your program may encounter three types of exceptions, which your program should be able to handle:

<ol>

 <li>Invalid number of data fields per row: in case the number of values in one row is less than or exceeds10 values a <strong>InvalidDataFormatException </strong>should be thrown. Your program should handle such exceptions by issuing the warning statement ”WARNING: invalid data format in config file in line <em>&lt; linecount &gt;</em>” to the command-line and skip the respective row then continue reading in the next line.</li>

 <li>Invalid data type: in case the value can not be casted into an existing data type (<em>g.</em>, a character where an int should be for age) a <strong>NumberFormatException </strong>should be thrown. Your program should handle such exceptions by issuing the warning statement ”WARNING: invalid number format in config file in line <em>&lt; linecount &gt;</em>” to the command-line, assign a default value instead, and continue with the next value in that line.</li>

 <li>Invalid field values: in case your program does not accommodate a specific value (<em>g.</em>, skinny as a bodyType) an <strong>InvalidCharacteristicException </strong>should be thrown. Your program should handle such exceptions by issuing a warning statement ”WARNING: invalid characteristic in config file in line <em>&lt; linecount &gt;</em>” to the command-line, assign a default value instead, and continue with the next value in that line.</li>

</ol>

Note that <em>&lt; linecount &gt; </em>depicts the line number in the config file where the error was found. While you can import the <em>NumberFormatException </em>from the package <em>java.lang </em>you will need to create custom exceptions for the other two.

config

<table width="444">

 <tbody>

  <tr>

   <td width="71"><strong>class</strong></td>

   <td width="37"><strong>gender</strong></td>

   <td width="23"><strong>age</strong></td>

   <td width="51"><strong>bodyType</strong></td>

   <td width="57"><strong>profession</strong></td>

   <td width="46"><strong>pregnant</strong></td>

   <td width="35"><strong>isYou</strong></td>

   <td width="40"><strong>species</strong></td>

   <td width="35"><strong>isPet</strong></td>

   <td width="50"><strong>role</strong></td>

  </tr>

  <tr>

   <td width="71"><strong>scenario:green</strong></td>

   <td width="37"> </td>

   <td width="23"> </td>

   <td width="51"> </td>

   <td width="57"> </td>

   <td width="46"> </td>

   <td width="35"> </td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50"> </td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">female</td>

   <td width="23">24</td>

   <td width="51">average</td>

   <td width="57">doctor</td>

   <td width="46">FALSE</td>

   <td width="35">TRUE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">passenger</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">male</td>

   <td width="23">40</td>

   <td width="51">overweight</td>

   <td width="57">unemployed</td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">passenger</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">female</td>

   <td width="23">2</td>

   <td width="51">average</td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">passenger</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">male</td>

   <td width="23">82</td>

   <td width="51">average</td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">female</td>

   <td width="23">32</td>

   <td width="51">average</td>

   <td width="57">ceo</td>

   <td width="46">TRUE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">male</td>

   <td width="23">7</td>

   <td width="51">athletic</td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>animal</strong></td>

   <td width="37">male</td>

   <td width="23">4</td>

   <td width="51"> </td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40">dog</td>

   <td width="35">TRUE</td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>scenario:red</strong></td>

   <td width="37"> </td>

   <td width="23"> </td>

   <td width="51"> </td>

   <td width="57"> </td>

   <td width="46"> </td>

   <td width="35"> </td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50"> </td>

  </tr>

  <tr>

   <td width="71"><strong>animal</strong></td>

   <td width="37">female</td>

   <td width="23">4</td>

   <td width="51"> </td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40">cat</td>

   <td width="35">TRUE</td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>animal</strong></td>

   <td width="37">female</td>

   <td width="23">2</td>

   <td width="51"> </td>

   <td width="57"> </td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40">bird</td>

   <td width="35">FALSE</td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">female</td>

   <td width="23">30</td>

   <td width="51">athletic</td>

   <td width="57">doctor</td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">male</td>

   <td width="23">1</td>

   <td width="51">average</td>

   <td width="57">homeless</td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">pedestrian</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">female</td>

   <td width="23">32</td>

   <td width="51">average</td>

   <td width="57"> </td>

   <td width="46">TRUE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">passenger</td>

  </tr>

  <tr>

   <td width="71"><strong>human</strong></td>

   <td width="37">male</td>

   <td width="23">40</td>

   <td width="51">athletic</td>

   <td width="57">criminal</td>

   <td width="46">FALSE</td>

   <td width="35">FALSE</td>

   <td width="40"> </td>

   <td width="35"> </td>

   <td width="50">passenger</td>

  </tr>

 </tbody>

</table>

Table 1: Contents of the configuration file (<em>config.csv</em>).

<h2>4.4           Audit your Algorithm Using the Scenarios from the Config File</h2>

Once your program has imported all scenarios from <em>config.csv </em>it should create a new <em>Audit</em>. Therefore, you need to extend your <em>Audit </em>class by adding two more methods:

<ul>

 <li>the constructor <em>Audit(Scenario[] scenarios)</em>: this constructor creates a new instance with a fixed set of scenarios.</li>

 <li>the public method <em>run()</em>: runs the simulation with the scenarios specified and runs each scenario through the <em>EthicalEngine </em>using its <em>decide(Scenario scenario) </em></li>

</ul>

Use the <em>printToFile(String path) </em>method to show the results of your audit on the console-line as well as save your audit results to <em>’results.log’ </em>or whatever is specified as a target <em>filepath </em>by the command-line flag −<em>r </em>(or −− <em>results</em>). The program should terminate after showing the statistic.

<h1>5       Interactive Scenarios (10 points)</h1>

Now it is time to let the user take over and be the judge. Therefore, you need to build an interactive console program, which presents the user with a number of ethical scenarios. These scenarios can either be randomly generated or imported from a config file. For each scenario the user is asked to make a decision about who should survive. The results are logged to a user file (<em>user.log</em>) but only if the user consents to it.

<h2>5.1      Program Setup</h2>

As described in Section 4.1, we will use command-line options or so-called <em>flags </em>to initialize the execution of <em>EthicalEngines</em>. Therefore, you should add a few more options as possible command-line arguments. Print Help Make sure your program provides a help documentation to tell users how to correctly call and execute your program. The help is a printout on the console telling users about each option that your program supports.

The following program call should invoke the help:

$ java EthicalEngine –help and $ java EthicalEngine -h

The command-line output following the invocation of the help should look like this:

<table width="601">

 <tbody>

  <tr>

   <td width="601">EthicalEngine – COMP90041 – Final ProjectUsage: java EthicalEngine [arguments]Arguments:-c or –config                               Optional: path to config file-h or –help                                    Print Help (this message) and exit-r or –results                                Optional: path to results log file-i or –interactive Optional: launches interactive mode</td>

  </tr>

 </tbody>

</table>

The help should be displayed when the −−<em>help </em>or −<em>h </em>flag is set or if the −−<em>config </em>flag is set without an argument (<em>i.e.</em>, no path is provided). If the −− <em>config </em>or −<em>c </em>flag is not set, your program should generate random scenarios. The flag −−<em>interactive </em>or −<em>i </em>indicates the interactive user mode. Without this flag the audit from Section 3 should kick in. Only if the −− <em>interactive </em>or −<em>i </em>is set the program launches its interactive scenarios. The flag −−<em>results </em>or −<em>r </em>indicates the path and filename where the results of your audit should be saved to. See Section 3.2 for details.

The following command will launch the program with a config file in the interactive mode:

$ java EthicalEngine -i -c config.csv

Here is an example of launching the program in the interactive mode with random scenarios:

$ java EthicalEngine -i

<h2>5.2      Program Execution</h2>

You need to extend the <em>EthicalEngine </em>class to manage the user interaction and support the following program flow: show a welcome message, collect user consent for data collection, present 3 scenarios and have user judge these, show the statistic, and ask for another round of scenarios.

<strong>5.2.1         Show Welcome Screen</strong>

At the start of the program, a welcome message must be shown: your program should read in and display the contents of <em>welcome.ascii </em>to the user without modifying it. The message provides background information about Moral Machines and walks the user through the program flow.

Next, your program should collect the user’s consent before saving any results. Explicit consent is crucial to make sure users are aware of any type of data collection. Your program should, therefore, ask for explicit user consent before logging any user responses to a file. After the welcome message, you program should therefore prompt the user with the following method on the command-line:

Do you consent to have your decisions saved to a file? (yes/no)

Only if the user confirms (<em>yes</em>), your program should save the user statistic to <em>’user.log’ </em>(in the default folder). If the user selects <em>no </em>your program should function normally but not write any of the users’ decisions to the file (it should still display the statistic on the command-line though). If the user types in anything other than <em>yes </em>or <em>no</em>, an <strong>InvalidInputException </strong>should be thrown and the user should be prompted again:

Invalid response. Do you consent to have your decisions saved to a file? (yes/no)

<strong>5.2.2        Present Scenarios</strong>

Once the user consented (or not), the scenario judging begins. Therefore, scenarios are either imported from the config file or (if the config file is not specified) randomly generated. Therefore, you should use the <em>Audit </em>class to keep track of the scenarios and decisions. Make sure to set the audit type to <em>User </em>using the method <em>setAuditType(String name). </em>Scenarios are presented one by one using the <em>toString() </em>method of the <em>Scenario </em>instance and printing its outputs to the command-line. Each scenario should be followed by a prompt saying:

Who should be saved? (passenger(s) [1] or pedestrian(s) [2])

Any of the following user inputs should be considered saving the passengers:

<ul>

 <li>passenger</li>

 <li>passengers</li>

 <li>1</li>

</ul>

Any of the these user inputs should be considered saving the pedestrians:

<ul>

 <li>pedestrian</li>

 <li>pedestrians</li>

 <li>2</li>

</ul>

After the user made a decision, the next scenario is shown followed by the prompt to judge the scenario. This procedure should repeat until 3 scenarios have been shown and judged. After the third scenario decision, the result statistic is presented.

<strong>5.2.3         Show the Statistic</strong>

The statistic must be printed to the command-line using the same method and format as described in Section 3.1. If the user previously consented to the data collection, the statistic is saved (<em>i.e., </em>appended) to the file <em>user.log </em>using the function <em>printToFile(String filepath) </em>of the <em>Audit </em>class. Additionally, the user should be prompted to either continue or quit the program as follows:

Would you like to continue? (yes/no)

Should the user choose <em>no </em>the program terminates after the following prompt:

That’s all. Press Enter to quit.

As soon as the Enter key is pressed, the program should terminate. If the user decides to continue (<em>yes</em>), the next three scenarios should be shown. If the config file does not contain any more scenarios, the final statistic should be shown followed by the exit prompt (see above).

Here is an example of a statistic followed by a prompt to continue:

<table width="601">

 <tbody>

  <tr>

   <td width="601">====================================== # User Audit======================================– % SAVED AFTER 3 RUNS cat: 1.00 pregnant: 1.00 you: 1.00 senior: 0.67 student: 0.67 passengers: 0.60 female: 0.50</td>

  </tr>

  <tr>

   <td width="601">pet: 0.50 average: 0.37 animal: 0.34 adult: 0.29 green: 0.28 human: 0.27 male: 0.24 pedestrians: 0.16 athletic: 0.00 ceo: 0.00 child: 0.00 criminal: 0.00 dog: 0.00 homeless: 0.00 overweight: 0.00 unemployed: 0.00—average age: 67.25That’s all. Press Enter to quit.</td>

  </tr>

 </tbody>

</table>

And that’s it. Almost.

<h1>6       Documentation (5 points)</h1>

Always make sure to document your code in general. For this project you need to provide two types of documentation for your program: a UML diagram depicting your overall architecture and make sure to use JavaDoc syntax so that you can create an automatic Java code documentation in HTML. Only your UML diagram needs to be submitted through Canvas. You do not need to submit your documentation created through JavaDoc. This will be created automatically.

<h2>6.1       UML Diagram</h2>

Prepare a UML diagram describing your entire program containing all classes, their attributes (including modifiers), methods, associations, and dependencies. For each class you need to identify all its instance variables and methods (including modifiers) along with their corresponding data types and list of parameters. You should also identify relationships between classes, including associations, multiplicity, and dependencies. Static classes must be included in the UML. You can leave out any helper function that you added.

Make sure to save your UML diagram in PDF format and add it to your Github repository’s root directory as <em>UML.pdf</em>.

<h2>6.2     Javadoc</h2>

Make sure all your classes indicate their author and general description. For each constructor and method specified in the final project description you must provide at least the following tags:

<ul>

 <li>@param tags</li>

 <li>@returns tag</li>

 <li>@throws tag</li>

</ul>

You can leave minor helper function that you may have added. Make sure to test the correct generation of your documentation using javadoc<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a>.

For the submission, you do not need to generate and the javadoc to your Github repository. For marking, we will create the javadoc programmatically from your code.

<h1>7       Reflection (Bonus Task)</h1>

This optional task gives you the opportunity to reflect on and describe the reasons you applied when designing your program’s decision-making as well as the consequences revealed by auditing your algorithm. For example, what were inherent biases you might have become aware by running this simulation? Were there any surprises? What are the consequences of design choices that you take as a programmer in general? Please make sure to stay below 250 words.

This part is optional but allows you to score an <strong>additional 2 points </strong>you may have lost somewhere else. Note that you cannot exceed the total of 60 points for the entire project. But we would love to read about your thoughts.

<h1>8       Testing Before Submission</h1>

You will find two types of local tests available: 1) an invocation test with some basic assertions and 2) a program input/output test. The tests along with the sample input, configuration files, and the expected output can be found in the template repository along with more detailed instructions on how to run them.

<h2>8.1      Test Runner</h2>

In the repository, you will find a Java file called <em>TestRunner.java</em>. It comprises a range of methods to instantiate and invoke the basic functionality of your code. You can run it as follows:

javac TestRunner.java &amp;&amp; java TestRunnner

While the main functionality of your code is still missing, these tests will lead to a range of compile errors. We recommend you to first finish your project code and then start debugging using these tests. Once you have addressed all compile errors (<strong>don’t change the tests, change your code</strong>), the test runner will launch a series of comparisons between your program’s and the expected output. These tests will be the basis for the automated grading of your project, so make sure to pass them as well as you can. Passing them, however, does not guarantee the completeness of your program. You will need to thoroughly test your program beyond what these tests provide.

<h2>8.2        Scenario Import and Interactive Mode Test</h2>

To further test your program you will find a range of test inputs for your program in the repository. To run the interactive mode test, follow these steps:

<ol>

 <li>Check your Java code files and make sure you have the test input data files ready in your <em>tests </em> in_interactive_config_3 provides user input (interactive mode) if you run your program with the config_3.csv file.</li>

 <li>Open a console, navigate to your project directory (where your .java classes reside), and compileyour program: javac *.java. This command will compile all your java file in the current folder.</li>

 <li>Run your program with the following command-line parameters:</li>

</ol>

java EthicalEngine -i -c tests/config_3.csv &lt; tests/in_interactive_config_3 &gt; output

This command will run the EthicalEngine main method in interactive mode with user input described in ‘in_interactive_config_3” as input and write the output to a file called output)

<ol start="4">

 <li>Inspect the file output as it may contain any errors your program execution may have encountered.</li>

 <li>Compare your result with the provided output file out_interactive_config_3. Fix your code if they are different.</li>

</ol>

It is crucial that <strong>your output follows exactly the same format shown in the examples in this document.</strong>

<strong>NOTE: </strong>The test cases used to mark your submissions will be different from the sample tests given. You should test your program extensively to <strong>ensure it is correct for other input values </strong>with the same format as the sample tests.

<a href="#_ftnref1" name="_ftn1">[1]</a> https://canvas.lms.unimelb.edu.au/courses/1507/assignments/138029

<a href="#_ftnref2" name="_ftn2">[2]</a> https://docs.oracle.com/javase/8/docs/api/java/util/Random.html

<a href="#_ftnref3" name="_ftn3">[3]</a> https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html