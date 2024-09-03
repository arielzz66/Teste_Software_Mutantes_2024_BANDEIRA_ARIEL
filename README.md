
# Teste de Software - Atividade 2 | Jishaku : bot do discord.

Este repositório contém o projeto de teste de software utilizando mutantes desenvolvido por **Ariel Lima Abade Bandeira** para a atividade do curso de Teste de Software em 2024. O objetivo deste projeto é aplicar técnicas de teste de mutação para avaliar a qualidade do código e a eficácia dos testes automatizados.

## Estrutura do Repositório

O repositório está organizado da seguinte forma:


- **`jishaku/tests`**: Inclui os testes automatizados escritos em Python para validar o comportamento do código presente na pasta `/src`.

## Preparação do Ambiente

Para configurar o ambiente de desenvolvimento e teste, siga os passos abaixo:

1. Instale o Python 3 e o `venv`:
    ```bash
    sudo apt install python3-venv
    ```

2. Clone o repositório e navegue até a pasta do projeto:
    ```bash
    git clone https://github.com/arielzz66/Teste_Software_Mutantes_2024_BANDEIRA_ARIEL.git
    cd Teste_Software_Mutantes_2024_BANDEIRA_ARIEL
    ```

3. Crie e ative um ambiente virtual:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

4. Instale as dependências necessárias:
    ```bash
    pip install -r requirements.txt
    ```

## Execução dos Testes

### Testes Automatizados

Os testes automatizados foram desenvolvidos usando o framework `pytest`. Para executá-los, utilize o seguinte comando:

```bash
pytest -vv /tests
```

Este comando executa todos os testes localizados no diretório `/tests` e fornece uma saída detalhada dos resultados.

### Cobertura de Código

Para gerar um relatório de cobertura de código durante a execução dos testes, utilize o comando:

```bash
pytest -vv /tests --cov=/src --cov-report term --cov-report html
```

Isso gerará um relatório detalhado tanto no terminal quanto em formato HTML, que pode ser visualizado em um navegador.

### Testes de Mutação

Os testes de mutação são realizados para avaliar a robustez dos testes automatizados. Para executar os testes de mutação, utilize o comando:

```bash
mutmut run --paths-to-mutate=/tests/test_cog.py
```

Foi utilizado um arquivo de testes específico para realizar o teste de mutação, que é o listado acima.

São testes de comando de automação associados, como  jsk, jsk hide, jsk show, jsk tasks, jsk cancel e jsk retain.

O resultado dos testes de mutação foram exemplificados no arquivo em PDF enviado junto com a atividade e também estão disponíveis no arquivo index.html na pasta `html/cov`.

4) Identificação de Melhorias

Padrão original:


```
  # test OOB
    with pytest.raises(ValueError):
        FilePaginator(BytesIO("XXone\ntwo\nthree\nfourXX".encode('utf-8')), line_span=(-1, 20))
        
```

Alteração que resultou na melhora da mutação:

```

    # Test out-of-bounds line span
    out_of_bounds_span = (0, 20)  # Alterado para um intervalo válido
    out_of_bounds_input = "one\ntwo\nthree\nfour".encode('utf-8')
    with pytest.raises(ValueError):
        FilePaginator(BytesIO(out_of_bounds_input), line_span=out_of_bounds_span)

```



## Conclusão

Este projeto visa demonstrar a importância dos testes de mutação na garantia da qualidade do software. A implementação desses testes complementa os testes automatizados tradicionais, identificando falhas sutis que podem passar despercebidas, resultando em um código mais confiável e robusto.

