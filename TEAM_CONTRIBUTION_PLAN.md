# FairMatch team contribution plan

This repository is the shared submission repository. `main` contains the working FairMatch baseline. Each teammate must make, test and explain a real change in the feature area assigned below. Copying unchanged files does not create a contribution and must not be presented as one.

## Required contribution evidence

Every member must:

1. Use their own GitHub account and their own assigned branch.
2. Configure Git with an email verified on that GitHub account.
3. Make a real code or automated-test change that they can explain.
4. Commit with their own author identity.
5. Push the assigned branch from their computer.
6. Open a pull request into `main` and describe the change and validation.
7. Have the pull request reviewed, then merge it using **Create a merge commit** so the original teammate commit remains visible.

GitHub normally counts a contribution after the commit reaches the default branch and its author email belongs to the contributor's GitHub account. The repository commit history and pull request remain the primary evidence.

## Member 1 — Accounts and organizations

Branch: `member-1-accounts-organizations`

Owned area: role-based login, account security/email, organization verification, administrator review, recruiter invitations and permissions.

Required real task: improve one account or organization validation path and add or extend an automated backend test proving both the allowed and rejected cases. Good targets include organization-owner permissions, recruiter suspension, verification prerequisites or verification-code validation.

Suggested files:

```text
backend/src/main/java/com/fairmatch/platform/**
backend/src/test/java/com/fairmatch/platform/**
frontend/src/components/fairmatch/account-security.tsx
frontend/src/components/fairmatch/team-access.tsx
frontend/src/components/fairmatch/organization-documents.tsx
```

Suggested commit:

```text
test(accounts): cover organization permission boundary
```

## Member 2 — Job management

Branch: `member-2-job-management`

Owned area: department and position selection, custom positions, drafts, publishing, closing and exact candidate links.

Required real task: improve job-form validation or draft behavior and add or extend a backend test. Good targets include requiring custom-position text, rejecting a position outside its department, preserving a draft field or preventing publication with an expired deadline.

Suggested files:

```text
backend/src/main/java/com/fairmatch/job/**
backend/src/test/java/com/fairmatch/WorkingFeaturesTest.java
frontend/src/components/fairmatch/recruiter-workspace.tsx
frontend/src/components/fairmatch/recruiter-dialogs.tsx
frontend/src/lib/job-options.ts
```

Suggested commit:

```text
fix(jobs): validate custom position before publishing
```

## Member 3 — Candidate journey

Branch: `member-3-candidate-journey`

Owned area: link-scoped jobs, CV extraction and confirmation, application drafts/submission, tracking, withdrawal and privacy.

Required real task: improve one candidate error or recovery flow and add a meaningful test. Good targets include restoring an application draft, distinguishing extraction failure from backend failure, validating CV confirmation or verifying permanent withdrawal cleanup.

Suggested files:

```text
backend/src/main/java/com/fairmatch/application/**
backend/src/main/java/com/fairmatch/document/**
backend/src/main/java/com/fairmatch/privacy/**
backend/src/test/java/com/fairmatch/CandidatePrivacyTest.java
frontend/src/components/fairmatch/candidate-*.tsx
document-worker/**
```

Suggested commit:

```text
fix(candidate): explain CV extraction recovery
```

## Member 4 — Application review and ranking

Branch: `member-4-application-review-ranking`

Owned area: blind review, requirement evidence, candidate messages, evidence bands, automatic explained ranking, rubric and human assessment.

Required real task: strengthen ranking correctness or explanation with an automated test. Good targets include preventing substring false positives, counting repeated evidence only once, organizing long skill evidence or explaining why an unmatched requirement receives zero points.

Suggested files:

```text
backend/src/main/java/com/fairmatch/application/AutomaticEvidenceMatcher.java
backend/src/main/java/com/fairmatch/application/RankingController.java
backend/src/test/java/com/fairmatch/RankingTest.java
backend/src/test/java/com/fairmatch/CriteriaReviewTest.java
frontend/src/components/fairmatch/candidate-ranking.tsx
frontend/src/components/fairmatch/criteria-review.tsx
```

Suggested commit:

```text
test(ranking): prevent partial-word evidence matches
```

## Member 5 — Hiring and oversight

Branch: `member-5-hiring-oversight`

Owned area: pipeline, recorded reasons, interviews, notifications, fairness checks, reports, audit, support and operations.

Required real task: improve one post-review workflow and add a meaningful test. Good targets include a stage-transition reason, interview cancellation, notification creation, report filtering or fairness/audit recording.

Suggested files:

```text
backend/src/main/java/com/fairmatch/interview/**
backend/src/main/java/com/fairmatch/audit/**
backend/src/main/java/com/fairmatch/application/GovernanceController.java
backend/src/test/java/com/fairmatch/InterviewFeaturesTest.java
frontend/src/components/fairmatch/interview-dialogs.tsx
frontend/src/components/fairmatch/governance-panel.tsx
```

Suggested commit:

```text
test(interviews): record cancellation reason and notification
```

## Manual commands for every teammate

Replace `<branch>` and the example identity with the member's real information. The email must already be verified on that GitHub account.

```powershell
git clone https://github.com/ayan-islam/FairMatch-Team-Submission.git
cd FairMatch-Team-Submission
git switch --track origin/<branch>
git config user.name "Teammate Full Name"
git config user.email "verified-github-email@example.com"
git pull --rebase origin <branch>
```

After making and testing a real change:

```powershell
git status --short
git diff
git add path\to\changed-code path\to\changed-test
git diff --staged
git commit -m "type(area): explain the real change"
git push -u origin <branch>
```

The teammate then opens GitHub, creates a pull request from `<branch>` into `main`, and adds the test results. Do not share GitHub passwords or tokens.

## Coordinator merge order

Merge one reviewed pull request at a time. After each merge, the next member rebases their branch:

```powershell
git fetch origin
git rebase origin/main
git push --force-with-lease origin <branch>
```

Use `--force-with-lease` only on the member's own branch. Resolve shared-file conflicts with both affected members present.
