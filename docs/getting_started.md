---
title: Getting started
nav_order: 3
---

# Getting Started
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Creating a chart with Graph

In order to introduce you to our graphing tool, we will demostrate how to create charts using the Graph's interface to visualize SDDP case outputs. For the example, example case 20 will be used. It consists, basically, of one system containing three thermal plants supplying energy to consumers. Twelve stages constitute the study horizon, and the execution is deterministic.

For our first chart, let us suppose we are interested in visualizing the generations of each thermal plant in the system. So, to create the chart that fulfills out needs, follow the steps showed bellow.

The steps are listed below:

 1. Open Graph's interface

<div style="text-align:center">
    <img src="images\getting_started\OpeningGraphInterface.png" width="500"/>
</div>

 2. Select the option to add new chart

<div style="text-align:center">
    <img src="images\getting_started\AddChart.png" width="350"/>
</div>

 3. Choose the variable and agents to be analyzed

<div style="text-align:center">
    <img src="images\getting_started\SelectVariable_v2.png" width="450"/>
</div>

And then:

<div style="text-align:center">
    <img src="images\getting_started\SelectAgents.png" width="450"/>
</div>

 4. Configure the chart

<div style="text-align:center">
    <img src="images\getting_started\MainChartConfigs.png" width="450"/>
</div>

Following the steps above, the chart obtained will be:

<div style="text-align:center">
    <img src="images\getting_started\ThermalGenGraph_v2.png" width="1000"/>
</div>

## Using PSRIO to create new variables

Now, let us make some processing over the standard output data using PSRIO. In the previous section, we created a chart with 3 curves, each one describing the generation of each thermal plant of system during the study period. Suppose that we want the aggregated thermal generation, which is not standard, instead of each one separately. We will use PSRIO to make this processing and create a new variable for us, so that we can plot it and analyze the result.

The steps are listed below:

1. Open PSRIO editor

<div style="text-align:center">
    <img src="images\getting_started\OpenPSRIO.png" width="400"/>
</div>

2. Write, save and run the script for the processing

<div style="text-align:center">
    <img src="images\getting_started\RunPSRIO.png" width="450"/>
</div>

Note that we created a file named `total_gerter.csv`. `total_gerter` will be the name that we will have to search for when creating the chart. 

 3. Select "Add chart" option and find custom variable

<div style="text-align:center">
    <img src="images\getting_started\FindCustomVariable.png" width="600"/>
</div>

 4. Configure the chart

The final result looks like this:

<div style="text-align:center">
    <img src="images\getting_started\CustomPSRIOVar_v2.png" width="1000"/>
</div>

The recipe used for this example is the following:
```lua 
-- PSR Energy Consulting and Analytics
-- Graph 
-- Tutorial - Getting Started

-- load thermal collections and thermal generation data
thermal = require("collection/thermal");
gerter = thermal:load("gerter");

-- aggregate agents generations by sum and save to output file
total_gerter = gerter:aggregate_agents(BY_SUM(), "Total thermal");
total_gerter:save("total_gerter", {csv=true});
```



