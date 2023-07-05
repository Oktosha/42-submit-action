# 42-submit-action
A github action that submits specified part of the repo to intra.42.fr

# 🛑 Warning! Work in progress! 🛑

Todo:

+ Better parameters
    * passing author and commit message as optional parameter (for manual dispatch)
    * option to deduce the author and the message from the latest commit
+ Test commiting the whole repo and subdirs
    * multiple submitted dirs
    * submodules handling
    * more tests on submitting the whole repo
+ nice errors
    * message when there is nothing to commit
    * when the code-to-submit dir doesn't exist
    * when the ssh key doesn't work
    * ...
+ Example workflows (especially examples that use event_dispatch and change commit message)
+ Docs overall

# Things to read while the docs are absent

Example usage in a minishell project repo:
https://github.com/Oktosha/codam-minishell/blob/920cc45715a3d70bb6be984979ced78aa3a34d1f/.github/workflows/submit.yml

Super insightful read on ssh-agent: http://blog.joncairns.com/2013/12/understanding-ssh-agent-and-ssh-add/

## Notes

A sensetive env variable is "unset" by assigning an empty line to it

```yaml
run: echo "SSH_AUTH_SOCK=" >> "$GITHUB_ENV"
```

At the moment of writing there is no way to *unset* an env variable in an action, so I only override it https://github.com/actions/runner/issues/1126
