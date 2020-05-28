---
layout: default
title: Clinical Example
---

<article class="mb-5" id="clinicalexample">
<content>
  
  
<h3>Example from Clinical Requirement Gatherings Session</h3>
  <p>We present an example of how our explanations ontology could be used to address a question, "Why Drug B over Drug A?" that clearly requires a contrastive explanation. Given that a contrastive explanation is the most suitable explanation type to address this question, our ontology if loaded into a system can help guide a system designer to locate the <strong>facts</strong> in support of Drug A and <strong>foil</strong> in support/against Drug B. While this is a real question that was asked by one of the clincians to a prototype decision support tool that we built to walk them through a complicated type-2 diabetes patient case, we omit the exact explanation as it is difficult to explain without the entire context of the patient case and the knowledge available to the system. Instead, we present an abstracted up example of a contrastive explanation in <a href="#fig2">Fig. 2</a>. </p>
  <!--In <a href="#fig3">Fig. 3</a>, we also show how our ontology would have inferred the explanation to be of a <strong>contrastive</strong> kind if the system had generated two recommendations one based on the facts supporting Drug A and one on the foil ruling out drug B.-->
  
 <img src="../images/rdfviewerexample.png" style="width:100%; height:100%"/>  
  <caption id="fig2">Fig 2. A visual overview of the RDF representation of a contrastive explanation that addresses the question, "Why Drug B over A?"</caption>
  <br>
    <p>The RDF snippet can be browsed at and is available within our Github repository at : <a href="https://raw.githubusercontent.com/tetherless-world/explanation-ontology/master/annotations/contrastiveexp.rdf">https://raw.githubusercontent.com/tetherless-world/explanation-ontology/master/annotations/contrastiveexp.rdf</a></p>
  
  <br>
<!--<img src="../images/ProtegeSnapshot.png" style="width:100%; height:100%">  
  <caption id="fig3">Fig 3. A snapshot of classification results obtained by running <a href="https://github.com/stardog-union/pellet">Pellet reasoner</a> within <a href="https://protege.stanford.edu/">Protege</a> which depict how an explanation based on two system recommendations that were supported by a fact and foil respectively were inferred to be of a contrastive type. The reasoner leveraged the encoding of <a href="#explanationtypes">sufficiency conditions for each explanation type</a> that we support as OWL restrictions within our ontology.</caption>-->
  
 </content>
