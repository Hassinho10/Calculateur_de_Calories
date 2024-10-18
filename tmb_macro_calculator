def calcul_tmb(poids, taille, age, sexe):
    # Calcul du TMB selon la formule de Harris-Benedict
    if sexe == 'homme':
        tmb = 88.362 + (13.397 * poids) + (4.799 * taille) - (5.677 * age)
    elif sexe == 'femme':
        tmb = 447.593 + (9.247 * poids) + (3.098 * taille) - (4.330 * age)
    else:
        raise ValueError("Sexe non reconnu. Utilisez 'homme' ou 'femme'.")
    return tmb

def ajuster_calories(tmb, facteur_activite):
    # Multiplier le TMB par le facteur d'activité
    tmb_ajuste = tmb * facteur_activite
    return tmb_ajuste

def calculer_macronutriments(calories, poids):
    # Répartition des macronutriments (protéines, glucides, lipides)
    proteines = 2 * poids  # 2 g de protéines par kg de poids corporel
    lipides = 0.8 * poids  # 0.8 g de lipides par kg de poids corporel
    glucides = (calories - (proteines * 4 + lipides * 9)) / 4  # Le reste en glucides

    return proteines, glucides, lipides

# Fonction pour obtenir le facteur d'activité en fonction du nombre de pas
def obtenir_facteur_activite(nombre_pas):
    if nombre_pas < 3000:
        return 1.2  # Sédentaire
    elif 3000 <= nombre_pas < 5000:
        return 1.375  # Légèrement actif
    elif 5000 <= nombre_pas < 7500:
        return 1.55  # Modérément actif
    elif 7500 <= nombre_pas < 10000:
        return 1.725  # Actif
    else:
        return 1.9  # Très actif

# Fonction principale pour demander les infos
def main():
    print("Bienvenue dans l'outil de calcul du TMB et des macros!")
    
    # Demander les informations utilisateur
    sexe = input("Entrez votre sexe (homme/femme) : ").lower()
    age = int(input("Entrez votre âge : "))
    poids = float(input("Entrez votre poids en kg : "))
    taille = float(input("Entrez votre taille en cm : "))
    nombre_pas = int(input("Combien de pas faites-vous en moyenne par jour ? "))

    # Calculer le TMB
    tmb = calcul_tmb(poids, taille, age, sexe)
    print(f"Votre TMB (sans ajustement pour l'activité) est : {tmb:.2f} kcal")
    
    # Obtenir le facteur d'activité
    facteur_activite = obtenir_facteur_activite(nombre_pas)
    print(f"Votre facteur d'activité est : {facteur_activite}")
    
    # Ajuster les calories selon le facteur d'activité
    calories = ajuster_calories(tmb, facteur_activite)
    print(f"Votre apport calorique ajusté est : {calories:.2f} kcal")

    # Calculer les macronutriments
    proteines, glucides, lipides = calculer_macronutriments(calories, poids)
    print(f"Répartition des macronutriments :")
    print(f"Protéines : {proteines:.2f} g")
    print(f"Glucides : {glucides:.2f} g")
    print(f"Lipides : {lipides:.2f} g")

# Exécuter la fonction principale
if __name__ == "__main__":
    main()
