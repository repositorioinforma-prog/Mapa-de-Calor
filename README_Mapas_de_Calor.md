# Mapas de Calor — Edição Especial

Aplicação web para importar arquivos KML, visualizar malhas geográficas, aplicar cores manualmente, numerar regiões e exportar o resultado final em PNG.

O projeto funciona diretamente no navegador e foi desenvolvido em um único arquivo HTML, utilizando Leaflet para exibição dos mapas e conversão de KML para GeoJSON.

## Visão geral

A aplicação permite criar mapas temáticos de maneira simples, sem necessidade de servidor, banco de dados ou instalação de dependências locais.

Principais possibilidades:

- Importação simultânea de vários arquivos KML;
- Visualização das regiões sobre mapas do OpenStreetMap ou imagens de satélite da Esri;
- Aplicação manual de cores em cada malha;
- Uso de paleta especial, paleta padrão ou cor personalizada;
- Inserção de números ou identificadores sobre as regiões;
- Movimentação manual dos números no mapa;
- Controle da opacidade das cores;
- Controle da espessura das bordas;
- Controle do tamanho dos números;
- Exibição ou ocultação dos números;
- Exportação do mapa final em PNG.

## Tecnologias utilizadas

- HTML5;
- CSS3;
- JavaScript;
- Leaflet 1.9.4;
- leaflet-image;
- toGeoJSON;
- OpenStreetMap;
- Esri World Imagery.

As bibliotecas são carregadas por CDN. Por isso, é necessário estar conectado à internet durante o uso da aplicação.

## Estrutura do projeto

```text
index_2.0.html
README.md
```

Todo o código da aplicação está concentrado no arquivo:

```text
index_2.0.html
```

## Como executar

Não é necessário instalar Node.js, Python ou qualquer outro ambiente.

### Opção 1 — Abrir diretamente

1. Localize o arquivo `index_2.0.html`;
2. Clique duas vezes sobre o arquivo;
3. Abra-o em um navegador moderno, como Google Chrome, Microsoft Edge ou Firefox.

### Opção 2 — Usar um servidor local

Alguns navegadores podem aplicar restrições ao abrir módulos JavaScript diretamente pelo protocolo `file://`.

Nesse caso, execute o arquivo com um servidor local.

Com Python:

```bash
python -m http.server 8000
```

Depois, acesse:

```text
http://localhost:8000/index_2.0.html
```

Com a extensão Live Server do Visual Studio Code:

1. Abra a pasta do projeto no VS Code;
2. Clique com o botão direito em `index_2.0.html`;
3. Selecione **Open with Live Server**.

## Como utilizar

### 1. Importar os arquivos KML

Na seção **KMLs**:

1. Clique no campo de seleção de arquivos;
2. Escolha um ou mais arquivos com extensão `.kml`;
3. Aguarde o carregamento das malhas.

Cada arquivo é tratado como uma região independente.

O nome do arquivo, sem a extensão `.kml`, será usado como nome da região no painel lateral e nos pop-ups do mapa.

Exemplo:

```text
Regiao_01.kml
Regiao_02.kml
Regiao_03.kml
```

As regiões serão exibidas como:

```text
Regiao_01
Regiao_02
Regiao_03
```

Após a importação, o mapa ajusta automaticamente o enquadramento para mostrar todas as malhas carregadas.

## Configurações visuais

### Mapa de fundo

A aplicação oferece três opções:

- **OSM (Padrão):** mapa do OpenStreetMap;
- **Satélite (Esri):** imagens de satélite fornecidas pela Esri;
- **Sem mapa:** remove o mapa-base e mantém somente as malhas.

O mapa do OpenStreetMap recebe um filtro em escala de cinza para dar maior destaque às regiões pintadas.

### Espessura das bordas

Permite controlar a espessura dos contornos das regiões.

Intervalo disponível:

```text
0 a 10 pixels
```

O valor pode ser alterado pelo controle deslizante ou pelo campo numérico.

### Opacidade das cores

Controla a transparência da cor aplicada sobre cada região.

Intervalo disponível:

```text
0% a 100%
```

- `0%`: região totalmente transparente;
- `100%`: região totalmente preenchida.

O valor padrão é:

```text
60%
```

### Tamanho dos números

Controla o tamanho dos números ou identificadores exibidos sobre o mapa.

Intervalo disponível:

```text
10 a 80 pixels
```

O valor padrão é:

```text
28 pixels
```

## Pintura das regiões

Depois de importar os arquivos KML, cada região aparece no painel lateral.

Para cada região, é possível:

- Escolher uma cor da Guia Especial;
- Escolher uma cor da paleta padrão;
- Selecionar uma cor personalizada;
- Inserir um número ou texto curto;
- Alterar a cor sempre que necessário.

### Guia Especial

A paleta especial contém:

- Azul-claro;
- Laranja;
- Vermelho vivo;
- Cinza-claro.

### Cores padrão

A paleta padrão contém:

- Azul-escuro;
- Azul-médio;
- Laranja-escuro;
- Laranja-médio;
- Laranja-claro;
- Vermelho;
- Cinza.

### Cor personalizada

O seletor de cor permite utilizar qualquer cor disponível no padrão hexadecimal.

Exemplo:

```text
#1E90FF
```

A cor escolhida é aplicada imediatamente à região correspondente.

## Numeração das regiões

Cada região possui um campo no qual pode ser digitado um número, letra ou identificador curto.

Exemplos:

```text
1
2
A
B
01
Zona 1
```

O texto é exibido no centro geográfico aproximado da região.

### Movimentação manual

Os números podem ser arrastados diretamente no mapa.

Isso é útil quando:

- O centro calculado fica fora da área visual principal;
- Duas numerações ficam sobrepostas;
- A geometria da região é irregular;
- É necessário melhorar a composição visual do mapa.

A posição manual permanece ativa durante a sessão atual.

### Ocultar ou mostrar números

O botão **Ocultar números** remove temporariamente os identificadores da visualização.

Ao clicar novamente, o botão muda para **Mostrar números** e restaura os marcadores.

Mesmo ocultos na tela, os números continuam registrados no projeto.

## Limpar pintura

O botão **Limpar pintura** remove todas as cores aplicadas manualmente.

A ação:

- Não remove os arquivos KML;
- Não apaga os números;
- Não altera a posição dos números;
- Mantém as configurações de opacidade, borda e tamanho.

## Exportação para PNG

O botão **Exportar PNG** gera uma imagem do mapa exibido.

O arquivo é salvo com o nome:

```text
mapa_calor.png
```

A exportação inclui:

- Mapa-base selecionado;
- Malhas geográficas;
- Cores aplicadas;
- Bordas;
- Números;
- Posições personalizadas dos números.

Antes da captura, a aplicação aguarda o carregamento dos blocos do mapa por até alguns segundos.

Os números são desenhados diretamente no canvas final para garantir que apareçam corretamente na imagem exportada.

## Requisitos dos arquivos KML

Os arquivos devem:

- Ter extensão `.kml`;
- Possuir geometrias geográficas válidas;
- Utilizar coordenadas reconhecidas pelo Leaflet;
- Conter preferencialmente polígonos ou multipolígonos;
- Estar em um sistema de coordenadas compatível com latitude e longitude.

A aplicação também pode interpretar outros elementos presentes no KML, dependendo da conversão feita pela biblioteca toGeoJSON.

## Comportamento dos nomes

O nome original do arquivo é exibido ao usuário.

Internamente, o sistema cria uma versão padronizada do nome para identificar cada região.

Essa padronização:

- Remove acentos;
- Converte letras para minúsculas;
- Substitui caracteres especiais;
- Evita conflitos entre nomes repetidos.

Quando dois arquivos geram a mesma chave interna, são criadas identificações sequenciais.

Exemplo:

```text
regiao
regiao #2
regiao #3
```

## Cores utilizadas

As principais cores da aplicação são definidas em variáveis CSS:

```css
--azul-claro: #87CEFA;
--azul-medio: #1E90FF;
--azul-escuro: #121958;
--laranja-claro: #FFDF9E;
--laranja-medio: #FFA500;
--laranja-escuro: #843C0C;
--vermelho: #bb0c0c;
--vermelhao: #ff0000;
--laranja: #ff8c00;
--cinza: #808080;
--cinza-claro: #d3d3d3;
```

Essas cores podem ser alteradas diretamente no bloco `:root` do CSS.

## Personalização

### Alterar o título

Localize no HTML:

```html
<title>Mapas de Calor - Edição Especial</title>
```

E também:

```html
<h1>Mapas de Calor - Edição Especial</h1>
```

Substitua pelo nome desejado.

### Alterar a posição inicial do mapa

Localize:

```javascript
const map = L.map('map', {
  zoomControl: true,
  preferCanvas: true
}).setView([-15.78, -47.88], 11);
```

Os valores representam:

```text
[latitude, longitude], zoom
```

### Alterar o nome do PNG

Localize:

```javascript
a.download = 'mapa_calor.png';
```

Substitua pelo nome desejado.

### Adicionar novas cores

Adicione uma nova variável em `:root`:

```css
--verde: #008000;
```

Depois, inclua a cor em uma das paletas JavaScript:

```javascript
{id: 'verde', hex: getVar('--verde'), label: 'Verde'}
```

## Limitações conhecidas

- A aplicação não salva automaticamente o trabalho;
- Ao atualizar ou fechar a página, cores, números e posições são perdidos;
- Não existe importação de configurações salvas;
- A exportação depende do carregamento correto dos mapas externos;
- Alguns servidores de mapas podem bloquear imagens por políticas de CORS;
- Arquivos KML muito grandes podem reduzir o desempenho;
- Não há suporte nativo para edição das geometrias;
- Não há legenda automática na imagem exportada;
- A aplicação depende de internet para carregar bibliotecas e mapas-base.

## Sugestões de melhorias

Possíveis evoluções do projeto:

- Salvar o projeto em JSON;
- Reabrir configurações já salvas;
- Criar legenda automática;
- Exportar também em SVG ou PDF;
- Permitir edição dos nomes das regiões;
- Adicionar campo de busca;
- Importar arquivos GeoJSON;
- Importar arquivos ZIP contendo KMLs;
- Aplicar cores automaticamente com base em valores;
- Criar faixas de intensidade;
- Adicionar título, fonte e observações ao mapa;
- Permitir reposicionamento de textos por teclado;
- Incluir botão para restaurar a posição central dos números;
- Salvar as preferências no armazenamento local do navegador;
- Disponibilizar funcionamento offline;
- Gerar versão responsiva para dispositivos móveis.

## Segurança e privacidade

Os arquivos KML são processados localmente no navegador.

A aplicação não envia os arquivos para um servidor próprio e não possui integração com banco de dados.

Entretanto, os mapas-base e as bibliotecas externas são carregados de serviços de terceiros.

## Navegadores recomendados

Recomenda-se utilizar versões recentes de:

- Google Chrome;
- Microsoft Edge;
- Mozilla Firefox.

## Licenças e atribuições

Este projeto utiliza bibliotecas e serviços externos, incluindo:

- Leaflet;
- leaflet-image;
- toGeoJSON;
- OpenStreetMap;
- Esri World Imagery.

Ao publicar ou distribuir a aplicação, mantenha as atribuições exigidas pelos provedores de mapas e pelas respectivas licenças das bibliotecas.

## Autor

Projeto desenvolvido para criação e exportação de mapas temáticos a partir de arquivos KML.

## Licença

Defina a licença do projeto conforme a forma de uso e distribuição desejada.

Exemplo:

```text
MIT License
```
