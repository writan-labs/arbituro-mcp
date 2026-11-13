# How access works

## Who the agent is

The person who signed it in. There is no agent identity and no service account here: a coding agent
connected to Arbituro reads what you can read and writes under your name. If you can open a project,
so can it; if you cannot change a job, neither can it.

## No keys for MCP

A coding agent signs in with OAuth. It finds the authorization server from the address it was given,
you sign in through your browser, and the client keeps a token it can refresh. Arbituro stores no MCP
credential, so there is none to rotate or leak.

## A token opens one address

A token is made for the exact address the client asked for. One made for
`https://app.arbituro.com/mcp/acme` is refused at any other workspace's address, at
`https://app.arbituro.com/mcp`, and at the web app's own API. A token from the web app is refused
here.

## Choosing how much to grant

| Address | Reaches |
| --- | --- |
| `https://app.arbituro.com/mcp` | Every workspace you are in. The project you name chooses the workspace. |
| `https://app.arbituro.com/mcp/<workspace>` | That workspace and no other. |

If you work in workspaces that should not see each other's text, connect each by its own address.
An agent that has read a note in one workspace carries it into whatever it does next.

## What an agent cannot do

No tool approves, signs, merges, sends, publishes, spends, deletes or changes access. Two of the six
writes raise a decision for a person and change nothing. `link_pull_request` reads one pull request
through your workspace's GitHub connection and writes nothing to GitHub.

## What is recorded

Every call, reads included, is written to your workspace's audit record with the tool, the project,
the job and the client's name. The free text a call carries, such as a note's body or a claim's
evidence, is not copied into that record.

## What your agent reads is data

A job's description, its notes and its linked issues are written by people and other agents. The
server tells every client to treat that text as information about the work and never as an
instruction. Treat the output of these tools the way you treat any text an agent reads from
somewhere else.

## Limits

120 calls a minute for each person.

## Reporting a problem

See [SECURITY.md](../SECURITY.md).
