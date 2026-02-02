---
name: patient-intake
description: "Automate gathering of patient medical histories. Use this skill when creating patient intake forms, anamnesis, or collecting medical history. Triggers: patient intake, anamnese, formulário de paciente, histórico médico, medical history, new patient form, patient registration."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Patient Intake: Comprehensive Medical History Forms

## Overview
This skill is designed to streamline and standardize the collection of patient information by generating and processing comprehensive medical history forms. It helps healthcare professionals gather detailed data from patients in a structured format, covering everything from personal details and chief complaints to past medical history, family history, social history, and review of systems. By automating this process, the skill reduces administrative workload, minimizes errors, and ensures that clinicians have a complete and accurate patient profile before the first consultation.

## Automatic Triggers

**ALWAYS activate this skill when user mentions:**
- Keywords: patient intake, anamnese, formulário de paciente, histórico médico, medical history, new patient form, patient registration, medical questionnaire, health history
- Phrases: "criar um formulário para paciente novo", "coletar histórico médico do paciente", "gerar anamnese", "create a new patient form", "gather medical history"
- Context: Any discussion about creating forms or questionnaires to collect patient health information before a consultation.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **New Patient Registration:** When a new patient schedules an appointment, this skill can be used to send them a comprehensive intake form to complete beforehand.
- **Pre-Consultation Information Gathering:** For follow-up appointments, specific sections of the form can be used to get updates on the patient's condition, new symptoms, or changes in their lifestyle.
- **Specialty-Specific Intakes:** The skill can generate specialized forms for different medical fields, such as orthopedics, cardiology, or mental health, by including relevant questions for each specialty.
- **Clinical Research:** Researchers can use this skill to create detailed questionnaires for study participants, ensuring consistent data collection across the cohort.
- **Telemedicine Appointments:** In a remote setting, having a detailed medical history is even more critical. This skill ensures the physician has all the necessary information before the virtual consultation begins.

## Core Capabilities

### 1. Dynamic Form Generation
The skill can generate customized intake forms based on the specific needs of the clinic or the patient's presenting complaint. You can specify which sections to include or exclude.

**Example: Generating a form for a new patient with a musculoskeletal issue.**
```bash
# This is a conceptual example of how a tool could use this skill
manus --skill patient-intake --action generate-form --type new-patient --specialty orthopedics
```

### 2. Multi-Language Support
The forms can be generated in multiple languages to accommodate a diverse patient population. The default language is English, but you can specify others as needed.

### 3. Structured Data Output
After the patient completes the form, the skill processes the information and organizes it into a structured format (e.g., JSON or a formatted Markdown file). This makes it easy to integrate with Electronic Health Record (EHR) systems.

**Example of a JSON output:**
```json
{
  "patient_details": {
    "full_name": "John Doe",
    "dob": "1985-04-12",
    "gender": "Male"
  },
  "chief_complaint": "Chronic lower back pain for the last 6 months.",
  "history_of_present_illness": {
    "onset": "6 months ago",
    "location": "Lower back, radiating to the left leg",
    "duration": "Constant, with intermittent sharp pains",
    "character": "Dull ache with episodes of sharp, shooting pain",
    "aggravating_factors": ["Sitting for long periods", "Lifting heavy objects"],
    "relieving_factors": ["Stretching", "Lying down"],
    "timing": "Worse in the morning and after a long day of work",
    "severity": "7/10"
  },
  "past_medical_history": [
    {
      "condition": "Hypertension",
      "diagnosed_year": 2018
    },
    {
      "condition": "Appendectomy",
      "surgery_year": 2005
    }
  ]
}
```

### 4. Template-Based Approach
The skill includes several pre-built templates for different types of intake forms. These can be used as-is or customized.

- **`full_intake.md`**: A comprehensive form for new patients.
- **`follow_up.md`**: A shorter form for returning patients.
- **`pain_management.md`**: A specialized form for patients with chronic pain.
- **`mental_health.md`**: A form focused on psychological and emotional well-being.

## Step-by-Step Workflow

1.  **Select or Create a Form Template:**
    -   Start by choosing one of the existing templates or create a new one. To see available templates, you could conceptually run a command like:
        ```bash
        ls /skills/patient-intake/templates
        ```

2.  **Customize the Form (Optional):**
    -   If needed, edit the template to add, remove, or modify sections and questions. For example, you might want to add a section on dietary habits for a nutritional consultation.

3.  **Generate the Patient-Facing Form:**
    -   Use the skill to generate a user-friendly version of the form (e.g., a fillable PDF or a web form). This step would typically involve another tool that can render the form.

4.  **Patient Completes the Form:**
    -   The patient fills out the form and submits it.

5.  **Process the Submitted Data:**
    -   The skill takes the completed form as input and extracts the information into a structured format.

6.  **Review and Integrate:**
    -   The healthcare professional reviews the structured data for completeness and accuracy. The data can then be manually or automatically entered into the patient's EHR.

## Best Practices

-   **Be Clear and Concise:** Use simple language in your forms. Avoid medical jargon as much as possible.
-   **Ensure Patient Privacy:** Always handle patient data with the utmost confidentiality and in compliance with regulations like HIPAA. When using this skill, ensure the environment is secure.
-   **Start with a Template:** It's often easier to start with a comprehensive template and remove what you don't need, rather than starting from scratch.
-   **Review Before Finalizing:** Always have a clinician review the generated forms and the processed data to ensure everything is medically sound and accurate.
-   **Combine with Other Skills:** This skill can be combined with others, such as a `notifications` skill to send reminders to patients to fill out the form, or a `data-visualization` skill to create summaries of the patient's history.

## Examples

### Example 1: Creating a Full Intake Form for a New Patient

This example shows the content of a `full_intake.md` template.

```markdown
# New Patient Intake Form

## Personal Information
- Full Name:
- Date of Birth:
- Gender:
- Address:
- Phone Number:
- Email Address:
- Emergency Contact Name & Phone:

## Chief Complaint
What is the main reason for your visit today?

## History of Present Illness
- When did the problem start?
- What were you doing when it started?
- Where is the problem located?
- Does the pain radiate to other areas?
- How long do the symptoms last?
- What does the pain feel like (e.g., sharp, dull, aching, burning)?
- What makes it better?
- What makes it worse?
- How severe is the pain on a scale of 1-10?

## Past Medical History
- **Medical Conditions:** (e.g., Hypertension, Diabetes, Asthma)
- **Surgeries:** (Include type and year)
- **Hospitalizations:** (Include reason and year)
- **Allergies:** (Medications, food, environmental)
- **Current Medications:** (Include name, dose, and frequency)
- **Immunizations:** (Are you up to date?)

## Family History
Do any of your immediate family members (parents, siblings, children) have a history of the following?
- Heart Disease
- Cancer (specify type)
- Diabetes
- High Blood Pressure
- Stroke
- Mental Health Conditions
- Other:

## Social History
- **Marital Status:**
- **Occupation:**
- **Living Situation:**
- **Tobacco Use:** (Never, former, current - specify amount and duration)
- **Alcohol Use:** (Never, occasional, daily - specify amount)
- **Recreational Drug Use:** (Never, former, current - specify type)
- **Diet:** (e.g., balanced, vegetarian, vegan, low-carb)
- **Exercise:** (Type, frequency, duration)

## Review of Systems
Are you currently experiencing any of the following? (Please check all that apply)

- **General:** [ ] Fever, [ ] Chills, [ ] Fatigue, [ ] Weight loss/gain
- **Head/Eyes/Ears/Nose/Throat (HEENT):** [ ] Headaches, [ ] Vision changes, [ ] Hearing loss, [ ] Sore throat
- **Cardiovascular:** [ ] Chest pain, [ ] Palpitations, [ ] Swelling in legs
- **Respiratory:** [ ] Shortness of breath, [ ] Cough, [ ] Wheezing
- **Gastrointestinal:** [ ] Nausea, [ ] Vomiting, [ ] Diarrhea, [ ] Constipation, [ ] Abdominal pain
- **Genitourinary:** [ ] Painful urination, [ ] Frequent urination, [ ] Blood in urine
- **Musculoskeletal:** [ ] Joint pain, [ ] Muscle weakness, [ ] Back pain
- **Neurological:** [ ] Dizziness, [ ] Numbness, [ ] Tingling, [ ] Seizures
- **Psychiatric:** [ ] Anxiety, [ ] Depression, [ ] Mood swings
- **Skin:** [ ] Rashes, [ ] Itching, [ ] Sores

```

### Example 2: Creating a Specialized Pain Management Form

This is a snippet from a `pain_management.md` template, focusing on pain-specific questions.

```markdown
# Pain Management Intake Form

## Pain Assessment

- **Pain Diagram:** Please mark the areas on the diagram below where you feel pain.
  *(A body diagram would be included here in a graphical format)*

- **Pain Description:**
  - What words best describe your pain? (e.g., Aching, Burning, Stabbing, Throbbing, Sharp, Dull)
  - Is the pain constant or does it come and go?

- **Pain Triggers:**
  - What activities or movements trigger your pain?
  - Are there specific times of day when the pain is worse?

- **Previous Treatments:**
  - What treatments have you tried for this pain? (e.g., Medications, Physical Therapy, Injections, Surgery)
  - How effective were these treatments?

- **Pain Impact on Daily Life:**
  - How does the pain affect your ability to work?
  - How does it affect your sleep?
  - How does it affect your mood and relationships?

```

## References

-   [AHRQ - Health Literacy Universal Precautions Toolkit](https://www.ahrq.gov/health-literacy/improve/precautions/index.html)
-   [HIPAA Journal - HIPAA Compliance Information](https://www.hipaajournal.com/)
-   [OpenEHR - Open specifications for a shared health record](https://www.openehr.org/)

