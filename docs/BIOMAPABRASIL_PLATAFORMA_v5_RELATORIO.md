# BioMapaBrasil v5 — relatório curto de design

## O que mudou

- O mapa deixou de usar o relevo sombreado de pequena escala como superfície principal. A nova base combina o mosaico orbital EOxCloudless / Sentinel-2 de 2025 com sombreamento analítico derivado de elevação real e limites estaduais do IBGE na mesma projeção Web Mercator.
- A superfície local de 4096 × 4302 px garante uma apresentação durável na repo. A partir de 1,48×, uma camada WMS do mesmo mosaico é solicitada para a área visível e entra por transição, aumentando o detalhe durante a exploração; se a rede falhar, a cópia local permanece.
- O entorno do Brasil deixou de repetir a imagem orbital fora do limite nacional. A superfície Sentinel-2 permanece em cor real apenas dentro da geometria do IBGE; o relevo é aplicado como luz e sombra, não como falsa cor.
- O globo atmosférico decorativo, seus halos circulares e o canvas WebGPU foram removidos. O fundo do palco agora é um campo cartográfico retangular, sóbrio e contínuo, com grade linear discreta; não há máscara esférica, borda curva ou imagem recortada atrás do país.
- A camada temática não pinta mais o território inteiro. Densidade no GBIF é codificada por cor e espessura dos contornos; as hastes continuam representando ocorrências filtradas em escala de raiz quadrada e o disco continua mostrando a quantidade real de caminhos.
- A sinalização de baixa densidade foi mantida, mas ficou 4× mais espaçada, com fundo quase transparente e traço menos opaco. Continua identificável e acionável sem esconder a imagem de superfície.
- A procedência cartográfica fica visível no mapa. A legenda separa explicitamente superfície orbital, relevo, limite territorial e camada temática, e declara que a imagem não é um mapa geológico.
- A barra de comando, o palco cartográfico e o inspetor continuam separados. Regiões podem rolar horizontalmente; zoom, enquadramento e “Baixa densidade” não cobrem o país.
- O gráfico territorial continua usando 27 pontos identificáveis em escala logarítmica, com mínimo, mediana e máximo rotulados.
- A trilha “Da floresta à molécula” permanece no modelo LifeMap: visão geral silenciosa, conexões reveladas somente no foco e ficha referenciada junto ao cursor. Os medalhões continuam mostrando o lastro real de cada elo.
- Tema claro amazônico, escala tipográfica, iconografia, estados, movimento, Escada de Lastro, três vistas da base, critérios e procedência permanecem no sistema v5 já revisado.
- A redação da interface foi auditada de ponta a ponta. A chamada absolutista foi substituída por “Rastreabilidade fortalece a evidência científica”; “elo mais fraco” passou a “elo determinante” ou “menor lastro documental”; “véu de ausência” passou a “camada de baixa densidade”. Avisos, estados vazios, critérios, ficha, mapa e cabeçalho do CSV agora usam linguagem científica propositiva, sem reduzir ressalvas ou ocultar ausências.
- A faixa de quatro indicadores situada abaixo da abertura foi removida integralmente, inclusive seu contêiner, rotina de montagem e inicialização. Os valores de origem continuam disponíveis nas estruturas de dados e nas visualizações pertinentes; apenas essa apresentação redundante deixou a página.
- Na Escada de Lastro, “testemunho” foi substituído por “material de referência depositado em coleção científica”. A definição L4 agora explicita a possibilidade de reexame da identificação taxonômica; L3 informa a ausência de material de referência vinculado, sem alterar a classificação dos registros.

## Fontes e licença da cartografia

- Superfície: [EOxCloudless / EOX](https://cloudless.eox.at), Sentinel-2 2025, fonte de 10 m. “Contains modified Copernicus Sentinel data 2025”. Licença CC BY-NC-SA 4.0 para uso acadêmico não comercial; uso comercial exige licença correspondente da EOX.
- Relevo: [Terrain Tiles / Mapzen no AWS Open Data](https://registry.opendata.aws/terrain-tiles/), com SRTM e GMTED2010 cortesia do USGS. O sombreamento usa azimute de 315°, altura de luz de 38° e nenhum exagero vertical.
- Limites das UFs: IBGE. A caixa cartográfica usada no SVG e nos rasters é a mesma: 0–1000 × 0–1050,1 no palco, correspondente a −73,9904 a −34,7932° de longitude e −33,7439 a 5,2718° de latitude.

## O que foi medido e verificado

- HTML publicado como `index.html`: 978.524 bytes; 3.710 linhas; SHA-256 `f3a38803c3fee22d51736aab84085bfd4ec9c98d6f8aff8e2f1458ece6c17241`; JavaScript com sintaxe validada. A diferença de 14 bytes em relação ao artefato de submissão corresponde apenas ao prefixo `assets/` nas duas referências cartográficas.
- Superfície orbital: 4096 × 4302 px, 3.122.530 bytes, SHA-256 `3b3b1193bf747a2231e733383b029278ae8f829358113a10f1f9311715e09b47`.
- Relevo analítico: 4096 × 4302 px, 3.019.278 bytes, SHA-256 `4719b362304e9a081f77a7d2ed98d0cc9d65741375c5ece9dca1adc10850af9c`.
- Integridade: `REG`, `UF` e o raster `REL` incorporado são idênticos aos da v4; as 14 imagens incorporadas também permanecem byte a byte idênticas.
- Desktop em 1268 × 714 px: 27 UFs presentes; palco de 811,9 px + inspetor de 356 px; colisão medida entre regiões e controles = falsa; largura do documento 1258 px para viewport de 1268 px.
- Mobile em 390 × 844 px: mapa com 348 px de largura; documento com 380 px de largura útil, sem overflow horizontal; 27 UFs e 23 torres renderizadas; procedência permanece visível.
- Revisão editorial em 1280 × 720 px e 390 × 844 px: título em três e quatro linhas, respectivamente; nenhum texto-elemento visível abaixo de 11 px; sem overflow horizontal. O controle de baixa densidade mede 112 × 34 px no mobile e não colide com as regiões.
- Detalhe progressivo: testado em 1,8×; WMS carregado, alinhado ao recorte SVG e revelado com opacidade de 0,98.
- Foram conferidos zoom, reenquadramento, camada de lacunas, seleção territorial, realce recíproco, navegação horizontal das regiões e reorganização do inspetor abaixo do mapa.

## O que decidi não mexer

- Nenhum registro, número, relação, grau de lastro, cálculo, filtro, busca, exportação, vista ou regra científica.
- Nenhum texto factual, crédito, autoria, licença, etiqueta de natureza da imagem, declaração de ausência ou ressalva sobre distribuição no GBIF versus procedência do material. A revisão alterou apenas enquadramento editorial, títulos, rótulos e microcopy.
- Nenhuma imagem do Google Earth foi copiada ou incorporada. A referência foi tratada como meta de qualidade; a implementação usa fontes redistribuíveis e atribuição visível.
- Não chamei imagem orbital de geologia, não converti cor da superfície em cobertura vegetal e não apliquei exagero vertical ao DEM.
- Nenhuma pontuação, mecanismo, dado ou fonte foi inventado. O efeito atmosférico WebGPU foi removido; cartografia e relevo continuam vindo exclusivamente das camadas identificadas acima.
