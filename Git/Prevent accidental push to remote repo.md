
For example, you work at a company and may need to fetch/pull from upstream but must not push to it (for security reason):

```sh
git set-url --push <remote name> INVALID_URL
```