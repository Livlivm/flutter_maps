#  Flutter Map

Aplicativo mobile desenvolvido em **Flutter** para trabalhar com mapas interativos e cálculo de rotas entre diferentes pontos.

O projeto utiliza o **Google Maps** para apresentar o mapa na aplicação e a API **OSRM (Open Source Routing Machine)** para calcular o percurso entre uma origem e um destino.

---

##  Sobre o projeto

A proposta do projeto é demonstrar como uma aplicação Flutter pode utilizar informações de localização e serviços externos para apresentar uma rota de forma visual.

O usuário trabalha com dois pontos principais:

*  **Origem:** local onde o percurso começa;
*  **Destino:** local onde o percurso termina.

Depois que as coordenadas são informadas, o aplicativo consulta o OSRM e utiliza os dados retornados para desenhar o caminho diretamente sobre o mapa.

---

## Como funciona

O funcionamento da aplicação acontece da seguinte maneira:

1. O mapa é carregado através do `GoogleMap`;
2. São definidos os pontos de origem e destino;
3. As coordenadas são enviadas para o serviço OSRM;
4. A API calcula o percurso pelas vias disponíveis;
5. A resposta é recebida no formato **GeoJSON**;
6. As coordenadas da rota são extraídas e convertidas;
7. Uma `Polyline` é criada para representar o caminho;
8. A câmera do mapa é ajustada para mostrar toda a rota.

O aplicativo também possui tratamento para situações em que a requisição não é concluída corretamente.

---

##  Funcionalidades

* Exibição de mapa interativo;
* Definição de origem e destino;
* Consulta de rotas através de API externa;
* Integração com o OSRM;
* Processamento de dados em GeoJSON;
* Conversão de coordenadas geográficas;
* Desenho da rota utilizando `Polyline`;
* Ajuste automático da câmera;
* Tratamento de erros durante as requisições.

---

##  Tecnologias utilizadas

* **Flutter**
* **Dart**
* **Google Maps Flutter**
* **HTTP**
* **OSRM API**

### Principais dependências

```yaml
dependencies:
  flutter:
    sdk: flutter
  google_maps_flutter:
  http:
```

---

##  API de rotas

Para calcular o percurso, o aplicativo realiza uma requisição para a API pública do **OSRM**.

O formato utilizado é:

```text
https://router.project-osrm.org/route/v1/driving/{longitude_origem},{latitude_origem};{longitude_destino},{latitude_destino}?overview=full&geometries=geojson
```

Os parâmetros utilizados permitem solicitar o percurso completo e receber a geometria da rota no formato **GeoJSON**.

### Exemplo

```text
https://router.project-osrm.org/route/v1/driving/-46.7798,-22.7086;-46.7650,-22.7010?overview=full&geometries=geojson
```

---

##  Representação da rota

Depois que a API retorna os dados, as coordenadas presentes no GeoJSON são processadas pelo aplicativo.

Esses pontos são transformados em coordenadas compatíveis com o Google Maps e utilizados para criar uma `Polyline`.

A linha representa visualmente o caminho calculado entre os dois pontos.

---

##  Ajuste do mapa

Para facilitar a visualização, a aplicação calcula os limites geográficos da rota.

Dessa forma, a câmera consegue se ajustar automaticamente para enquadrar o percurso completo no mapa.

---

##  Tratamento de erros

Como o projeto depende de uma API externa, podem ocorrer falhas durante a comunicação.

A aplicação considera situações como:

* Erro na requisição HTTP;
* Falha na conexão;
* Resposta inválida;
* Rota não encontrada;
* Problemas no processamento dos dados recebidos.

---

##  Demonstração

![Flutter Map](https://github.com/user-attachments/assets/1d4c8d1e-ac99-428f-9e81-48441cd2442e)

---

##  Objetivo

O projeto foi desenvolvido para praticar a integração de **Flutter com mapas e APIs externas**, trabalhando conceitos de:

* Localização;
* Coordenadas geográficas;
* Requisições HTTP;
* APIs externas;
* GeoJSON;
* Polylines;
* Manipulação da câmera;
* Tratamento de erros.

O desenvolvimento também demonstra como dados obtidos de uma API podem ser processados e transformados em elementos visuais dentro de uma aplicação mobile.

---

##  Desenvolvimento

Projeto desenvolvido durante os estudos de **Desenvolvimento de Sistemas — SENAI** utilizando Flutter e Dart.
