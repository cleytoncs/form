<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Formulário de Inscrição | Projeto EducaOperador de ETA</title>
    <style>
        body {
            font-family: Arial, Helvetica, sans-serif;
            background-image: linear-gradient(to right, rgb(181, 232, 189), rgb(185, 248, 195));
            margin: 10;
        }

        .header {
            text-align: center;
            margin-bottom: 55px;
        }

        .header img {
            width: 100%;
            max-width: 300 px;
            border: 1.3px solid rgb(2, 152, 24);
            display: block;
            margin: 0 auto;
        }

        .box {
            color: white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.6);
            padding: 50px;
            border-radius: 35x;
            max-width: 100%;
            width: 500px;
        }

        fieldset {
            border: 3px solid rgb(254, 255, 254);
        }

        legend {
            border: 3px solid rgb(254, 255, 254);
            padding: 30px;
            text-align: center;
            background-image: linear-gradient(to right, rgb(4, 188, 32), rgb(2, 152, 24));
            border-radius: 5px;
            font-size: 1.6em
        }

        .inputBox {
            position: relative;
            margin-bottom: 40px;
        }

        .inputUser {
            background: none;
            border: none;
            border-bottom: 4px solid white;
            outline: none;
            color: white;
            font-size: 1.3em;
            width: 100%;
            letter-spacing: 1px;
        }

        .labelInput {
            position: absolute;
            top: 0;
            left: 0;
            pointer-events: none;
            transition: .5s;
        }

        .inputUser:focus ~ .labelInput,
        .inputUser:valid ~ .labelInput {
            top: -33px;
            font-size: 1.5em;
            color: white;
            outline: none;
        }

        #curso {
            border: none;
            padding: 10px;
            border-radius: 15px;
            outline: none;
            font-size: 1.3em;
            color: rgb(255, 255, 255);
        }

        #submit {
            background-image: linear-gradient(to right, rgb(4, 188, 32), rgb(2, 152, 24));
            width: 100%;
            border: none;
            padding: 15px;
            color: white;
            font-size: 1.6em;
            cursor: pointer;
            border-radius: 15px;
        }

        #submit:hover {
            background-image: linear-gradient(to right, rgb(230, 76, 5), rgb(248, 55, 52));
        }

        #successMessage {
            display: none;
            color: green;
            text-align: center;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="box">
        <form id="registrationForm">
            <fieldset>
                <legend><b>Formulário de Inscrição</b></legend>
                <div class="header">
                    <img src="projeto capacita.png" alt="Projeto CapacitaOperador">
                </div>

                <div class="inputBox">
                    <input type="text" name="nome" id="nome" class="inputUser" required>
                    <b for="nome" class="labelInput">Nome completo</b></label>
                </div>

                <div class="inputBox">
                    <input type="cpf" name="cpf" id="cpf" class="inputUser" required>
                    <b for="cpf" class="labelInput">CPF - Somente os números </b></label>
                </div>

                <div class="inputBox">
                    <input type="text" name="email" id="email" class="inputUser" required>
                    <b for="email" class="labelInput">E-mail</b></label>
                </div>

                <div class="inputBox">
                    <input type="tel" name="telefone" id="telefone" class="inputUser" required>
                    <b for="telefone" class="labelInput">Telefone DD 9 0000-0000</b></label>
                </div>

                <div class="inputBox">
                    <input type="text" name="cidade" id="cidade" class="inputUser" required>
                    <b for="cidade" class="labelInput">Cidade</b></b></label>
                </div>

                <div class="inputBox">
                    <input type="text" name="unidadeNegocio" id="unidadeNegocio" class="inputUser" required>
                    <label for="unidadeNegocio" class="labelInput">Unidade de Negócio</b></label>
                </div>

                <div class="inputBox">
                    <select name="curso" id="curso" class="inputUser" required>
                       <option value="" disabled selected></option>
                        <option ;  value= "informatica_basica">Curso de Informática Básica</option>
                    </select>
                    <b for="curso" class="labelInput">Selecionar Curso</b></label>
                </div>

                <input type="submit" name="submit" id="submit" value="Realizar Inscrição">
                <div id="successMessage">Inscrição realizada com sucesso!</div>
            </fieldset>
        </form>
    </div>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function (e) {
            e.preventDefault();

            // Coletar dados do formulário
            var formData = new FormData(this);
            var data = {};
            formData.forEach(function (value, key) {
                data[key] = value;
            });

            // Adicionar a lógica para se conectar ao SheetDB.io
            fetch('https://sheetdb.io/api/v1/olar91fxgae03', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data),
            })
            .then(response => response.json())
            .then(data => {
                console.log('Success:', data);
                
                // Exibir mensagem de sucesso
                document.getElementById('successMessage').style.display = 'block';

                // Limpar o formulário
                document.getElementById('registrationForm').reset();

                // Adicione aqui qualquer lógica adicional após a submissão bem-sucedida
            })
            .catch((error) => {
                console.error('Error:', error);
                // Adicione aqui qualquer lógica adicional em caso de erro
            });
        });
    </script>
</
