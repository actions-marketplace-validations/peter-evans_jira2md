# jira2md
[![CI](https://github.com/peter-evans/jira2md/workflows/CI/badge.svg)](https://github.com/peter-evans/jira2md/actions?query=workflow%3ACI)

A GitHub action to convert between Jira text formatting and GitHub flavored markdown

This action is a wrapper around the [jira2md](https://www.npmjs.com/package/jira2md) npm package.

## Usage

### Convert Jira -> markdown

```yml
      - uses: peter-evans/jira2md@v1
        id: jira2md
        with:
          input-text: |
            *Some bold things**
            _Some italic stuff_
            h2. H2
            [http://google.com]

      - run: echo "${{ steps.jira2md.outputs.output-text }}"
```

### Convert markdown -> Jira

```yml
      - uses: peter-evans/jira2md@v1
        id: md2jira
        with:
          input-text: |
            **Some bold things**
            *Some italic stuff*
            ## H2
            <http://google.com>
          mode: md2jira

      - run: echo "${{ steps.md2jira.outputs.output-text }}"
```

### Action inputs

| Name | Description | Default |
| --- | --- | --- |
| `input-text` | The input text to convert. | |
| `mode` | The conversion mode; `jira2md` or `md2jira`. | `jira2md` |

#### Outputs

- `output-text` - The converted text.

## License

[MIT](LICENSE)
