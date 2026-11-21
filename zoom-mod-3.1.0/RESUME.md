# Zoom 3.1.0 : zoom etendu jusqu a environ x70

Fichier principal : zoom-3.1.0.hmod (paquet wasm Horizon, API 0.2, cote client)
SHA-256 : cc74b01040c06db61eea93e0716596e1cc1747f19a11e8f19e73d3a228abec3e

## Pourquoi pas x1 000 000 000
Le moteur borne le zoom d un mod a 10x (native_zoom_now) et n accepte un champ de vision (compute_fov) qu entre 1 et 179 degres. Le maximum atteignable par un mod est donc d environ x70 (a FOV 70).

## Modifications (src/lib.rs)
- Molette : limite 10x -> 70x (MAX)
- Zoom moteur : plafonne a 10x (ENGINE_MAX), comme le moteur l impose
- Hook compute_fov : au-dela de 10x, le champ de vision est reduit du facteur restant (jamais sous 1 degre)
- Hook calculate_player_turn : l option Ralentir la rotation continue de ralentir la souris au-dela de 10x
- Tests : 7/7 OK (un nouveau test pour la partie au-dela de 10x)
- Version 3.0.3 -> 3.1.0 ; README mis a jour ; voir modifications.diff

## Build
cargo horizon-mod build --wasm : cargo-horizon-mod au commit .github/horizon-rev (8f83e5c), SDK f00125f (signature verifiee), Rust 1.99.1 (commit 58cf8f9c, depuis conda-forge).
cargo horizon-mod check : OK (paquet non signe).

## Non teste en jeu
Le rendu et la sensibilite au-dela de 10x n ont pas pu etre testes. Le zoom lisse (smooth) peut produire un petit saut au passage des 10x.

## Installation
Copier zoom-3.1.0.hmod dans le dossier horizon-mods/ du jeu (ou via le launcher). Retirer l ancien Zoom pour eviter un doublon.
