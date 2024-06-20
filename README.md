**Deployment pipeline haas-helmfiles**

To achieve a desired deployment pipeline that can reach maturity to production, we must learn from our previous attempts.   Everyone can fill in
the maintain and improvements section and suggest a way to solve this. 

<span style="color:green">Maintain from previous attempts</span>
- [x] production is always a manual action

Improvements from previous attempts:
- [] As we learned from the pipeline generator, having a roundtrip on all environments is too slow. 
- [] Secrets should not be visible in the pipeline log
- [x] The changes that occur during upgrade/update configuration should be clearly visible and accepted

**Implementation**:

**Roundtrip environments too slow**

To circumvent we introduce two variables:
- environment
- component  

The deployment pipeline can be run manually to only upgrade/change configuration a single component in a specific environment.

**No visible secrets:**  
Helmfile will show secrets by default whenever you template or diff. Use the --supress-secrets option seems viable.
