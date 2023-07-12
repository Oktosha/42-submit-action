# 42-submit-action

A github action that submits specified part of the repo to intra.42.fr. The author and the email are deduced from the latest commit.

# 🛑 Warning! Work in progress! 🛑

Current ready-to-use version is [v0.1.1](https://github.com/Oktosha/42-submit-action/tree/v0.1.1).

It is good enough to work for [our minishell](https://github.com/Oktosha/codam-minishell) but that's it.

# Example usage

```yaml
- uses: Oktosha/42-submit-action@v0.1.1
        with:
          code-to-submit: kotishell
          intra-repo: ${{ secrets.INTRA_REPO_URL }}
          intra-ssh-key: ${{ secrets.SSH_PRIVATE_KEY_FOR_INTRA }}
```

You can find the full example in [our minishell repo](https://github.com/Oktosha/codam-minishell).

# Todo

+ Better parameters
    * passing author and commit message as optional parameter (can be especially nice for manual dispatch)
+ Test commiting the whole repo and subdirs
    * multiple submitted dirs
    * submodules handling
    * testing submitting the whole repo (should work, but not tested)
    * testing starting with an empty intra repo (should work, but not tested)
+ nice errors
    * message when there is nothing to commit
    * when the code-to-submit dir doesn't exist
    * when the ssh key doesn't work
    * ...
+ More example workflows
+ Docs overall

# Things to read while the docs aren't ready

Super insightful read on ssh-agent: http://blog.joncairns.com/2013/12/understanding-ssh-agent-and-ssh-add/

## Notes

A sensetive env variable is "unset" by assigning an empty line to it

```yaml
run: echo "SSH_AUTH_SOCK=" >> "$GITHUB_ENV"
```

At the moment of writing there is no way to *unset* an env variable in an action, so I only override it https://github.com/actions/runner/issues/1126
