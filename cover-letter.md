# Cover Letter to PLOS Computational Biology

Dear Editor,

We submit for consideration "Composable probabilistic models can lower barriers to rigorous infectious disease modelling" as a Methods article for PLOS Computational Biology.

Recent outbreaks of Ebola, COVID-19 and mpox, and routine surveillance of endemic pathogens such as influenza, have demonstrated the value of modelling for synthesising data to inform decision making.
However, current approaches create barriers to integrating diverse expertise required for effective outbreak response.
Methods either chain separate models together, offering flexibility but losing information and potentially introducing bias, or use rigorous joint models that are often monolithic and difficult to adapt.
These barriers have prevented advances across settings where models could have provided actionable insights.

This paper addresses these limitations by outlining proposed requirements for a composable infectious disease modelling framework and presenting a proof of concept.
Our approach enables components to be reused across contexts and combined whilst maintaining statistical rigour.
When components have standardised interfaces, domain experts can contribute specialised knowledge without understanding entire modelling frameworks.

We demonstrate the approach through three case studies recreating published analyses, showing component reuse across different models.
The first replicates a COVID-19 analysis for South Korea using renewal processes.
The second extends these components with reporting delays and day-of-week effects to replicate EpiNow2, a real-time nowcasting tool.
The third replicates an ordinary differential equation model analysis of influenza outbreak data.

We believe this work fits the Epidemiology & Public Health section, specifically addressing process-based approaches to infectious disease modelling.
Such systems could improve both routine surveillance, where validated components can be refined across seasons, and outbreak response, where components can be rapidly adapted for novel pathogens.
The framework enables interdisciplinary collaboration by lowering technical barriers for domain experts to contribute directly to model development.

All authors have approved the manuscript and declare no competing interests.

Yours sincerely,

Sam Abbott and Samuel P. C. Brand
(on behalf of all authors)