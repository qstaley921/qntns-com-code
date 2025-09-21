# QNTN notes
1. 


# Best Practices for Feature Development with Git

  1. Always Work on Feature Branches

  git switch -c feature/user-authentication
  git switch -c fix/login-bug
  git switch -c experiment/new-ui
  Never commit directly to main - this protects your working code.

  2. Keep Main Branch Clean

  - Main should always be deployable
  - Only merge completed, tested features
  - Use branch protection rules on GitHub to enforce this

  3. Small, Frequent Commits

  git add specific-file.js
  git commit -m "Add user validation logic"
  # Better than one huge commit with everything

  4. Test Before Merging

  # On your feature branch
  npm test                    # Run tests
  npm run build              # Ensure it builds
  git switch main
  git pull origin main       # Get latest changes
  git switch feature-branch
  git rebase main            # Resolve conflicts early

  5. Use Pull Requests (GitHub)

  - Create PR instead of merging directly
  - Enables code review and CI checks
  - Documents the change with discussion

  6. Backup Your Work

  git push origin feature-branch    # Push feature branch to remote
  # Even if not ready - gives you backup

  7. When Things Go Wrong

  # If you mess up your feature branch
  git switch main                   # Go back to safety
  git branch -D broken-feature      # Delete broken branch
  git switch -c feature-retry       # Start fresh

  # If you accidentally commit to main
  git reset --hard HEAD~1           # Undo (if not pushed)
  git switch -c fix-branch HEAD~1   # Move commits to new branch

  8. AI Development Workflow

  # Start feature
  git switch -c ai/implement-search

  # Let AI write code, commit frequently
  git add .
  git commit -m "AI: Add search component structure"

  # Test the AI's work
  npm test

  # If it works, continue
  git commit -m "AI: Add search functionality"

  # If it breaks, easily revert
  git reset --hard HEAD~1  # Or go back to last working commit

  9. Stash for Quick Switches

  # If you need to quickly check main
  git stash                  # Save current work
  git switch main           # Check main branch
  git switch feature-branch
  git stash pop             # Resume work

  10. Branch Naming Conventions

  - feature/description - New features
  - fix/description - Bug fixes
  - experiment/description - Trying things out
  - ai/description - AI-assisted development

  This approach lets you experiment freely while keeping main stable and always having a
  way back to working code.