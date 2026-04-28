# Probabilité de Ruine — Modèle de Lundberg

Ce dépôt contient un projet d'étude sur la **théorie de la ruine** dans le cadre des assurances. L'objectif est de modéliser l'évolution des fonds propres d'une compagnie et d'estimer la probabilité de faillite via des simulations de Monte-Carlo, en les comparant aux résultats théoriques de Lundberg.

## 📖 Description du Modèle

Le surplus d'une compagnie d'assurance à l'instant $t$ est modélisé par le processus :
$$U(t) = u + ct - S(t)$$

Où :
* **$u$** : Fonds propres initiaux (capital de départ).
* **$c$** : Taux de prime constant (revenus).
* **$S(t)$** : Montant global des sinistres, défini par un processus de Poisson composé $S(t) = \sum_{k=1}^{N_t} X_k$.
    * $N_t \sim \text{Poisson}(\lambda)$ : Nombre de sinistres.
    * $X_k \sim \mathcal{E}(\mu)$ : Montant de chaque sinistre (loi exponentielle).

La **ruine** survient dès que le surplus devient négatif ($U(t) \leq 0$).

## 🚀 Fonctionnalités du Projet

* **Simulation de trajectoires** : Génération de trajectoires exactes du surplus sans discrétisation temporelle.
* **Estimation de $\psi(u, T)$** : Calcul de la probabilité de ruine sur un horizon fini $T$.
* **Vérification théorique** : Comparaison des résultats de simulation avec la formule de Lundberg : $\psi(u) = \rho e^{-\gamma u}$.
* **Analyse de convergence** : Étude de l'impact du nombre de simulations ($N$) et du capital initial ($u$).

## 📁 Contenu du Dépôt

* `projet1_probabilite_ruine.ipynb` : Notebook Jupyter contenant l'implémentation Python (NumPy, Matplotlib) et les visualisations.
* `proba_ruine.pdf` : Rapport détaillé présentant les démonstrations mathématiques (condition de viabilité $c > \lambda\mu$) et l'analyse des résultats.

## 🛠️ Installation & Utilisation

1.  Clonez le dépôt :
    ```bash
    git clone [https://github.com/votre-utilisateur/votre-repo.git](https://github.com/votre-utilisateur/votre-repo.git)
    ```
2.  Assurez-vous d'avoir installé les dépendances :
    ```bash
    pip install numpy matplotlib scipy
    ```
3.  Lancez le notebook :
    ```bash
    jupyter notebook projet1_probabilite_ruine.ipynb
    ```

## 📊 Résultats
Les simulations montrent que la probabilité de ruine décroît de manière exponentielle avec l'augmentation du capital initial $u$. Les courbes obtenues par la méthode de Monte-Carlo se superposent presque parfaitement aux courbes théoriques, validant ainsi l'algorithme de simulation.

---
**Auteur :** Alessio Nocera
