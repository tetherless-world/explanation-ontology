---
layout: default
title: Modeling Snippets
---

[Modeling of Explanation Types](#explanationtypes) | [A Clinical Example](#clinicalexample)

<article class="mb-5" id="modelingsnippets">
<content>
  
  
<h2 id="modelingabout">Modeling of Explanation Types and a Clinical Example</h2>
  <p>In this section, we show how our <a href="#ontology">Explanations Ontology</a> can be used to represent the generational needs of different explanation types we identified from our literature review as well as support generation of some examples of explanations we observed or encoded into our prototype AI system that we designed during our requirements gathering session with Duke clinicians. For more details about our requirements gathering sessions or the explanation types itself, refer to our paper submission. In this website we present modeling snippets that use classes and properties from our ontology.</p>
  
  <article class="mb-5" id="explanationtypes">
<content>
  
  
<h3>Modeling of Explanation Types</h3>
  <p>We identified nine explanation types, each with different foci and generational needs, from a literature review we conducted in the computer science and adjacent explanation science domains of philosophy and social sciences. The explanation types are; <a href="#casebased">case based</a>, <a href="#contextual">contextual</a>, <a href="#contrastive">contrastive</a>, <a href="#counterfactual">counterfactual</a>, <a href="#everyday">everyday</a>, scientific, simulation based, statistical and trace based. Utilizing the schema provided by our explanations ontology, we can encode the generational needs of these explanation types as OWL restrictions. Below for each explanation type, we present our description, a prototypical question they can address in a clinical setting and the logical formalization of the explanation type.</p>
  
  <h4> Explanation Types </h4>
  <p class="message">We depict logical formalization of our encoding of the generational needs for explanation type in <a href="https://www.w3.org/TR/owl2-manchester-syntax/">Manchester OWL syntax</a>, in that classes in the OWL restriction are referred to via their labels, and the color highlights are similar to those that can be viewed in Protege. These logical formalizations presented against the <strong>OWL restrictions</strong> label for each explanation type are a representation of the <strong>sufficiency conditions</strong> mentioned before the restrictions.</p>
 <ol>
  <li id="casebased">
<table><td><strong>Case Based Explanation</strong></td><td style="text-align: right;"><a href="#explanationtypes">Top</a></td></table>  <ul type = "circle">
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
    <table><td><strong>Contextual Explanation</strong></td><td style="text-align: right;"><a href="#explanationtypes">Top</a></td></table>
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
<table><td><strong>Contrastive Explanation</strong></td><td style="text-align: right;"><a href="#explanationtypes">Top</a></td></table>  <ul type = "circle">
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
<table><td><strong>Counterfactual Explanation</strong></td><td style="text-align: right;"><a href="#explanationtypes">Top</a></td></table>  <ul type = "circle">
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
<table><td><strong>Everyday Explanation</strong></td><td style="text-align: right;"><a href="#explanationtypes">Top</a></td></table>  <ul type = "circle">
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
 <span style="color:#39bfaf">and</span> (isBasedOn <span style="color:#bf399e">some</span>  'System Recommendation')) 
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
</ol>
  <!--can cite our book chapter here-->
 </content>
 
 <article class="mb-5" id="clinicalexample">
<content>
  
  
<h3>Example from Clinical Requirement Gatherings Session</h3>
  <p>We present an example of how our explanations ontology could be used to address a question, "Why Drug B over Drug A?" that clearly requires a contrastive explanation. Given that a contrastive explanation is the most suitable explanation type to address this question, our ontology if loaded into a system can help guide a system designer to locate the <strong>facts</strong> in support of Drug A and <strong>foil</strong> in support/against Drug B. While this is a real question that was asked by one of the clincians to a prototype decision support tool that we built to walk them through a complicated type-2 diabetes patient case, we omit the exact explanation as it is difficult to explain without the entire context of the patient case and the knowledge available to the system. Instead, we present an abstracted up example of a contrastive explanation in <a href="#fig2">Fig. 2</a>. In <a href="#fig3">Fig. 3</a>, we also show how our ontology would have inferred the explanation to be of a <strong>contrastive</strong> kind if the system had generated two recommendations one based on the facts supporting Drug A and one on the foil ruling out drug B.</p>
  
 <img src="../images/rdfviewerexample.png" style="width:100%; height:100%"/>  
  <caption id="fig2">Fig 2. A visual overview of the RDF representation of a contrastive explanation that addresses the question, "Why Drug B over A?"</caption>
  <br>
    <p>The RDF snippet can be browsed at and is available within our Github repository at : <a href="https://raw.githubusercontent.com/tetherless-world/explanation-ontology/master/annotations/contrastiveexp.rdf">https://raw.githubusercontent.com/tetherless-world/explanation-ontology/master/annotations/contrastiveexp.rdf</a></p>
  
  <br>
  <br>
<img src="../images/ProtegeSnapshot.png" style="width:100%; height:100%">  
  <caption id="fig3">Fig 3. A snapshot of classification results obtained by running <a href="https://github.com/stardog-union/pellet">Pellet reasoner</a> within <a href="https://protege.stanford.edu/">Protege</a> which depict how an explanation based on two system recommendations that were supported by a fact and foil respectively were inferred to be of a contrastive type. The reasoner leveraged the encoding of <a href="#explanationtypes">sufficiency conditions for each explanation type</a> that we support as OWL restrictions within our ontology.</caption>
  
 </content>
