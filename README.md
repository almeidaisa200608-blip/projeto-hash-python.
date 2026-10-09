# Projeto: Codificador e Hash de Senhas
# Feito para praticar strings, funções, laços e a função ord() em Python.

dicionario = "qwertyuiopasdfghjklzxcvbnm"
alfabeto = "abcdefghijklmnopqrstuvwxyz"


def codifica(senha):
    """Troca letras minúsculas por letras de um dicionário de substituição."""
    senha_criptografada = ""

    for letra in senha:
        if "a" <= letra <= "z":
            posicao = ord(letra) - ord("a")
            senha_criptografada += dicionario[posicao]
        elif "A" <= letra <= "Z":
            # Mantém a mesma lógica para letras maiúsculas.
            posicao = ord(letra.lower()) - ord("a")
            senha_criptografada += dicionario[posicao].upper()
        else:
            # Números e símbolos permanecem iguais.
            senha_criptografada += letra

    return senha_criptografada


def calcula_hash(senha):
    """Calcula uma soma simples dos códigos Unicode dos caracteres."""
    valor = 0

    for letra in senha:
        valor += ord(letra)

    return valor


def main():
    senha = "Marcelo123"
    nova_senha = "python"

    print("=== Codificador e Hash de Senhas ===")
    print(f"Senha original: {senha}")
    print(f"Senha codificada: {codifica(senha)}")
    print(f"Hash simples: {calcula_hash(senha)}")
    print()
    print(f"Nova senha: {nova_senha}")
    print(f"Senha codificada: {codifica(nova_senha)}")
    print(f"Hash simples: {calcula_hash(nova_senha)}")
    print()
    print("Outros exemplos:")
    print(f"Hash de 'ola': {calcula_hash('ola')}")
    print(f"Hash de 'Marcelo123!@': {calcula_hash('Marcelo123!@')}")


if __name__ == "__main__":
    main()
