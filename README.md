# cosmology-galaxy-clustering-aps
```mermaid
graph TD
    %% Custom Styling
    classDef realData fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px;
    classDef simData fill:#efebe9,stroke:#795548,stroke-width:2px;
    classDef tool fill:#f3e5f5,stroke:#9c27b0,stroke-width:2px;
    classDef output fill:#e8f5e9,stroke:#4caf50,stroke-width:2px;

    %% Stream 1: Galaxy Clustering Observational Data
    subgraph Observational_Pipeline [DELVE & SDSS Galaxy Catalogs]
        A1[DELVE Survey Data]:::realData --> B[Galaxy Selection & Cleaning]
        A2[SDSS Survey Data]:::realData --> B
        B --> C[Apply Angular Survey Mask]:::realData
    end

    %% Stream 2: Simulation / Mock Data
    subgraph Simulation_Pipeline [Mock Catalog Generation]
        D1[Quijote Simulations]:::simData --> E[Mock Galaxy Catalog Generation]
        D2[In-House Simulations]:::simData --> E
        E --> F[Apply DELVE / SDSS Footprints & Selection Functions]:::simData
    end

    %% HEALPix Grid Pixelization
    subgraph Map_Making [HEALPix Pixelization]
        C --> G[Observational HEALPix Maps]:::tool
        F --> H[Simulated Mock HEALPix Maps]:::tool
    end

    %% NaMaster Pseudo-Cl Estimation
    subgraph Power_Spectrum [NaMaster Estimator]
        G --> I[Compute Pseudo-Cl & Mode Coupling Matrix]:::tool
        H --> I
        I --> J[Mask Deconvolution & Binned Cl]:::tool
    end
    
    %% Downstream Cosmology Output
    J --> K[Galaxy Clustering APS Results]:::output
    K --> L[Covariance Matrix Computation]:::output
    L --> M([Cosmological Parameter Inference]):::output
```
### Presentation Slides
You can download the senior seminar presentation here:
[Download senior seminar presentation (PPTX)](senior-seminar presentation-slides.pptx)
