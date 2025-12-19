# Cover Letter to PLOS Computational Biology

Dear Editor,

We submit for consideration "Composable probabilistic models can lower barriers to rigorous infectious disease modelling" as a Methods article for PLOS Computational Biology.

Mathematical models help synthesise data to inform infectious disease policy for both routine surveillance and outbreak response.
For evidence to inform policy it must be timely and rigorous, yet current modelling approaches struggle to achieve both.
During COVID-19, models integrating multiple data sources informed policy decisions, yet were not adapted for the 2022 mpox outbreak where different expertise was needed.
Similarly, multi-team forecasting collaborations combine outputs to improve forecasts, but teams rarely share model components despite shared goals.
Methods either chain separate models together, offering flexibility but losing information, or use rigorous joint models that are monolithic and difficult to adapt.

In this work, we propose composable probabilistic infectious disease modelling as a solution for this tension.
We present requirements for a composable probabilistic modelling framework, and a proof of concept demonstrating feasibility.
We then demonstrate the approach through three case studies recreating published analyses.
The first replicates a COVID-19 analysis for South Korea using renewal processes.
The second extends these components with reporting delays and day-of-week effects to replicate EpiNow2, a real-time nowcasting tool.
The third replicates an ordinary differential equation model analysis of influenza outbreak data.

The methodological contribution is a set of requirements for composable infectious disease modelling along with a proof of concept, validated through case studies recreating three published analyses using shared components.
This addresses the Epidemiology & Public Health section by providing a principled approach for infectious disease modellers to build rigorous joint models that remain adaptable.
The proof of concept implementation is open source with an R interface to lower adoption barriers.
Such systems could provide the rigorous evidence needed to inform policy in a timely manner during both routine surveillance and outbreak response.

All authors have approved the manuscript and declare no competing interests.

Yours sincerely,

Sam Abbott and Samuel P. C. Brand
(on behalf of all authors)