# FHIR Synthetic Dataset Generation

## Abstract

- When creating the FHIR synthetic datasets, we were interested in gathering the records of 100 patients and including resources that can be mapped to phenopackets. To ensure the same patients were retrieved with each query, the same 100 patient IDs were included in queries. Datasets with resources Condition, Procedure and DiagnosticReport were created using SyntheticMass, which is an environment hosting open-source patient data [1,2].
- The first dataset (conditions_hypertension.json) involves the Condition resource, and includes all records pertaining to the code 38341003 (Hypertension) of the 100 patients queried. An additional Condition dataset (conditions.json) was created, where, rather than retrieving a specific Condition code, the first 100 conditions were queried and then passed with the 100 patients. 
- When creating the Procedure resource dataset (procedure.json), those with code 395123002 (urine screening test for diabetes) within the records of the predetermined 100 patients were retrieved. DiagnosticReport dataset (diagnostic_report.json) was retrieved by including everything within diagnostic report records of the 100 patients queried. Due to the nature of the server, the number of retrieved codes is limited to 100, so for the Condition, Procedure, Observation (observations.json), and DiagnosticReport datasets, only the first 100 results are retrieved. It is therefore possible that some patients do not have a Condition, Procedure, Observation or DiagnosticReport code, as only the first 100 results of these resources were retrieved. 
- We were also interested in generating a dataset with the Specimen resource, and turned to the HAPI server to do so, rather than SyntheticMass. The HAPI server is also open-source and is Apache 2.0 licensed [3]. The generated Specimen dataset (specimens.json) consists of 100 specimen IDs, with reference to the associated Patient ID. It should be noted that the Specimen data was post-processed to add patient IDs. Since the data comes from two different sources, SyntheticMass and HAPI, it has the potential to be clinically inconsistent and thus, cannot be used for clinical discovery. 
- This was done with the goal of testing the functionality of our service to work with a FHIR data format, particularly, to test the ingestion algorithm. Overall, all generated datasets were successfully ingested into the metadata service.


### Citations
[1] https://synthea.mitre.org/

[2] Jason Walonoski, Mark Kramer, Joseph Nichols, Andre Quina, Chris Moesel, Dylan Hall, Carlton Duffett, Kudakwashe Dube, Thomas Gallagher, Scott McLachlan, Synthea: An approach, method, and software mechanism for generating synthetic patients and the synthetic electronic health care record, Journal of the American Medical Informatics Association, Volume 25, Issue 3, March 2018, Pages 230–238, https://doi.org/10.1093/jamia/ocx079

[3] http://hapi.fhir.org/about


