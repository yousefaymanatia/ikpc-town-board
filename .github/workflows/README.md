# GitHub Actions Workflows

This project uses automated workflows to make contributing easier:

## 1. Validate Member PR
- Runs when someone opens a PR that modifies `data/members.json`
- Checks JSON syntax is valid
- Verifies all required fields are present
- Comments on PR with validation results

## 2. Auto Merge PR
- Automatically checks for merge conflicts
- If no conflicts: auto-approves and merges the PR
- If conflicts: comments with instructions to resolve
- Uses squash merge to keep history clean

## 3. Welcome New Contributor
- Triggers after PR is merged
- Adds labels to the PR
- Posts welcome message
- **Automatically invites contributor to the organization**
- Thanks the contributor

## Setup Required

### 1. Enable Workflow Permissions

Go to **Settings → Actions → General**:
- Set "Workflow permissions" to **Read and write permissions**
- Check **Allow GitHub Actions to create and approve pull requests**
- Save changes

### 2. Create Organization Invite Token (for auto org invites)

1. Go to your GitHub profile → **Settings → Developer settings → Personal access tokens → Tokens (classic)**
2. Click **Generate new token (classic)**
3. Name it: `IKPC Town Board - Org Invites`
4. Select scopes:
   - `admin:org` → `write:org` (invite users to organization)
5. Click **Generate token** and copy it

6. In your repo, go to **Settings → Secrets and variables → Actions**
7. Click **New repository secret**
8. Name: `ORG_INVITE_TOKEN`
9. Paste the token
10. Save

Now when a PR is merged:
- ✅ Auto-merged (if no conflicts)
- 🎉 Welcome message posted
- 📧 **Organization invite sent automatically**
- 🏅 User becomes a contributor

**Without the token:** Everything works except auto org invite (you'd need to invite manually).
