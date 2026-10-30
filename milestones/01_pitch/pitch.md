# Milestone 1 — Pitch
**Due: 30.10.2026**

---


**VISTA** – Visual Identification and Search Tool for Abstract Art

*A visual retrieval system that identifies abstract paintings from photographs and links them to their catalogue records.*

This project explores how visual retrieval can make art collections accessible without textual entry points, using the *Schüttbilder* (action paintings) of the Austrian artist *Hermann Nitsch* (1938–2022) as a case study. These non-figurative works were created in large numbers during *Malaktionen* (painting performances), in which, as the artist described, paint was smeared, splattered and poured onto the canvas.[^1] As a result, the works are shaped by gesture and bodily movement rather than by depicted objects. The self-supervised vision transformer model DINOv2 has been shown to capture texture and structure far beyond its training data, even without fine-tuning: Brondolo and Beaussant demonstrated that it reliably distinguishes rock samples in CT scans by clustering them according to pore size and porosity density,[^2] while Oquab et al. additionally report strong instance retrieval on artworks among their benchmarks.[^3] These findings suggest that the model could also capture the visual identity of abstract paintings. Building on this, the project combines frozen DINOv2 embeddings with art collection metadata in a visual Retrieval-Augmented Generation (RAG) pipeline.

The project addresses two research questions:

- **RQ1:** To what extent can frozen DINOv2 features reliably re-identify an individual action painting, and how robust is this re-identification across different types of query images?  
Tested in two steps: first with synthetic transformations such as cropping, rotation and brightness changes, then with real smartphone photographs showing reflections, perspective distortion and color shifts.


- **RQ2:** How can a visual RAG system use the retrieved matches to generate accurate catalogue information?  
Including how the RAG component should communicate uncertainty when no reliable match is found, instead of forcing a single identification.

The system draws on digitized action paintings from the artist's catalogue raisonné, provided by the Nitsch Foundation and the Atelier Hermann Nitsch, each assigned a unique image ID that links it to its catalogue record; within the scope of this project, works created before 1990 are excluded, as their data would require additional preparation. Real smartphone photographs serve as test queries, reflecting how works are often encountered in practice. Having worked for the artist for 15 years, I know how much time is spent identifying works from such images, a problem shared by many GLAM institutions. The system could reduce an expert's hours of manual comparison to a matter of verification. Beyond identification, it could surface visually related works, which would offer added value for art historical research. If reliable, the pipeline could be transferred to other art collections without fine-tuning or annotated training data, serving as a reusable component for digital asset management (DAM) systems and archives used by art historians, curators, archivists and digital humanities researchers.

The project also raises technical and legal concerns: Frozen embeddings may fail to separate similar works or lose accuracy on smartphone photographs, and incorrect matches or hallucinated details could produce convincing but false answers. The system can therefore support expert judgement, but neither replace it nor guarantee completeness. Since the artworks are protected by copyright and the corpus is confidential, an external LLM API is not an option; how to integrate an LLM without sharing collection data remains an open question.

**Note:** Within the scope of this project, catalogue records are limited to image ID, painting performance number, location, year and dimensions. Further fields of the catalogue raisonné, such as provenance, exhibition history and literature, are not included.

--- 

[^1]: Hermann Nitsch, “Action Painting” (1964), nitsch.org, accessed October 29, 2026, https://www.nitsch.org/en/paintingactions/. ↩

[^2]: Florent Brondolo and Samuel Beaussant, “DINOv2 Rocks Geological Image Analysis: Classification, Segmentation, and Interpretability,” Journal of Rock Mechanics and Geotechnical Engineering 17 (2025): 6859, https://doi.org/10.1016/j.jrmge.2025.01.057. ↩

[^3]: Maxime Oquab et al., “DINOv2: Learning Robust Visual Features without Supervision,” Transactions on Machine Learning Research (2024): 14, https://arxiv.org/abs/2304.07193. ↩