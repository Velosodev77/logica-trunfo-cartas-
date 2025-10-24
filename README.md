# Cartas com valores conhecidos e "None" para os desconhecidos
cartas = {
    "Dragão":     {"F": 9, "V": 6, "I": None, "M": 7},
    "Fênix":      {"F": 7, "V": None, "I": 8, "M": 8},
    "Unicórnio":  {"F": 6, "V": 7, "I": 9, "M": None},
    "Gigante":    {"F": None, "V": 4, "I": 3, "M": 2},
    "Sereia":     {"F": 4, "V": 9, "I": None, "M": 6},
    "Goblin":     {"F": 3, "V": None, "I": 4, "M": 5},
}

# Pistas (restrições)
# A soma dos atributos do Dragão é 26 → F + V + I + M = 26
cartas["Dragão"]["I"] = 26 - (cartas["Dragão"]["F"] + cartas["Dragão"]["V"] + cartas["Dragão"]["M"])

# Fênix V = Sereia M
cartas["Fênix"]["V"] = cartas["Sereia"]["M"]

# Soma do Unicórnio é 29
cartas["Unicórnio"]["M"] = 29 - (cartas["Unicórnio"]["F"] + cartas["Unicórnio"]["V"] + cartas["Unicórnio"]["I"])

# Soma do Gigante é 14
cartas["Gigante"]["F"] = 14 - (cartas["Gigante"]["V"] + cartas["Gigante"]["I"] + cartas["Gigante"]["M"])

# Goblin V = 6
cartas["Goblin"]["V"] = 6

# Inteligência da Sereia = 7
cartas["Sereia"]["I"] = 7

# Agora calcular a soma total de cada carta
for nome, atributos in cartas.items():
    total = sum(atributos.values())
    print(f"{nome}: {atributos}, Soma = {total}")

# Descobrir quem é o Super Trunfo
super_trunfo = max(cartas.items(), key=lambda c: sum(c[1].values()))
print(f"\nO Super Trunfo é {super_trunfo[0]} com soma = {sum(super_trunfo[1].values())}")
