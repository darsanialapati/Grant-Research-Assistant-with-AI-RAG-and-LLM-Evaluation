# AI for Research Proposal Automation

A Python and retrieval-augmented generation (RAG) prototype that turns an NIH Notice of Funding Opportunity (NOFO) and a collection of research papers into a first-draft research concept note. The demo focuses on digital mental health research and supports early proposal development for faculty and grants-office reviewers.

## Sample result

The demo indexed **7,512 text chunks** and retrieved the **50 most relevant passages** across **13 papers**. It generated five funding-aligned research ideas and developed the selected idea, **Network-Informed Digital Care Transitions for Serious Mental Illness**, into a Research Proposal First Draft

The draft received **2 out of 5** on an advisory LLM rubric covering innovation, significance, approach, and investigator expertise. The score flagged the need for further refinement and expert review.

## How it works

1. Extract the main research topic from the NIH funding announcement.
2. Split research PDFs into overlapping passages, embed them with OpenAI, and index them in Chroma.
3. Retrieve relevant evidence and summarize the papers’ findings, limitations, and research gaps.
4. Generate five candidate ideas. Combine the selected idea, supporting papers, funding announcement, and proposal template to draft a concept note.
5. Export the draft to PDF and display a rubric-based evaluation in the notebook.

**Tools** · Python, Google Colab, LangChain, OpenAI, Chroma, PyPDF, and Markdown PDF.

## Run the demo

1. Open the original notebook in Google Colab. If you only have the [Python export](project_2_learner_lowcode_%281%29.py), copy the code into Colab cells. The export includes notebook shell commands and uses Colab’s `/content` paths.
2. Upload `Project_Files.zip` to `/content`. The workflow expects it to unpack to `/content/Project Files/` with `NOFO.pdf`, `Research Proposal Template.pdf`, and `ResearchPapers.zip`. The nested archive should extract to `/content/Papers/`.
3. Create a private `/content/config.json` with `OPENAI_API_KEY` and `OPENAI_API_BASE`. Use an endpoint with access to the configured chat and embedding models. Keep the credential file out of GitHub.
4. Run the cells in order. Set `idea_number` to choose one of the five generated ideas. The notebook writes `Research Proposal First Draft.pdf` to the working directory.

## Limitations

Retrieval uses the extracted topic and ranks papers by their frequency among the retrieved passages. A more detailed query and a second ranking pass could improve relevance. Before using a draft externally, verify the citations and research claims against the original papers and have a subject-matter expert review the proposed approach.
