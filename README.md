# polkadot-developer-data

The goal of this project is to develop a configurable crawler that finds GitHub repositories of projects building on Polkadot. 

These repositories are collected using a set of static heuristics as well as GitHub search queries that can be found in a configuration file.  

A binary is built that can be run periodically, with different configuration files. 

Some additional context can be found [here](https://forum.parity.io/t/developer-activity-getting-it-right/1695).


## Configuration 

A configuration file `config.yaml` is used to provide the rules used for fetching the repositories.

`config.yaml`

```
rules:
  js:
    - '@polkadot filename:package.json' # matching polkadot JS api
    - '@talisman filename:package.json' # matching talisman wallet integration
	
  rust:
    - 'frame filename:Cargo.toml' # project uses frame

```

## Installing

Clone the repository & run `cargo build`.

## Running

For ideal automation, the target usage should be:

```
./crawler -c ./config.yaml -o ./repos_202301.csv
```

Note that the `GITHUB_ACCESS_TOKEN` will be automatically fetched from the system environment variables, if present. 

It can be overriden with:

```
GITHUB_ACCESS_TOKEN="..." ./crawler -c ./config.yaml -o ./repos_202301.csv
```