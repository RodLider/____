
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Agendamento Online e Presencial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background: url('https://i.imgur.com/aPLuDmc.jpeg') no-repeat center center fixed;
            background-size: cover;
            color: white;
            margin: 0;
        }
        .container {
            max-width: 90%;
            margin: auto;
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
        }
        h2 {
            color: #007bff;
            font-weight: bold;
            font-size: 1.5em;
        }
        label {
            color: #007bff;
            font-weight: bold;
            display: block;
            text-align: left;
            margin-top: 10px;
        }
        select, input {
            display: block;
            width: 100%;
            margin-top: 5px;
            padding: 10px;
            border-radius: 5px;
            border: none;
            font-size: 1em;
            color: black;
        }
        button {
            background-color: #007bff;
            color: white;
            padding: 12px;
            border: none;
            cursor: pointer;
            margin-top: 15px;
            width: 100%;
            font-weight: bold;
            border-radius: 5px;
            font-size: 1.2em;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Agende seu atendimento</h2>
        <form id="agendamento-form">
            <label for="nome">Cliente:</label>
            <input type="text" id="nome" name="nome" required>
            
            <label for="contato">Contato:</label>
            <input type="text" id="contato" name="contato" required>
            
            <label for="tipo">Tipo de Atendimento:</label>
            <select id="tipo" name="tipo" required>
                <option value="online">Online</option>
                <option value="presencial">Presencial</option>
            </select>
            
            <label for="data">Data:</label>
            <input type="date" id="data" name="data" required>
            
            <label for="horario">Horário:</label>
            <select id="horario" name="horario" required>
                <option value="09:00">09:00</option>
                <option value="09:30">09:30</option>
                <option value="10:00">10:00</option>
                <option value="10:30">10:30</option>
                <option value="11:00">11:00</option>
                <option value="11:30">11:30</option>
                <option value="12:00">12:00</option>
                <option value="14:00">14:00</option>
                <option value="14:30">14:30</option>
                <option value="15:00">15:00</option>
                <option value="15:30">15:30</option>
                <option value="16:00">16:00</option>
                <option value="16:30">16:30</option>
                <option value="17:00">17:00</option>
                <option value="17:30">17:30</option>
                <option value="18:00">18:00</option>
            </select>
            
            <label for="responsavel">Falar com:</label>
            <select id="responsavel" name="responsavel" required>
                <option value="Silmara">Silmara</option>
                <option value="Larissa">Larissa</option>
            </select>
            
            <button type="button" onclick="agendarWhatsApp()">Agendar</button>
        </form>
    </div>

    <script>
        function agendarWhatsApp() {
            var nome = document.getElementById("nome").value;
            var contato = document.getElementById("contato").value;
            var tipo = document.getElementById("tipo").value;
            var data = document.getElementById("data").value;
            var horario = document.getElementById("horario").value;
            var responsavel = document.getElementById("responsavel").value;
            
            var diaSemana = new Date(data).getDay();
            var endereco = tipo === "presencial" ? "Rua do Sol, centro. Em cima do ligeirinho do Banco do Brasil, Multimarcas, sala 10" : "Atendimento Online";
            
            if (diaSemana === 6 && (horario < "09:00" || horario > "12:00")) {
                alert("Aos sábados, o horário de atendimento é das 09:00 às 12:00.");
                return;
            }
            
            var mensagem = `*Agendamento ${tipo.toUpperCase()}*%0ACliente: ${nome}%0AContato: ${contato}%0AHorário: ${horario}%0AData: ${data}%0AEndereço: ${endereco}%0AFalar com: ${responsavel}`;
            
            var url = `https://wa.me/98984699652?text=${mensagem}`;
            window.open(url, "_blank");
        }
    </script>
</body>
</html>
