from PIL import Image

# Simulação de uma base de dados de produtos com códigos de barras, preços e imagens
produtos = {
    "123456789012": {"nome": "Arroz", "preco": 10.50, "imagem": "teste.jpg"},
    "987654321098": {"nome": "Feijão Maximo", "preco": 7.80, "imagem": "Feijão.png"},
    "111222333444": {"nome": "Macarrão", "preco": 5.20, "imagem": "macarrao.jpg"},
    "555666777888": {"nome": "Óleo", "preco": 8.90, "imagem": "oleo.jpg"},
    "999888777666": {"nome": "Açúcar", "preco": 4.30, "imagem": "acucar.jpg"}
}


# Função para abrir e exibir a imagem de um produto
def exibir_imagem(caminho_imagem):
    try:
        img = Image.open(caminho_imagem)
        img.show()  # Abre a imagem no visualizador padrão
    except FileNotFoundError:
        print(f"Imagem {caminho_imagem} não encontrada.")


# Função para simular a leitura de código de barras e processar a lista de compras
def leitura_codigo_barras():
    lista_compras = []
    total = 0.0

    while True:
        codigo = input("Digite o código de barras (ou 'sair' para finalizar): ")

        if codigo.lower() == 'sair':
            break

        # Verifica se o código está no dicionário de produtos
        if codigo in produtos:
            produto = produtos[codigo]
            lista_compras.append(produto)
            total += produto['preco']
            print(f"Produto: {produto['nome']} - R$ {produto['preco']:.2f} adicionado à lista.")
            # Exibe a imagem do produto
            exibir_imagem(produto['imagem'])
        else:
            print("Código de barras não encontrado. Tente novamente.")

    # Exibe a lista de compras e o total
    print("\n--- Lista de Compras ---")
    for item in lista_compras:
        print(f"{item['nome']}: R$ {item['preco']:.2f}")

    print(f"\nTotal: R$ {total:.2f}")


# Chama a função para iniciar a leitura de códigos de barras
leitura_codigo_barras()
