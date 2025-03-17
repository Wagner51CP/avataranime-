# Projeto de Criação de Avatar

## Descrição
Este projeto utiliza a biblioteca **Pillow** para criar avatares personalizados. O avatar é gerado com um círculo representando a cabeça e o nome do usuário abaixo do círculo.

## Funcionalidades
- **Criação de Avatar**: Gera um avatar com um círculo e o nome do usuário.
- **Personalização de Cor**: Permite escolher a cor de fundo do avatar.
- **Personalização de Tamanho**: Permite definir o tamanho do avatar.

## Tecnologias Utilizadas
- **Linguagem de Programação**: Python
- **Biblioteca de Manipulação de Imagens**: Pillow

## Instalação
1. Clone este repositório: `git clone https://github.com/seu-usuario/projeto-avatar.git`
2. Navegue até o diretório do projeto: `cd projeto-avatar`
3. Instale as dependências: `pip install -r requirements.txt`

## Uso
### Exemplo de Código
```python
from PIL import Image, ImageDraw, ImageFont

def create_avatar(name, color, size=(200, 200)):
    # Cria uma imagem em branco
    avatar = Image.new('RGB', size, color)
    
    # Desenha um círculo para representar a cabeça
    draw = ImageDraw.Draw(avatar)
    head_radius = size[0] // 4
    head_center = (size[0] // 2, size[1] // 2)
    draw.ellipse((head_center[0] - head_radius, head_center[1] - head_radius,
                  head_center[0] + head_radius, head_center[1] + head_radius), fill='white')
    
    # Adiciona o nome do avatar
    font = ImageFont.load_default()
    text_size = draw.textsize(name, font=font)
    text_position = (head_center[0] - text_size[0] // 2, head_center[1] + head_radius + 10)
    draw.text(text_position, name, fill='black', font=font)
    
    return avatar

# Exemplo de uso
avatar = create_avatar("AnimeFan", "blue")
avatar.show()
avatar.save("avatar.png")
