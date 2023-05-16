# polkadot-developer-data

The goal of this project is to develop a configurable crawler that finds GitHub repositories of projects building on Polkadot. 

These repositories are collected using a set of static heuristics as well as GitHub search queries that can be found in a configuration file.  

A binary is built that can be run periodically, with different configuration files. 

Some additional context can be found [here](https://forum.parity.io/t/developer-activity-getting-it-right/1695).


## Configuration 

```
config:
  output_path: './repos.csv'
  compute_stats: off 

rules:
  js:
    - '@polkadot filename:package.json'
    - '@talisman filename:package.json'
	
  rust:
    - 'frame filename:Cargo.toml'

```


