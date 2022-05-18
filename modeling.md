---
layout: default
title: Modeling Snippets
---

[Catalog of Explanation Types](#explanationtypes) | [Modeling of Explanation Types](#modelingexplanations)

<article class="mb-5" id="modelingsnippets">
<content>
  
  
<h2 id="modelingabout">Explanation Types</h2>
  <p>In this section, we show how our <a href="#ontology">Explanation Ontology</a> can be used to represent the generational needs of <b>fifteen</b> different explanation types we identified from our literature review. For more details about our explanation types itself, refer to our paper submission. In this website we present modeling snippets that use classes and properties from our ontology.</p>
    
  <article class="mb-5" id="explanationtypes">
<content>
  
  
<h3>Catalog of Explanation Types</h3>
  <p>We identified nine explanation types, each with different foci and generational needs, from a literature review we conducted in the computer science and adjacent explanation science domains of philosophy and social sciences. Additionally, we also support six explanation types detailed in a recent paper, <a href="https://www.mdpi.com/1020146">Zhou et al</a>. Utilizing the schema provided by our explanation ontology, we can encode the generational needs of these explanation types as OWL restrictions. Below for each explanation type, we present our description, a prototypical question they can address in different settings (mainly clinical) and the logical formalization of the explanation type. The explanation types are:
  <table id="catalogexplanations">
    <th>Explanation Type</th>
    <tr><td><a href="#casebased">Case Based</a></td></tr>
    <tr><td><a href="#contextual">Contextual</a></td></tr>    
    <tr><td><a href="#contrastive">Contrastive</a></td></tr>
    <tr><td><a href="#counterfactual">Counterfactual</a></td></tr>
     <tr><td><a href="#data">Data</a></td></tr>
    <tr><td><a href="#everyday">Everyday</a></td></tr>
    <tr><td><a href="#fairness">Fairness</a></td></tr>
     <tr><td><a href="#impact">Impact</a></td></tr>
      <tr><td><a href="#rationale">Rationale</a></td></tr>
    <tr><td><a href="#responsibility">Responsibility</a></td></tr>
    <tr><td><a href="#safety">Safety and Performance</a></td></tr>
    <tr><td><a href="#scientific">Scientific</a></td></tr>
    <tr><td><a href="#simulationbased">Simulation Based</a></td></tr>
    <tr><td><a href="#statistical">Statistical</a></td></tr>
    <tr><td><a href="#tracebased">Trace Based</a></td></tr> 
    </table></p>
  
  <h3 id="modelingexplanations"> Explanation Types </h3>
  <p class="message">We depict logical formalization of our encoding of the generational needs for explanation type in <a href="https://www.w3.org/TR/owl2-manchester-syntax/">Manchester OWL syntax</a>, in that classes in the OWL restriction are referred to via their labels, and the color highlights are similar to those that can be viewed in Protege. These logical formalizations presented against the <strong>OWL restrictions</strong> label for each explanation type are a representation of the <strong>sufficiency conditions</strong> mentioned before the restrictions.</p>
 <ol>
  <li id="casebased">
<table><td><strong>Case Based Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong> Provides solutions that are based on actual prior cases that can be presented to the user to provide compelling support for the system’s conclusions, and may involve analogical reasoning, relying on similarities between features of the case and of the current situation. </li>
    <li><strong>Prototypical Question:</strong> To what other situations has this recommendation been applied? </li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there at least one other prior `case' similar to this situation that requires an `explanation'? <br/>Is there a similarity between this case, and that other case?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
     isBasedOn <span style="color:#bf399e">some</span> 
    (Explanation
     <span style="color:##39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span>
        ('System Recommendation'
         <span style="color:#39bfaf">and</span> (prov:wasGeneratedBy <span style="color:#bf399e">some</span>
            ('Artificial Intelligence Task'
             <span style="color:#39bfaf">and</span> ('has input' <span style="color:#bf399e">some</span> 'Object Record'))))))
      </pre></li>
  </ul>
  </li>

  <li id="contextual">
    <table><td><strong>Contextual Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>
  <ul type = "circle">
    <li> <strong>Definition:</strong> Refers to information about items other than the explicit inputs and output, such as information about the user, situation, and broader environment that affected the computation. </li>
    <li><strong>Prototypical Question:</strong> What broader information about the current situation prompted the suggestion of this recommendation?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Are there any other extra inputs that are not contained in the `situation' description itself? <br/> And by including those, can better insights be included in the `explanation'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
     (
     (isBasedOn <span style="color:#bf399e">some</span>  
    ('Contextual Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' some Situation))) 
     <span style="color:#39bfaf">or</span> 
     (isBasedOn <span style="color:#bf399e">some</span> ('Contextual Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  'Object Record'))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span>  'System Recommendation')
      </pre></li>
  </ul>
  </li>

  <li id="contrastive">
<table><td><strong>Contrastive Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong> Answers the question “Why this output instead of that output,” making a contrast between the given output and the facts that led to it (inputs and other considerations),  and an alternate output of interest and the foil (facts that would have led to it).</li>
    <li><strong>Prototypical Question:</strong> Why drug A over drug B the one I am typically prescribed?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a `system recommendation' that was made let’s call it A)? <br/> What `facts' led to it? <br/> Is there another `system recommendation' that could have happened or did occur, (let’s call it B)? <br/> What was the `foil that led to B? <br/> Can A and B be compared?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used some Fact)))
 <span style="color:#39bfaf">and</span> 
 (isBasedOn <span style="color:#bf399e">some</span>
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span> Foil)))
      </pre></li>
  </ul>
  </li>

   <li id="counterfactual">
<table><td><strong>Counterfactual Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Addresses the question of what solutions would have been obtained with a different set of inputs than those used.</li>
    <li><strong>Prototypical Question:</strong> What if input A was over 1000?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a different set of inputs that can be  considered? <br/> If so what is the alternate `system recommendation'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span> 
        (Knowledge
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> 'Object Record'))))
      </pre></li>
  </ul>
  </li>
   
    <li id="data">
<table><td><strong>Data Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong> Focuses on what the data is and how it has been used ina particular decision, as well as what data and how it hasbeen used to train and test the ML model. This type of ex-planation can help users understand the influence of dataon decisions.</li>
    <li><strong>Prototypical Question:</strong> What is the data?, How has the data been used in a particular decision?, How has the data been used to train the ML model?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that has as input, a ‘dataset’ or part of it? <br/> Is there a ‘system recommendation’ that includes ‘object records’ that are used to train / test the ‘AI method’?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span> 
        (Knowledge
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> 'Object Record'))))
      </pre></li>
  </ul>
  </li>

  <li id="everyday">
<table><td><strong>Everyday Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Uses accounts of the real world that appeal to the user, given their general understanding and knowledge.</li>
    <li><strong>Prototypical Question:</strong>Why does Option A make sense?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Can accounts of the real world be simplified to appeal to the user based on their general understanding and `knowledge'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>
   
   <li id="fairness">
<table><td><strong>Fairness Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Provides steps taken across the design and implementation of an ML system to ensure that the decisions it assistsare generally unbiased, and whether or not an individualhas been treated equitably. Fairness explanations are key to increasing individuals’ confidence in an AI system. It can foster meaningful trust by explaining to an individual how bias and discrimination in decisions are avoided.</li>
    <li><strong>Prototypical Question:</strong>Is there a bias consequence of this system recommendation? What data was used to arrive at this decision?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that has a ‘statement of consequence’? <br/> Is  there a ‘dataset’ in  the ‘system  recommendation’ the explanation is based on?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>
   
    <li id="impact">
<table><td><strong>Impact Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Concerns the impact that the use of a system and its de-cisions has or may have on an individual and on a wider society. Impact explanations give individuals some power and control over their involvement in ML-assisted decisions. By understanding the possible consequences of the decision, an individual can better assess their participation in the process and how the outcomes of the decision may affect them.</li>
    <li><strong>Prototypical Question:</strong>What is the impact of a system recommendation? How will the recommendation affect me?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that has a ‘statement of consequence’?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>
   
     <li id="rationale">
<table><td><strong>Rationale Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>About the “why” of an ML decision and provides reasonsthat led to a decision, and is delivered in an accessible and understandable  way, especially  for  lay  users.  If  the  ML decision was not what users expected, rationale explanations allows users to assess whether they believe the reasoning of the decision is flawed. While, if so, the explanation supports them to formulate reasonable arguments for why they think this is the case.</li>
    <li><strong>Prototypical Question:</strong>Why was this ML decision made and provides reasons that led to a decision</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that has a ‘system trace’? <br/> Is there a ‘local explanation’ output that an ‘explanation’ is based on?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>
   
    <li id="responsibility">
<table><td><strong>Responsibility Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Concerns “who” is involved in the development, manage-ment, and implementation of an ML system, and “who” to contact for a human review of a decision. Responsibility explanations help by directing the individual to the person or team responsible for a decision. It also makes accountability traceable.</li>
    <li><strong>Prototypical Question:</strong>Who  is  involved  in  the  development,  management, and implementation of an ML system?, Who to contact for a human review of a decision?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that was part of a ‘system’, whose ‘system developer’ is known?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>

   
    <li id="safety">
<table><td><strong>Safety and Performance Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Deals with steps taken across the design and implementation  of  an  ML  system  to  maximise  the  accuracy,  reli-ability,  security,  and  robustness  of  its  decisions  and  behaviours. Safety and performance explanations help to assure individuals that an ML system is safe and reliable by explanation to test and monitor the accuracy, reliability,security, and robustness of the ML model.</li>
    <li><strong>Prototypical Question:</strong>What steps were taken to ensure robustness and reliability of system?, How has the data been used totrain the ML model?, What steps were taken to ensure robustness and reliability of AI method?, What were the plans for the system development?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a ‘system recommendation’ from an ‘AI method’ that is part of a ‘system’ that exposes its design ‘plans’? <br/> Is there a ‘system recommendation’ that includes ‘object records’ that are used to train / test the ‘AI method’?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
((isBasedOn <span style="color:#bf399e">some</span>  
    (Situation
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (isBasedOn <span style="color:#bf399e">some</span>  
    ('Experential Knowledge'
     <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span>  User))))
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span>  
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> ((used <span style="color:#bf399e">some</span> 
        (Situation
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User))) <span style="color:#39bfaf">or</span> (used <span style="color:#bf399e">some</span>  
        ('Experential Knowledge'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> User)))))
)
      </pre></li>
  </ul>
  </li>
   
  <li id="scientific">
<table><td><strong>Scientific Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>References the results of rigorous scientific methods, observations, and measurements.</li>
    <li><strong>Prototypical Question:</strong> What studies have backed this recommendation?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Are there results of rigorous `scientific methods' to explain the situation? <br> Is there `evidence' from the literature to explain this `situation'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    (
(isBasedOn <span style="color:#bf399e">some</span> 'System Recommendation')
 and (isBasedOn <span style="color:#bf399e">some</span> 
    ('Scientific Knowledge'
     <span style="color:#39bfaf">and</span> ((wasGeneratedBy <span style="color:#bf399e">some</span> study) <span style="color:#39bfaf">or</span> (wasGeneratedBy <span style="color:#bf399e">some</span> 'Scientific Method'))))) 
<span style="color:#39bfaf">or</span>
(isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span> 
        ('Scientific Knowledge'
         <span style="color:#39bfaf">and</span> ((wasGeneratedBy some study) <span style="color:#39bfaf">or</span> (wasGeneratedBy <span style="color:#bf399e">some</span> 'Scientific Method')))))
)
      </pre></li>
  </ul>
  </li>

  <li id="simulationbased">
<table><td><strong>Simulation Based Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Uses an imagined or implemented imitation of a system or process and the results that emerge from similar inputs.</li>
    <li><strong>Prototypical Question:</strong> What would happened if this recommendation is followed?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there an `implemented' imitation of the `situation' at hand? <br> Does that other scenario have inputs similar to the current `situation'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
    isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (wasGeneratedBy <span style="color:#bf399e">some</span> 
        ('AI Task'
         <span style="color:#39bfaf">and</span> ('has input' <span style="color:#bf399e">some</span> 
            ('Object Record'
             and (hasSetting <span style="color:#bf399e">some</span> Situation))))))
      </pre></li>
  </ul>
  </li>

  <li id="statistical">
<table><td><strong>Statistical Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Presents an account of the outcome based on data about the occurrence of events under specified (e.g., experimental) conditions. Statistical explanations refer to numerical evidence on the likelihood of factors or processes influencing the result.</li>
    <li><strong>Prototypical Question:</strong> What percentage of people with this condition have recovered?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there `numerical evidence'/likelihood account of the `system recommendation' based on data about the occurrence of the outcome described in the recommendation?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
     isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span> 
        ('Numerical Evidence'
         <span style="color:#39bfaf">and</span> ('in relation to' <span style="color:#bf399e">some</span> 'Object Record'))))
      </pre></li>
  </ul>
  </li>

   <li id="tracebased">
<table><td><strong>Trace Based Explanation</strong></td><td style="text-align: right;"><a href="#catalogexplanations">Top</a></td></table>  <ul type = "circle">
    <li> <strong>Definition:</strong>Provides the underlying sequence of steps used by the system to arrive at a specific result, containing the line of reasoning per case and addressing the question of why and how the application did something.</li>
    <li><strong>Prototypical Question:</strong>What steps were taken by the system to generate this recommendation?</li>
    <li><strong>Sufficency Condition:</strong> <br/>Is there a record of the underlying sequence of steps (`system trace') used by the `system' to arrive at a specific `recommendation'?</li>
    <li> <strong>OWL Restriction:</strong> <br/>
      <pre>
     isBasedOn <span style="color:#bf399e">some</span> 
    ('System Recommendation'
     <span style="color:#39bfaf">and</span> (wasGeneratedBy <span style="color:#bf399e">some</span>  
        ('AI Task'
         <span style="color:#39bfaf">and</span> (used <span style="color:#bf399e">some</span>  
            (('Decision Tree' <span style="color:#39bfaf">or</span> 'Knowledge based Systems')
             <span style="color:#39bfaf">and</span> ('has output' <span style="color:#bf399e">some</span> 'System Trace'))))))
      </pre></li>
  </ul>
  </li>
</ol>
  <!--can cite our book chapter here-->
 </content>
 
 
