---
layout: default
title: Explanation Ontology: A General-Purpose, Semantic Representation for Supporting User-Centered Explanations
---

[Abstract](#abstract) | [Resources](#resources) | [Tools Used](#toolsused) | [Team](#contributors) | [Publications](#publications)


<h1 class="page-title" style="text-transform:uppercase;" id="header">Explanation Ontology: A General-Purpose, Semantic Representation for Supporting User-Centered Explanations</h1>

<p class="message">A website to navigate resources open-sourced for the Explanation Ontology. Use the side navigation panel to explore different sections of the website and click on an add symbol for more navigation options under some sections.</p>

<!-- <table>
  <tbody>
    <tr>
      <td><a href="#abstract">Abstract</a></td>
    </tr>
  </tbody>
</table> -->

<hr>
<article class="mb-5" id="abstract">
<content>
  
  
<h2>Abstract</h2>
  <p>In the past decade, trustworthy Artificial Intelligence (AI) has emerged as a focus for the AI community to ensure better adoption of AI models, and explainable AI is a cornerstone in this area. Over the years, the focus has shifted from building transparent AI methods to making recommendations on how to make black-box or opaque machine learning models and their results more understandable by experts and non-expert users. 
    <hr/>
    In our <a href="https://arxiv.org/abs/2010.01479">previous work</a>, to address the goal of supporting user-centered explanations that make model recommendations more explainable, we developed an Explanation Ontology (EO), a general-purpose representation, to help system designers, our intended users of the EO, connect explanations to their underlying data and knowledge. 
  <hr/>
    We now addresses the apparent need for improved interoperability to support a wider range of use cases. We expand the EO, mainly in the system attributes contributing to explanations, by introducing new classes and properties to support a broader range of state-of-the-art explainer models. We present the expanded ontology model, highlighting the classes and properties that are important to model a larger set of <em>fifteen</em> literature-backed explanation types that are supported within the EO.
  <hr/>
    We build on these explanation type descriptions to show how to utilize the EO model to represent explanations in <em>five</em> use cases spanning the domains of finance, food, and healthcare. We include competency questions that evaluate the EO's capabilities to provide guidance for system designers on how to apply our ontology to their own use cases. This guidance includes allowing system designers to query the EO directly and providing them exemplar queries to explore content in the EO represented use cases. 
  <hr/>
    We have released this significantly expanded version of the Explanation Ontology at <a href="https://purl.org/heals/eo" >https://purl.org/heals/eo</a> and updated here on our <a href ="https://tetherless-world.github.io/explanation-ontology">resource website</a>, with supporting documentation. 
  <hr/>
    Overall, through the EO model, we aim to help system designers be better informed about explanations and support these explanations that can be composed, given their systems' outputs from various AI models, including a mix of machine learning, logical and explainer models, and different types of data and knowledge available to their systems.</p>
 </content>
 
 <hr/>
 <article class="mb-5" id="resources">
<content>
<h2>List of Resources </h2>
<ul>
 <table style="width:100%">
    <tr>
    <th>Resources</th>
    <th>Links</th> 
  </tr>
   <tr>
    <td>Protocol Guidance on Usage of Ontology</td>
    <td><a href="protocol">Protocol</a> </td> 
  </tr>
  <tr>
    <td>Ontology</td>
    <td><a href="ontology">Explanation Ontology</a> </td> 
  </tr>
  <tr>
    <td>Explanation Types</td>
    <td><a href="modeling#explanationtypes">Modeling</a> </td> 
  </tr>
    <!--<tr>
    <td> </td>
    <td> (b) <a href="./application.html">Faceted Browser</a> </td> 
  </tr>-->
    <tr>
    <td>Examples</td>
    <td><a href="clinicalexample">Use Case Examples</a> </td> 
  </tr>
   <tr>
    <td>Competency Questions </td>
    <td><a href="competencyquestions#sparql">SPARQL Queries</a> </td> 
  </tr>
   <tr>
    <td>Tools Used </td>
    <td><a href="index#toolsused">References to tools used</a> </td> 
  </tr>
</table>
  
 </ul>
 </content>
 
 <hr/>
 
 <article class="mb-5" id="toolsused">
<content>
  
  
<h2>Tools Used during Development</h2>
  <ul>
  <li>Ontology Editor: <a href="https://protege.stanford.edu/products.php#desktop-protege">Protege 5.5.0</a></li>
  <li>Conceptual Diagram created using <a href="https://www.omnigroup.com/omnigraffle/">Omnigraffle</a></li>
  <li>Ontology documentation tool, <a href="https://github.com/dgarijo/Widoco">Widoco</a></li>
  <li>RDF Visualization generated with <a href="http://jimmccusker.github.io/rdfviewer/">RDFViewer</a> and <a href="https://github.com/protegeproject/ontograf">Ontograf</a> in Protege</li>
  </ul>
  </content>
  <!--<iframe src="https://tetherless-world.github.io/explanation-ontology/WidocoDocumentation/index-en.html" style="width:100%;"/>-->
  
    <hr/>
    <article class="mb-5" id="contributors">
<content>
  <h2>Team</h2>
  <h2>Current Contributors</h2>
   <h3 style="color:dimgrey;">Shruthi Chari<sup>1</sup>, Oshani Seneviratne<sup>1</sup>, Mohamed Ghalwash<sup>2</sup>, Sola Shirai<sup>1</sup> Daniel M. Gruen<sup>1</sup>, Pablo Meyer<sup>2</sup>, Prithwish Chakraborty<sup>2</sup>, Deborah L. McGuinness<sup>1</sup></h3>
  <h2>Past Contributors</h2>
  <h3 style="color:dimgrey;">Morgan Foreman<sup>2</sup>,  Amar K. Das<sup>2</sup></h3>
<h3><a href="https://www.rpi.edu/"><sup>1</sup>Rensselaer Polytechnic Institute</a> | <a href="https://research.ibm.com/science"><sup>2</sup>IBM Research</a></h3>
   </content>
 
  <article class="mb-5" id="publications">
<content>
  <h2>Publications</h2>
  <ul>
    <li>[<b>Best Resource Paper</b>] Explanation Ontology: A Model of Explanations for User-Centered AI; Shruthi Chari , Oshani Seneviratne , Daniel M. Gruen ,  Morgan A. Foreman , Amar K. Das, Deborah L. McGuinness; Resource Track,19th International Semantic Web Conference 2020</li>
    <li>Explanation Ontology in Action: A Clinical Use-Case; Shruthi Chari , Oshani Seneviratne , Daniel M. Gruen ,  Morgan A. Foreman , Amar K. Das, Deborah L. McGuinness; Posters and Demo Track,19th International Semantic Web Conference 2020</li>
  </ul>
  </content>
<!-- 
<div class="posts">
  {% for post in paginator.posts %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

    {{ post.content }}
  </div>
  {% endfor %}
</div>

<div class="pagination">
  {% if paginator.next_page %}
    <a class="pagination-item older" href="{{ site.baseurl }}page{{paginator.next_page}}">Older</a>
  {% else %}
    <span class="pagination-item older">Older</span>
  {% endif %}
  {% if paginator.previous_page %}
    {% if paginator.page == 2 %}
      <a class="pagination-item newer" href="{{ site.baseurl }}">Newer</a>
    {% else %}
      <a class="pagination-item newer" href="{{ site.baseurl }}page{{paginator.previous_page}}">Newer</a>
    {% endif %}
  {% else %}
    <span class="pagination-item newer">Newer</span>
  {% endif %}
</div> -->
