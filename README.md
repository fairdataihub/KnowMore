[![Contributors][contributors-shield]][contributors-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![DOI](https://zenodo.org/badge/384260122.svg)](https://zenodo.org/badge/latestdoi/384260122)
<!-- [![Lines of code][lines-of-code-shield]][lines-of-code-url] -->


<!-- HEADER -->
<br />
<p align="center">
  <a href="#">
    <img src="https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/kmlogo-with-text3.png" alt="Logo" height="80">
  </a>
  <br/>
  <h3 align="center">
    Say "no more" to tedious manual discovery across SPARC datasets
  </h3>
  <h4 align="center">
  <br/>
  <a href="https://sparc-know-more.herokuapp.com/sparc-app/">Test the KnowMore prototype</a>
  </h4>
  <p align="center">
     <br/>
   <a href="https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/KnowMore-Manuscript-v1.0.pdf">Read manuscript draft </a> . <a href="https://github.com/SPARC-FAIR-Codeathon/KnowMore/issues">Report Issue</a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About](#about)
* [The Problem](#the-problem)
* [Our Solution - KnowMore](#our-solution---knowmore)
* [Workflow](#workflow)
* [Using KnowMore](#using-knowmore)
* [Using the Source Code](#using-the-source-code)
* [Reporting issues and contributing](#reporting-issues-and-contributing)
* [Cite us](#cite-us)
* [FAIR practices](#fair-practices)
* [License](#license)
* [Team](#team)
* [Acknowledgements](#acknowledgements)

## About
This is the repository of Team KnowMore (Team #6) at the 2021 SPARC Codeathon. Click [here](https://commonfund.nih.gov/sparc) to find out more about the NIH SPARC (Stimulating Peripheral Activity to Relieve Condition) Program. Click [here](https://sparc.science/help/2021-sparc-fair-codeathon) to find out more about the SPARC Codeathon 2021. Check out the [Team section](#team) of this page to find out more about our team members.

**No work was done on this project prior to the Codeathon**. Only the high-level idea of a knowledge discovery tool for SPARC datasets was submitted as a project suggestion for the Codeathon. The detailed outline of the project (what knowledge? what level of automation? what use case?) was defined jointly by the team after the kick-off of the Codeathon. The development of all the code and documentation was initiated subsequently.

## The Problem
The NIH SPARC program seeks to accelerate the development of therapeutic devices that modulate electrical activity in nerves to improve organ function. All the datasets generated by SPARC-funded projects are curated and shared according to strict guidelines that ensure these datasets are [Findable, Accessible, Interoperable, and Reusable (FAIR)](https://www.go-fair.org/fair-principles/). Specifically, the datasets are organized and annotated following the [SPARC Data Structure](https://www.biorxiv.org/content/10.1101/2021.02.10.430563v2), shared publicly on the [Pennsieve discover plaform](https://discover.pennsieve.io/), and easily accessible via the SPARC Data Portal ([sparc.science](https://sparc.science/)). The SPARC program thus provides a wealth of openly available and well-curated datasets that span over multiple organs, species, and datatypes and have the potential for leading to new discoveries. This is great! But...

While it is very easy to learn about the findings of a single dataset on the portal by looking at the dataset summary page (e.g., [see here](https://sparc.science/datasets/65?type=dataset)), there is currently **no easy way to rapidly analyze multiple SPARC datasets together**. Typically, a user of the portal will search for datasets through the search feature and identify datasets of interest from the list of results. To find relations across datasets that are deemed of interest, the user would then have to do so manually, i.e., read the description of each of the datasets from their summary page, go through their protocols, browse files that are accessible from the browser, etc. For a deeper investigation and cross-analysis of the data from these datasets, they will then have to download each dataset before analyzing them further on their computer (payment may be required for downloading large datasets according to AWS pricing). This is a tedious process that needs to be urgently improved to enable rapid discoveries from SPARC datasets, which would 1) Enhance the speed of innovations in the neuromodulation field and 2) Elevate the impact of the SPARC program.

## Our Solution - KnowMore
To address this problem, we have developed a tool called KnowMore. KnowMore is an automated knowledge discovery tool integrated within the SPARC Portal that allows users of the portal to visualize, in just a few clicks, potential similarities, differences, and connections between multiple SPARC datasets of their choice. This simple process for using KnowMore is illustrated in the figure below.

<br/>
<p align="center">
   <img src="https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/knowmore-usage-blue.png" alt="knowmore-usage" width="900">
  <br/> 
  <br/> 
  <i> Illustration of the simple user side workflow of KnowMore. Note that the tool is not currently integrated in the offical SPARC Portal, but accessible through our own deployed prototype. We refer to the <a href="https://github.com/SPARC-FAIR-Codeathon/KnowMore#using-knowmore"> "Using KnowMore"</a>, section for details. </i>
  </img>
</p> 
<br/>

The output of KnowMore consists of multiple interactive visualization items displayed to the user such that they can progressively gain knowledge on the potential similarities, differences, and relations across the datasets. This output is intended to provide foundational information to the user such that they can rapidly make novel discoveries from SPARC datasets, generate new hypotheses, or simply decide on their next step (assess each dataset individually on the portal, download and analyze the datasets further, remove/add datasets to their analysis pool, etc.). A list of the visualization items is provided in the table below, along with the potential knowledge that could be gained from each of them. 

<table>
<thead>
  <tr>
    <th>Visualization item</th>
    <th>Knowledge gained across the datasets</th>
    <th>Raw data used for generating the visualization and how it was obtained </th>
    <th>Status</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td> Knowledge Graph</td>
    <td>High-level connections (authors, institutions, funding organisms, etc.)</td>
    <td> 
      Dataset metadata from <a href="https://docs.pennsieve.io/reference/discover_datasets"> Pennsieve API </a> and
      <a href="https://fdilab.gitbook.io/api-handbook/sparc-metadata-elasticsearch/untitled"> SciCrunch Elasticsearch API</a> 
    </td>
    <td>&#9989</td>
  </tr>
  <tr>
    <td> Summary Table</td>
    <td>Similarities/differences in the study design</td>
    <td> Dataset metadata.json file from <a href="https://docs.pennsieve.io/reference/discover_datasets"> Pennsieve API </a> </td>
    <td>&#9989</td>
  </tr>
  <tr>
    <td> Common Keywords </td>
    <td>Common themes</td>
    <td> Dataset metadata.json file and all dataset text files from <a href="https://docs.pennsieve.io/reference/discover_datasets"> Pennsieve API </a>, protocol text from <a href="https://www.protocols.io/developers"> protocols.io API</a> </td>
    <td>&#9989</td>
  </tr>
  <tr>
    <td> Abstract </td>
    <td>Common study design and findings </td>
    <td> Dataset metadata.json file and all dataset text files from <a href="https://docs.pennsieve.io/reference/discover_datasets"> Pennsieve API</a>, protocol text from <a href="https://www.protocols.io/developers"> protocols.io API</a> </td>
    <td>&#9989</td>
  </tr> 
  <tr>
    <td> Data Plots </td>
    <td>Comparison  between measured numerical data (if any) </td>
    <td> MAT files in the derivative folder of the datasets on <a href="https://docs.pennsieve.io/reference/discover_datasets"> Pennsieve API</a> </td>
    <td>&#9989</td>
  </tr>
  <tr>
    <td> Image Clustering </td>
    <td>Comparison between image data (if any) </td>
    <td> Image files associated with the datasets from <a href="https://documenter.getpostman.com/view/8986837/SVtPXAVm"> Biolucida API </a> </td>
    <td>&#10060;</td>
  </tr>
</tbody>
</table>
<p align="center">
<i> Table listing the visualization items automatically generated by KnowMore along with their status (&#9989 = available, &#10060 = not fully ready) </i>
</p>
<br/>

A sample output is presented in the figure below. 

<br/>
<p align="center">
   <img src="https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/knowmore-ouput.PNG" alt="coming-soon..." width="900">
  <br/> 
  <i> Sample output from KnowMore. It consists of interactive text and plots display to the user.</i>
  </img>
 </p> 
<br/>

Under the hood, KnowMore uses several Machine Learning and Data Science workflows to output the above-mentioned elements, including Natural Language Processing (NLP), Image clustering, and Data Correlation. Details about these are discussed in the [draft of our manuscript](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/KnowMore-Manuscript-v1.0.pdf) associated with this project.

## Workflow
The overall workflow of KnowMore is shown in the figure below. Our architecture consists of three main blocks that can all run independently:
1. The front end of our app is based on a fork of the sparc-app (i.e. the front-end of sparc.science) where we have integrated additional UI elements and back-end logic for KnowMore. [Learn more about the sparc app](https://github.com/nih-sparc/sparc-app).
2. The back-end consists of a Flask application that listens to front-end requests and launches the data processing jobs. 
3. The data processing and result generation is done through a Matlab code (for 'MAT' data files) and Python code (all other data types) that run on osparc, the SPARC supported cloud computing platform. [Learn more about osparc](http://docs.osparc.io/).

<br/>
<p align="center">
   <img src="https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/workflow.png" alt="knowmore-workflow" width="900">
  <br/> 
  <i> Illustration of the overall technical workflow of KnowMore. The red rectangles highlight the major code blocks of KnowMore that have been developed during this Codeathon. </i>
  </img>
 </p> 
<br/>


Such a design was motivated by our aim of making KnowMore ready to on-board the SPARC Data Portal:
* Integrating the front-end of KnowMore would only require to merge our fork of the sparc-app with the main branch sparc-app branch.
* The back-end of the sparc-app, the [sparc-api](https://github.com/nih-sparc/sparc-api), is build with Flask so the KnowMore back-end would be readily compatible.
* The data processing jobs are designed to run on osparc, the SPARC supported cloud computing platform, and would not require any type of integration as our back-end ensures communication with osparc.

Moreover, each of the three main elements of KnowMore is fully independent. While the front-end will not be of much use on its own, having the back-end fully interoperable is very valuable as our flask application can be connected to any front-end if needed (another analysis tool, website, software, etc.). The data processing and results generation jobs are also independent such that they can be used directly to get the visualization items, for instance in a Jupyter Notebook. Note that the data for the Knowledge graph is obtained from Pennsieve/Scicrunch on the front-end for efficiency but the same results can be generated in the back-end as well.

## Usecase
Our development and testing revolved around these three datasets: 
* [Quantified Morphology of the Rat Vagus Nerve](https://doi.org/10.26275/ilb9-0e2a)
* [Quantified Morphology of the Pig Vagus Nerve](https://doi.org/10.26275/maq2-eii4)
* [Quantified Morphology of the Human Vagus Nerve with Anti-Claudin-1](https://doi.org/10.26275/nluu-1ews)

They were selected due to their common theme with the aim of making some interesting and meaningful discoveries during the Codeathon. Our discoveries from these datasets are discussed in the [draft of our manuscript](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/KnowMore-Manuscript-v1.0.pdf) initiated during the Codeathon. Our results can be reproduced by selecting these datasets when using KnowMore (see next section). We would like to emphasize that our tool is not specifically designed around these datasets and is intended to work with any user-selected datasets. Only the Data Plots are limited to work with these datasets since we found that there are many discrepancies in tabular data structuring from dataset to dataset that limited auto generation of meaningful plots. Our suggestion to SPARC is to focus on standardizing tabular data for the next update to the SPARC Data Structure for icreasing the the interoperability of SPARC datasets. Recommendations to achieve that are discussed in the draft of our manuscript and well as the ["Recommendation from the KnowMore Team to increase FAIRness of SPARC datasets"](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/Recommendation%20from%20the%20KnowMore%20Team%20to%20increase%20FAIRness%20of%20SPARC%20datasets.pdf) document we have submitted to SPARC.

## Using KnowMore
You can test the current prototype of KnowMore directly on our fork of the SPARC Data Portal: https://sparc-know-more.herokuapp.com/sparc-app/

Follow the steps described below:
1. Find datasets of interest and click on the "Add to KnowMore" button, visible in the search list and the dataset page, to add each of them in the KnowMore analysis 
2. Go to the KnowMore tab, and check that all your selected datasets are listed
3. Click on "Discover" to initiate the automated discovery process
4. Wait until the results are displayed

## Using the Source Code

### Prerequisites 
We recommend using Anaconda to create and manage your development environments for KnowMore. All the subsequent instructions are provided assuming you are using [Anaconda (Python 3 version)](https://www.anaconda.com/products/individual).

### Running the app
To use the source code, clone or download the repository first.
```
git clone https://github.com/SPARC-FAIR-Codeathon/KnowMore.git --recurse
```

Then run our back-end flask-server following the documentation [available here](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/README.flask.md).

Finally, run our fork the sparc-app by following the documentation [available here](https://github.com/RyanQuey/sparc-app/tree/84ab5df2203ef0a551051cf0ac037762dbc4e7dc).

Our back-end data processing program consists of a Matlab code for handling 'MAT' files (when found in a dataset) and a Python code for processing all other data types. They run on osparc and, as such, do not require any local setup. The documentation for using/editing them is, however, [available here](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/assets/INPUT_FOLDER/README.md) if needed.

## Reporting issues and contributing
To report an issue or suggest a new feature, use the [issue page](https://github.com/SPARC-FAIR-Codeathon/KnowMore/issues). Check existing issues before submitting a new one.

Fork this repositery and submit a pull request to contribute. Before doing so, please read our [Code of Conduct](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/CODE_OF_CONDUCT.md) and [Contributing Guidelines](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/CONTRIBUTING.md).

## Cite us
If you use KnowMore to make new discoveries or use the source code, please cite us as follows
```
Ryan Quey, Matthew Schiefer, Anmol Kiran, Bhavesh Patel (2021). KnowMore: v1.0.0 - Automated Knowledge Discovery Tool for SPARC Datasets. 
Zenodo. https://doi.org/10.5281/zenodo.5137255.
```

## FAIR practices
Given that this codeathon revolved around FAIR data, we deemed suitable to ensure that the development of KnowMore is also FAIR. We have assessed accordingly the FAIRness of KnowMore against the FAIR Principles established for research software. The details are available in this [document](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/docs/FAIRness-KnowMore.pdf).

## License
KnowMore is fully Open Source and distributed under the very permissive MIT License. See [LICENSE](https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/main/LICENSE) for more information.



<!-- ## FAIR practices -->

## Team
* [Bhavesh Patel](https://github.com/bvhpatel/) (Lead)
* [Ryan Quey](https://github.com/RyanQuey) (SysAdmin)
* [Matthew Schiefer](https://github.com/schiefma/) (Writer - Manuscript)
* [Anmol Kiran](https://github.com/codemeleon) (Writer - Documentation)

## Acknowledgements
We would like to thank the organizers of the 2021 SPARC Codeathon and thank the [SPARC Data Resource Center (DRC) teams](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8265045/) for their guidance and help during this Codeathon.


[contributors-shield]: https://img.shields.io/github/contributors/SPARC-FAIR-Codeathon/KnowMore.svg?style=flat-square
[contributors-url]: https://github.com/SPARC-FAIR-Codeathon/KnowMore/graphs/contributors
[stars-shield]: https://img.shields.io/github/stars/SPARC-FAIR-Codeathon/KnowMore.svg?style=flat-square
[stars-url]: https://github.com/SPARC-FAIR-Codeathon/KnowMore/stargazers
[issues-shield]: https://img.shields.io/github/issues/SPARC-FAIR-Codeathon/KnowMore.svg?style=flat-square
[issues-url]: https://github.com/SPARC-FAIR-Codeathon/KnowMore/issues
[license-shield]: https://img.shields.io/github/license/SPARC-FAIR-Codeathon/KnowMore.svg?style=flat-square
[license-url]: https://github.com/SPARC-FAIR-Codeathon/KnowMore/blob/master/LICENSE
[lines-of-code-shield]: https://img.shields.io/tokei/lines/github/SPARC-FAIR-Codeathon/KnowMore
[lines-of-code-url]: #
