# Laravel Custom Validation

Pacote Laravel para validações comuns ao Brasil(pt-BR) tipo: CNPJ,CPF,CEP,CNS

## Instalação

Instale a dependencia com o seguinte comando

```bash
composer require robersonfaria/validation
```

#### Laravel 5.5+
Adicionado suporte ao Package Discovery, sendo assim não é mais necessário adicionar o Service Provider ao seu `config/app.php`


## Uso

Para usar basta adicionar o nome da validação que deseja no action store() ou update():

```php
    public function update(Request $request, $id)
    {
        
        $requestData = $request->all();
        
        $cliente = Cliente::findOrFail($id);
        $cliente->update($requestData);

        $validatedData = $request->validate([
            'nome' => 'required|max:55',
            'email' => 'required',
            'cpf' => 'required|cns',
        ]);

        return redirect('clientes')->with('flash_message', 'Cliente updated!');
    }
```

## Mensagens de erro

Configurar o locale em config/app.php

    'locale' => 'en',
    'locale' => 'pt_BR',


Adicione as mensagens de validação no seu arquivo na respectiva linguagem. Ex: Em pt_BR o arquivo `resources/lang/pt_BR/validation.php`
```php
<?php
return [
    'cns' => 'O campo :attribute é inválido.',
    'cnpj' => 'O campo :attribute é inválido.',
    'cpf' => 'O campo :attribute é inválido.',
    'cep_format' => 'O campo :attribute não possui um formato de cep válido',
];
```

Ou ainda, se desejar, pode customizar a mensagem de erro em tempo de execução:

```php
$this->validate($request, [
    "field-name" => "cns"
],[
    "field-name.cns" => 'Mensagem customizada para o campo :attribute'
]);
```

## Validações

| validation | Sigla | Descrição |
|---|---|---|
| cns | CNS | Cartão Nacional de Saúde|
| cnpj | CNPJ | Cadastro Nacional da Pessoa Jurídica. |
| cpf | CPF | Cadastro de Pessoas Físicas. |
| cep_format | CEP Format | Validação do formato do CEP, não validará se o CEP é válido, pelo menos não inicialmente. |


## CHANGELOG
#### 1.0.0
Criação do pacote e implementação da validação do CNS - Cartão Nacional de Saúde

#### 1.0.1
Implementação das validações de CNPJ, CPF e formato de CEP.

#### 1.0.2
Adicionado merge do arquivo de configuração para quando tiver modificações.

#### 1.0.3
Correção de autoload no composer.json

#### 1.0.4
Adicionado package discovery

#### 2.0.0
Alterado para compatibilizar com laravel 5.5