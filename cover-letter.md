# Cover Letter to PLOS Computational Biology

Dear Editor,

We submit for consideration "A Prototype for Compositional Probabilistic Infectious Disease Modelling" as a Methods article for PLOS Computational Biology.

Recent outbreaks of Ebola, COVID-19 and mpox have demonstrated the value of modelling for synthesising data for rapid evidence to inform decision making.
However, current modelling approaches create barriers to integration of expert domain knowledge.
Methods used to synthesise available data broadly fall into pipeline approaches that chain separate models together, or joint models that are often monolithic and difficult to adapt.
These barriers have prevented advances across multiple settings where models could have provided actionable insights.

This paper addresses these limitations by outlining key requirements for a composable infectious disease modelling framework and presenting a proof-of-concept implementation that addresses these requirements through composable epidemiological components built on Julia's type system and Turing.jl.
Our approach enables "LEGO-like" model construction where complex models emerge from composing simpler, reusable components.

We validate the approach through three case studies that recreate published epidemiological analyses, demonstrating that components can be reused across different models whilst maintaining statistical rigour.
The first replicates a COVID-19 analysis for South Korea using renewal processes with time-varying reproduction numbers.
The second extends these components with reporting delays and day-of-week effects for real-time nowcasting applications.
The third integrates ODE solvers for compartmental disease transmission models applied to influenza outbreak data.

We believe this work fits the Epidemiology & Public Health section, specifically addressing process-based approaches to infectious disease modelling.
The framework enables interdisciplinary collaboration by lowering technical barriers for domain experts to contribute directly to model development, and establishes requirements for future composable modelling systems that can respond to unpredictable infectious disease threats.

All authors have approved the manuscript and declare no competing interests.

Yours sincerely,

Sam Abbott and Samuel P. C. Brand
(on behalf of all authors)
