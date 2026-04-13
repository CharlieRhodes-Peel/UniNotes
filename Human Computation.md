Outsourcing computation to a crowd of people

For more about crowd sourcing look at [[Incentives]] and [[Expert Crowdsourcing]]
# What problems are suitable for HComp?
Problems that are **hard for computers** but **easy** for *humans*, and Ideally tasks that are quickly explained to non-experts,  fast to complete and ones that can be **decomposed** into **smaller** tasks. Also the tasks should be **robust** to some **noise**. To sum this all up **data collection**

# Amazon ![[Mechanical Turk]]
# Soylent : *Find-Fix-Verify* Pattern
Is a word processor with "a crowd inside". Text editing is a complex, open-ended task, and many people can get it wrong. Simply, they follow a **Find-Fix-Verify** Pattern:
- **FIND**: users highlight sections of a problem that need attention (e.g parts of a text that can be shortened, sentences that contain mistakes, etc.)
- **FIX**: Users propose improvements for the most commonly highlighted sections only (one improvement per user)
- **VERIFY**: Users vote on the best (or worst) improvements

You can see that this **DECOMPOSES** the problem down into simple **HCOMP Suitable** tasks! Each of these tasks could be posted to Mechanical Turk.

## Why it works so well
- Separates the **find** and **fix** users to avoid lazy users (those who focus on the easiest fixes)
- Local work enables parallel processing and allows edits to be mapped clearly to sections of text
- Verification ensure quality (workers often better at verification than producing high-quality output themselves)
- Decisions within each stage are independent
- Small tasks decrease the likelihood of errors

# Implementing HComp Workflows
Building and testing complex HComp workflows is challenging, they can be costly and take many hours or days to be completed. How do you debug / work on a system like this?

## The *Crash-and-Rerun* Pattern
Program is re-executed on failure, but some function results are cached:
- HComp results (HITs)
- Nondeterministic functions
- Functions with side effects
### Benefits of this
- Incremental development
- Easy to use
- Easy to add debugging output
### Diagram
![[Pasted image 20260310144533.png]]

# Quality Control
Can calculate some metrics to try and get some more accurate results from the data

| Metrics   | Equation                        |
| --------- | ------------------------------- |
| Precision | tp / (tp + fp)                  |
| Recall    | tp / (tp + fn)                  |
| Accuracy  | (tp + tn) / (tp + tn + fp + tn) |
where: (examples given as a diagnosis for cancer)
```
tp = true_positive # Test said they have cancer and they do
tn = true_negative # Test said they have cancer and they don't
fp = false_positive # Test said they don't have cancer and they do (bad)
fn = false_negative # Test said they don't have cancer and they don't
```