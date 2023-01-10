# octokit-pinned-issues

> Octokit plugin to manage pinned issues for a repository

[![Test](https://github.com/gr2m/octokit-pinned-issues/actions/workflows/test.yml/badge.svg)](https://github.com/gr2m/octokit-pinned-issues/actions/workflows/test.yml)

There is no REST API for the new ["Pinned Issues"] feature. This Octokit plugin uses GraphQL under the hood to provide simple methods to manage a repository’s pinned issues.

## Usage

```js
const Octokit = require("@octokit/rest").plugin(
  require("octokit-pinned-issues")
);

const octokit = new Octokit();

octokit
  .getPinnedIssues({
    owner: "repo-name",
    repo: "repo-name",
  })
  .then((issues) => {});
octokit
  .pinIssue({
    owner: "repo-name",
    repo: "repo-name",
    number: 123,
  })
  .then((issue) => {});
octokit
  .unpinIssue({
    owner: "repo-name",
    repo: "repo-name",
    number: 123,
  })
  .then((issue) => {});
```

An `issue` object can have the following properties

```js
[
  {
    id: "MDU6SXNzdWU...",
    number: 71,
    state: "OPEN",
    title: "issue title",
    body: "issue description",
    locked: false,
    active_lock_reason: null,
    milestone: {
      id: "MDk6TWlsZXN...",
      state: "OPEN",
      title: "Funk",
      description: "Get Funky!",
    },
    labels: [
      {
        id: "MDU6TGFiZWw...",
        name: "foo",
        description: null,
        color: "ededed",
      },
    ],
    assignees: [
      {
        login: "gr2m",
        id: "MDQ6VXNlcj...",
        avatar_url: "https://avatars3.githubusercontent.com/u/39992?v=4",
      },
    ],
  },
];
```

## LICENSE

[MIT](LICENSE)
