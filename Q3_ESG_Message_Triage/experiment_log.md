# Q3 Experiment Log – ESG Message Triage

## Purpose
The aim of this experiment was to test whether a large language model could classify ESG-related operational messages and recommend an appropriate operational response.

## Categories Used
- WATER_FACILITIES
- ENERGY
- WASTE_RECYCLING
- ACCESSIBILITY
- PROCUREMENT_GOVERNANCE

## Test Message 1
"There is a water leak in Building C that has been running all morning."

### LLM Result
Category: WATER_FACILITIES  
Urgency: HIGH  
Follow-up required: Y  
Recommended team: Facilities Maintenance

### Hugging Face Zero-Shot Result
Top label: water facilities  
Confidence score: approximately 0.956

### Observation
Both approaches classified the message as a water/facilities issue. The LLM provided additional operational information such as urgency, follow-up and escalation reasoning.

---

## Test Message 2
"The accessible entrance near the main building has been blocked for two days."

### LLM Result
Category: ACCESSIBILITY  
Urgency: HIGH  
Follow-up required: Y  
Recommended team: Facilities Management

### Hugging Face Zero-Shot Result
Top label: accessibility  
Confidence score: approximately 0.961

### Observation
Both approaches agreed on the accessibility category. The result was clear because the message directly described an accessibility barrier.

---

## Test Message 3
"I want to report that one of our suppliers may not meet our sustainability policy."

### LLM Result
Category: PROCUREMENT_GOVERNANCE  
Urgency: MEDIUM  
Follow-up required: Y  
Recommended team: Procurement and ESG Governance

### Hugging Face Zero-Shot Result
Top label: procurement governance  
Confidence score: approximately 0.746

### Observation
Both methods selected procurement governance, but the Hugging Face confidence score was lower than for the other two messages. This indicates greater uncertainty because the supplier issue is more governance-related and less directly expressed.

## Overall Comparison
The LLM and Hugging Face classifier produced consistent top-level categories for all three test messages. The zero-shot classifier was useful as a baseline because it provided category confidence scores. The LLM was more useful for operational triage because it also produced urgency, follow-up requirements, recommended teams and escalation reasons.

## Limitations
The experiment used only three messages, so it does not demonstrate performance across every possible ESG issue. LLM outputs may also hallucinate or assign incorrect urgency where the input is unclear. Human review should therefore be used for high-risk, uncertain or sensitive cases.

## Deployment Concept
A cloud deployment could use Azure Logic Apps or a service portal for message intake, Azure Functions for processing, an Azure OpenAI endpoint for classification, JSON validation and routing rules, and Azure storage/logging tools for audit evidence.
