# schema-docs

Here are the docs for schematools.

## What is this for?

This repo exists so that there is *reduced* complexity in publishing documentation 
for bids schema tools. We don't wish to attempt to push multiple parts of the bids
specification repo to read the docs. It's much better to bodge the deployment of the
documentation for `bidsschematools` than the actual specification.

## What do I need to do to make this repo work?

1) Set up an API token with access to this repo, see 
[creating a fine grain api token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-fine-grained-personal-access-token).
2) Use the API token in step 1 to synchronize `bidsschematools` from the `bids-specification` to this repository 
via the `.github/workflows/schema_docs.yaml` by adding the
api token as secret `SCHEMA_DOCS_GITHUB_API_TOKEN`.
3) Accept in your heart that one shouldn't be making changes to the `bidsschematools` or the `docs` folder 
in *this* repository as these folders are copied over w/ each push to the bids specification

## I want to edit the read the docs render for schema code

Great, don't do it here, you'll just end up having to make a PR to `bids-standard/bids-specification`. 

~~Best~~ practice is to install dependencies from this repo's `pyproject.toml` then
view/edit the schemacode/docs from the `bids-standard/bids-specification` repo. 

That would look something like this:

```bash
pushd schema-docs && pip install .
popd
pushd bids-specification/tools/schemacode/docs && make html
```

Sorry...

Alternatively, one can also ignore this documentation and run `make html` from 
the `bids-standard/bids-specification`  repo manually installing missing libraries 
until they get things working.
