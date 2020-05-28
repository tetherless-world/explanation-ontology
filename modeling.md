---
layout: default
title: Modeling Snippets
---

[Catalog of Explanation Types](#explanationtypes) | [Modeling of Explanation Types](#modelingexplanations)

<article class="mb-5" id="modelingsnippets">
<content>
  
  
<h2 id="modelingabout">Explanation Types</h2>
  <p>In this section, we show how our <a href="#ontology">Explanation Ontology</a> can be used to represent the generational needs of different explanation types we identified from our literature review. For more details about our explanation types itself, refer to our paper submission. In this website we present modeling snippets that use classes and properties from our ontology.</p>
    
  <article class="mb-5" id="explanationtypes">
<content>
  
  
<h3>Catalog of Explanation Types</h3>
  <p>We identified nine explanation types, each with different foci and generational needs, from a literature review we conducted in the computer science and adjacent explanation science domains of philosophy and social sciences. Utilizing the schema provided by our explanations ontology, we can encode the generational needs of these explanation types as OWL restrictions. Below for each explanation type, we present our description, a prototypical question they can address in a clinical setting and the logical formalization of the explanation type. The explanation types are:
  <table id="catalogexplanations">
    <th>Explanation Type</th>
    <tr><td><a href="#casebased">Case Based</a></td></tr>
    <tr><td><a href="#contextual">Contextual</a></td></tr>
    <tr><td><a href="#contrastive">Contrastive</a></td></tr>
    <tr><td><a href="#counterfactual">Counterfactual</a></td></tr>
    <tr><td><a href="#everyday">Everyday</a></td></tr>
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
 
 
