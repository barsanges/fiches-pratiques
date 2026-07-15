# Rust

# Rustup

`rustup update` : mettre à jour l'installation Rust

`rustup self uninstall` : désinstaller Rust et Rustup

## Cargo

`cargo new FOO` : créer un nouveau projet dans le dossier FOO (le repo
git est initialisé au passage)
  * `cargo new FOO --bin` : créer un projet pour une application
    (défaut)
  * `cargo new FOO --lib` : créer un projet pour une bibliothèque

`cargo build` : compiler le projet en debug
  * `cargo build --release` : compiler le projet en release

`cargo run` : compiler le projet et le lancer

`cargo check` : s'assurer que le code compile sans produire
l'exécutable
