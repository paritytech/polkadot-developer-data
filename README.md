# polkadot-developer-data

The goal of this project is to develop a configurable crawler that finds GitHub repositories of projects building on Polkadot. 

These repositories are collected using a set of static heuristics as well as GitHub search queries that can be found in a configuration file.  

A binary is built that can be run periodically, with different configuration files. 

Some additional context can be found [here](https://forum.parity.io/t/developer-activity-getting-it-right/1695).


## Configuration 

It is necessary to have a small file to configure the script as well as add an `.env` file with your GitHub API Key.

`.env`, not added to this repository. 

```
GITHUB_ACCESS_TOKEN=...
```


`config.yaml`, included in this repository.

```
config:
  output_path: './repos.csv'
  compute_stats: off 

rules:
  js:
    - '@polkadot filename:package.json' # matching polkadot JS api
    - '@talisman filename:package.json' # matching talisman wallet integration
	
  rust:
    - 'frame filename:Cargo.toml' # project uses frame

```


