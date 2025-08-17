# Projet Piper TTS

Ce référentiel contient un modèle de synthèse vocale (TTS) basé sur l’architecture VITS, entraîné avec Piper sur un jeu de données audio personnalisé. Le modèle a été peaufiné, exporté au format ONNX, et testé pour générer des fichiers WAV. Une configuration Docker est incluse pour le déploiement.

## Fichiers
- `model_2195.onnx` : Modèle ONNX entraîné (63.5 Mo).
- `model_2195.onnx.json` : Configuration du modèle (7 Ko).
- `config.json` : Configuration de l’entraînement.
- `dataset.jsonl` : Jeu de données prétraité (19.6 Mo).
- `test_onnx.wav` : Sortie audio générée (78 Ko).
- `test_existing.wav`, `test_lessac.wav`, `test_final.wav` : Autres fichiers WAV de test.
- `piper_setup_commands.txt` : Commandes de configuration et d’entraînement.
- `docker_piper.tar.gz` : Archive Docker (2 Go, [Google Drive](https://drive.google.com/file/d/1J8MghFESQgD3dFPfKh9O9NFVoO3wGWb6/view?usp=sharing)).
- `lightning_logs/` : Journaux TensorBoard et checkpoints.

## Résultats de l’entraînement
- Entraînement effectué sur Google Colab avec GPU, à partir de `lessac.ckpt` jusqu’à `epoch=2195-step=1452116.ckpt`.
- Métriques (TensorBoard, `version_0`, étape 679449) :
  - `loss_disc_all` : 2.0783 (brut), 2.0655 (lissé), stable avec oscillations.
  - `loss_gen_all` : 36.3367 (brut), 37.9235 (lissé), descendante mais élevée.
- Hyperparamètres (`hparams.yaml`) :
  - `batch_size: 1` (faible, à optimiser).
  - `learning_rate: 0.0002`.
  - `sample_rate: 22050` (qualité moyenne).
- Les logs complets (jusqu’à 1452116 pas) doivent être localisés.

## Instructions d’installation
1. Consultez `piper_setup_commands.txt` pour la configuration et l’entraînement.
2. Déploiement Docker :
   - Téléchargez `docker_piper.tar.gz` depuis [Google Drive](https://drive.google.com/file/d/1J8MghFESQgD3dFPfKh9O9NFVoO3wGWb6/view?usp=sharing).
   - Chargez l’image : `docker load -i docker_piper.tar.gz`.
   - Suivez `piper_setup_commands.txt` pour lancer le conteneur.
3. Visualisation des métriques :
   - Copiez `lightning_logs/version_X` dans `/content/training_dir/lightning_logs/`.
   - Lancez TensorBoard : `%tensorboard --logdir /content/training_dir/lightning_logs`.

## Prochaines étapes
- Localiser les logs TensorBoard pour l’étape 1452116.
- Évaluer la qualité de `test_onnx.wav`.
- Optimiser `batch_size` et relancer l’entraînement si nécessaire.


## Licence
[À spécifier, par exemple, MIT]. Consultez le fichier `LICENSE`.
