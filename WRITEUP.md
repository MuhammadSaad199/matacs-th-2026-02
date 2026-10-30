Questions to answer

1- AI vs rules: I used AI for data extraction, while the rest of the process was handled through code, including data validation, checking mandatory requirements, scoring, and ranking. I chose code based logic to maintain consistency and avoid potential inconsistencies that could arise if AI were used to evaluate other criteria.


2- Consistency and explainability: Even if the same proposals are uploaded two or three times, they will always receive the same scores because the scores are calculated using a fixed formula. This ensures consistent and repeatable results. Also the data used to calculate scores and rank the proposals will also be displayed in a table, allowing reviewers to see exactly what the ranking is based on and make informed decisions.


3- Human in the loop: After the proposals are ranked, reviewers can review the results and either confirm the ranking or override it, since the final decision-making authority rests with them. For every action they take, whether approving or rejecting a proposal, they must provide a reason, and every action they perform will be recorded in an audit log for future reference and verification. These logs can be reviewed later to cross check decisions and maintain transparency and accountability throughout the process.


4- Changing criteria: Whenever the admin updates the evaluation criteria or weights, the previous version will be saved, and the proposals will be re-ranked using the updated criteria. Existing rankings will remain under the previous criteria, while the new rankings will be generated using the updated criteria. Each new criteria version will have a unique identifier to prevent conflicts and ensure proper version tracking.


5- Risks: 
Wrong Extraction: After AI extracts the data, we cross check it using code to verify whether the extracted values are correct. If any issues are detected, the status is marked as "Flagged" for manual review.

Made-up Facts: If AI cannot find certain information, it returns null instead of guessing or making up values. If any required value is missing, the status is automatically marked as "Flagged" for review.

Bias: AI is only used to extract data. The scores are calculated based on the available extracted data and the evaluation criteria defined by the admin, not on any other factors. The same rules and criteria are applied consistently to all proposals, ensuring a fair and unbiased evaluation.

Manipulation: AI extracts the data, and code cross checks the extracted information before calculating scores based on the predefined evaluation criteria. If any hidden or any instructions are detected in a proposal, they are flagged as suspicious text, and the proposal's status is marked as "Flagged" for manual review.

Cost Efficiency: All the data is extracted when the PDF is uploaded for the first time. Even if the admin changes the evaluation criteria or weights later, the system reuses the previously extracted data instead of calling AI again. This reduces unnecessary AI calls and keeps operational costs low.