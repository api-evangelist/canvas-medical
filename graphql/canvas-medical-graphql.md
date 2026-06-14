# Canvas Medical GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Canvas Medical EHR platform's data model, derived from its FHIR R4 REST API and Python SDK capabilities. Canvas Medical is a developer-first EHR platform providing comprehensive clinical workflow support for virtual and value-based care organizations.

The schema covers patient management, clinical documentation, medication management, scheduling, lab orders, tasks, referrals, immunizations, allergies, vital signs, and administrative workflows.

## Source

- API Documentation: https://docs.canvasmedical.com/api/
- SDK Documentation: https://docs.canvasmedical.com/sdk/
- FHIR R4 Resources: 41 supported resources (21 with write capabilities)
- Authentication: OAuth 2.0 Client Credentials and Authorization Code (SMART on FHIR)

## Schema File

See `canvas-medical-schema.graphql` for the full type definitions.

## Key Domain Areas

### Patient Management
Types: `Patient`, `PatientDetails`, `MRN`, `PatientIdentifier`

Represents FHIR Patient resources with demographic information, medical record numbers, and identifiers from external systems.

### Appointments and Scheduling
Types: `Appointment`, `AppointmentDetails`, `AppointmentType`, `AppointmentStatus`, `Schedule`, `Slot`, `SlotDetails`, `Availability`

Covers the full scheduling lifecycle from slot availability through appointment booking and status tracking.

### Encounters and Clinical Notes
Types: `Encounter`, `EncounterDetails`, `EncounterReason`, `Note`, `NoteDetails`, `NoteType`, `ClinicalNote`, `ProgressNote`, `SOAPNote`, `SOAP`

Clinical encounter documentation including SOAP-structured notes, progress notes, and encounter reasons tied to diagnoses.

### Medications
Types: `Medication`, `MedicationDetails`, `MedicationRequest`, `MedicationStatement`, `Prescription`, `PrescriptionDetails`, `ERx`

Full medication lifecycle from ordering through dispensing, including electronic prescribing (ERx) workflows.

### Allergies and Intolerances
Types: `Allergy`, `AllergyIntolerance`, `AllergyDetails`

FHIR AllergyIntolerance resources capturing substance, reaction, severity, and clinical status.

### Immunizations
Types: `Immunization`, `ImmunizationDetails`, `VaccineCode`

Vaccine administration records with CVX codes and administration details.

### Conditions and Problems
Types: `Condition`, `ConditionDetails`, `ICD10`, `Problem`

Active problem list items and historical conditions coded with ICD-10.

### Vital Signs
Types: `VitalSign`, `BloodPressure`, `Temperature`, `Weight`, `Height`, `BMI`

Structured vital sign observations following FHIR Observation patterns.

### Lab Orders and Results
Types: `LabOrder`, `LabTest`, `LabResult`

Laboratory order management and result reporting with reference ranges and interpretations.

### Tasks and Referrals
Types: `Task`, `TaskDetails`, `TaskStatus`, `Referral`, `ReferralDetails`

Care coordination tasks and specialist referrals with status tracking.

### Staff and Teams
Types: `StaffUser`, `PracticeUser`, `Team`, `TeamDetails`

Practice staff, care team members, and organizational team structures.

### FHIR and API Infrastructure
Types: `FHIR`, `FHIRBundle`, `APIKey`, `Token`, `Webhook`

Core API infrastructure types for authentication tokens, API key management, FHIR bundle transactions, and webhook configuration.

## Authentication

Canvas Medical uses OAuth 2.0 with SMART on FHIR scopes:
- Machine-to-machine: Client Credentials flow
- User-delegated: Authorization Code flow with PKCE

Tokens are short-lived JWTs. API keys are used for SDK plugin authentication.

## FHIR Compliance

All clinical types align with FHIR R4 resource definitions. The `FHIRBundle` type supports batch and transaction operations across multiple resources in a single request.
