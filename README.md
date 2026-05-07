# JAIA Bot and YSI Temperature Comparison

## Overview

This repository contains a Jupyter Notebook analysis comparing Jaiabot temperature sensor measurements during repeated pipe dives with YSI sampling data. The analysis focuses on the Jaiabot main temperature sensor, the Jaiabot TSYS01 temperature sensor, and Jaiabot pressure-adjusted recorded depth.

The goal of this project is to evaluate how both Jaiabot temperature sensors responded during rapid temperature changes and repeated downcast-upcast pipe dives. The notebook uses Jaiabot recorded depth to identify individual dives, split each dive into downcast and upcast sections, plot selected dives, and calculate upcast-downcast temperature bias.

## Repository Contents

- `YSIcomparisonJAIA.ipynb`: Main Jupyter Notebook containing the full analysis.
- `YSI_data.csv`: YSI sampling dataset used as an external temperature reference.
- `TestTubeFirstSet.csv`: First Jaiabot mission dataset.
- `TestTubeSecondSet.csv`: Second Jaiabot mission dataset.
- `environment.yml`: Conda environment file used to reproduce the analysis.
- `README.md`: Description of the repository and project.

## Data Description

The Jaiabot datasets include timestamped measurements of the main Jaiabot temperature sensor, the TSYS01 temperature sensor, and pressure-adjusted recorded depth. The YSI dataset includes temperature, salinity, and depth observations collected during the same pipe experiment. The data were used to compare how the Jaiabot sensors responded during repeated pipe dives and rapid temperature transitions.

## Methods

The notebook first loads and cleans the YSI and Jaiabot datasets. Individual Jaiabot dives are detected using local maximum depth points from the Jaiabot pressure-adjusted depth record. Each dive is then split into downcast and upcast portions using the deepest recorded point as the approximate turn-around point.

Selected dives are plotted using Jaiabot recorded depth. Sensor type is shown by color, while cast direction is shown by line style and triangle markers. The notebook also calculates upcast-downcast temperature bias by interpolating downcast and upcast temperatures onto matching recorded depths.

## Main Findings

The selected dive plots show that the TSYS01 sensor captured a wider temperature range during repeated pipe dives. It reached both warmer top-pipe temperatures and cooler bottom-pipe temperatures more clearly than the main Jaiabot temperature sensor, suggesting that TSYS01 may be more responsive to rapid temperature changes.

The upcast-downcast bias analysis showed that both sensors had mostly negative bias when matched by Jaiabot recorded depth, meaning upcast temperatures were generally cooler than downcast temperatures at the same recorded depth. The main Jaiabot temperature sensor showed less upcast-downcast spread, while the TSYS01 sensor showed greater variability. This suggests a tradeoff where TSYS01 appears more responsive to rapid changes, while the main Jaiabot temperature sensor appears smoother and more consistent. Although, the main sensor didn't come close to the YSI temperature readings of the pipe while the TSYS01 did.

## How to Run

1. Download or clone this repository.
2. Create the conda environment using:

```bash
conda env create -f environment.yml
