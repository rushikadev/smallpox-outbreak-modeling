# Modeling a Deliberate Smallpox Release: Two Approaches

Two complementary epidemiological models of a bioterrorism scenario:a deliberate release of smallpox (Variola major). 
The two models will comapre the different response strategies: "no response," "ring vaccination + case isolation," and "mass vaccination".

Smallpox is used as the scenario pathogen because it's a WHO/CDC **Category A** bioterrorism agent.
**Smallpox**
- highly transmissible (R0 ≈ 5–7)
- a ~12-day incubation period that makes early detection difficult
- ~30% case fatality in unvaccinated people
- eradication in 1980 ended routine vaccination resulting in a global population with essentially no immunity
- 
Its historical weaponization by the Soviet Biopreparat program, and its continued use in biodefense planning scenarios (e.g. the 2001 "Dark Winter" tabletop exercise), make it a standard reference case in biodefense modeling.

## Two models, two kinds of insight

- **`seir_model.ipynb`**: a compartmental (SEIR) model using ordinary differential equations. Fast, deterministic, and good for seeing the  *expected* trajectory and comparing intervention strategies at scale.
- **`agent_based_model.ipynb`**: an individual-level Monte Carlo simulation on a small-world contact network, run across many stochastic trials. Slower, but captures something the compartmental model structurally can not: the chance extinction of small outbreaks, and the effect of realistic (clustered, not uniformly-mixed) contact structure.

Both are calibrated to the same epidemiological parameters and the same 21-day detection delay (the outbreak spreads uncontrolled until public health surveillance identifies it), so their results are directly comparable.

## Key finding

Both models agree that **ring vaccination + case isolation**, which is the actual strategy that eradicated smallpox in the 1970s, performs comparably to, or better than, mass vaccination, while requiring far fewer vaccine doses and less logistics capacity. Additionally, the agent-based model shows that with either intervention active, a meaningful share of simulated outbreaks go extinct on their own within the first handful of cases. This creates an argument for why speed of detection and targeted response can matter as much as the response's raw strength.

## Parameter sources

Model parameters are drawn from the smallpox modeling and biodefense literature rather than arbitrary assumptions:

- **R0 ≈ 6**: A systematic review of smallpox modeling studies found R0 estimates clustering between 3–6 across most published models, while estimates derived directly from historical outbreak data ran higher (10–20). The CDC's own ring-vaccination model uses R0 ≈ 5.2 as its baseline, making 6 a reasonable mid-range choice. ([Costantino et al. 2018, *Military Medicine*](https://pubmed.ncbi.nlm.nih.gov/29425329/);[Eichner & Dietz 2004, CDC *Emerging Infectious Diseases*](https://wwwnc.cdc.gov/eid/article/10/5/03-0419_article))
- **Incubation period ≈ 12 days**: Strong consensus in the literature (88% of reviewed studies used 11–12 days); matches the CDC's clinically reported 10–14 day range. ([Costantino et al. 2018](https://pubmed.ncbi.nlm.nih.gov/29425329/); [CDC Clinical Signs and Symptoms of Smallpox](https://www.cdc.gov/smallpox/hcp/clinical-signs/index.html))
- **Infectious period ≈ 17 days**: This parameter varies more across the literature (4–20 days depending on how "infectious" is defined — onset of rash vs. full scab resolution), so 17 days is a defensible mid-to-upper estimate rather than a firm consensus figure. ([Costantino et al. 2018](https://pubmed.ncbi.nlm.nih.gov/29425329/))
- **Case fatality rate ≈ 30%**: Well established specifically for variola major in unvaccinated populations, consistently cited across CDC, FDA, and clinical literature. ([CDC](https://www.cdc.gov/smallpox/hcp/clinical-signs/index.html);[Diagnosis and Management of Smallpox, *NEJM* 2002](https://www.nejm.org/doi/full/10.1056/NEJMra020025))

**Policy and historical framing:**

- **CDC Category A classification:** Smallpox is one of six agents (with anthrax, plague, botulism, tularemia, and viral hemorrhagic fevers) the CDC designates Category A: the highest-priority bioterrorism agents, based on ease of transmission and potential for mass casualties.([AAFP, "Bioterrorism," 2021](https://www.aafp.org/pubs/afp/issues/2021/1000/p376.html))
- **Dark Winter (2001):** A senior-level tabletop exercise (Andrews Air Force Base, June 22–23, 2001) simulating a covert smallpox release in Oklahoma City, run by the Johns Hopkins Center for Civilian Biodefense Strategies and CSIS, referenced here as the standard real-world precedent for this kind of scenario planning. ([Inglesby et al., "Shining Light on Dark Winter," *Clinical Infectious  Diseases*, 2002](https://pubmed.ncbi.nlm.nih.gov/11880964/))
- **Soviet Biopreparat weaponization of smallpox:** Confirmed through the defector testimony of Ken Alibek and Vladimir Pasechnik, who reported Soviet mass production of weaponized smallpox with an estimated annual capacity of 90–100 tons. (Leitenberg & Zilinskas, *The Soviet Biological Weapons Program: A History*, Harvard University Press, 2012)

## Requirements

```
numpy
scipy
matplotlib
networkx
```

## Usage

Each notebook is self-contained — run top to bottom to reproduce all figures and results.
