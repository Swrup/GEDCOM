# FamilySearch GEDCOM

The official FamilySearch GEDCOM specification for exchanging genealogical data.

This repository is for the collaborative development of the FamilySearch GEDCOM specification.
If you are looking for the specification itself, see <https://gedcom.io>.

If you are looking for FamilySearch's GEDCOM 5.5.1 Java parser, which previously had this same repository name, see <https://github.com/familysearch/gedcom5-java>


## Repository structure

- [`changelog.md`](changelog.md) is a running log of major changes made to the specification.
- [`specification/`](specification/) contains the FamilySearch GEDCOM specification:
	- `specification/gedcom-`number`-`title`.md` files are the source documents used to define the FamilySearch GEDCOM specification. It is written in pandoc-flavor markdown and is intended to be more easily written than read. It is splint into several files (ordered by the integer in their names) to facilitate comparing files.
	- In a local check-out, this is also where the build scripts place rendered files `gedcom.html` and `gedcom.pdf`; see [releases](releases/latest) for a pre-rendered copy of these.
	- [`specification/terms/`](specification/terms/)
		- YAML files to be served in the <https://gedcom.io/terms/v7/> namespace, augmenting those automatically extracted from the specification itself by [`build/uri-def.py`](build/uri-def.py).
- [`build/`](build/) contains files needed to render the specification
	- See [`build/README.md`](build/) for more
- [`extracted-files/`](extracted-files/) contains digested information automatically extracted from the specification. All files in this directory are automatically generated by scripts in the [`build/`](build/) directory.
	- [`extracted-files/grammar.abnf`](extracted-files/grammar.abnf) contains all the character-level ABNF for parsing lines and datatypes.
	- [`extracted-files/grammar.gedstruct`](extracted-files/grammar.gedstruct) contains a custom structure organization metasyntax.
	- various `.tsv` files to assist automated validation of files, including:
		- [`extracted-files/cardinalities.tsv`](extracted-files/cardinalities.tsv) with columns "superstructure type ID, substructure type ID, cardinality marker"
		- [`extracted-files/enumerations.tsv`](extracted-files/enumerations.tsv) with columns "superstructure type ID, enumeration string, enumeration ID"
		- [`extracted-files/payloads.tsv`](extracted-files/payloads.tsv) with columns "structure type ID, payload type"
		- [`extracted-files/substructures.tsv`](extracted-files/substructures.tsv) with columns "structure type ID, substructure tag, substructure type ID"
	- [`extracted-files/tags/`](extracted-files/tags/) contains summary information for each <https://gedcom.io/terms/>-based URI defined in the specification.

## Branches

- `main` contains the current release.
	Patch versions are generally pushed directly to `main` upon approval.

- `next-minor` contains a working draft of the next minor release. Changes from `main` have been discussed and approved by the working group supervising the next minor release, but have not been fully vetted and approved for inclusion in the standard and may change at any time without notice.

- `next-major` contains a working draft of the next major release. Changes from `main` have been discussed and approved by the working group supervising the next major release, but have not been fully vetted and approved for inclusion in the standard and may change at any time without notice.

- All other branches are for conversation drafts that may or may not be incorporated into a future version of the specification.

