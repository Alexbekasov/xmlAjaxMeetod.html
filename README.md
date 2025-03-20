# xmlAjaxMeetod.html



<!DOCTYPE html>
<html lang="et">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Autode ja Õpilaste Kuvamine AJAX meetodi abil</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
    <script>
        $(document).ready(function() {

            $.ajax({
                type: "GET",
                url: "data.xml",
                dataType: "xml",
                success: kuvaXML,
                error: vigaXML
            });
        });


        function vigaXML(xhr, status, error) {
            $("#vastus").append('<p style="color:red;">Probleemid XML failiga! Viga: ' + error + '</p>');
        }


        function kuvaXML(xml) {

            $("#kasutajadBody, #autodBody").empty();


            $(xml).find("kasutajad").find("kasutaja").each(function() {
                var name = $(this).find("nimi").text();
                var picture = $(this).find("pilt").text();
                var website = $(this).find("website").text();

                var userRow = `
                    <tr>
                        <td><img src="kasutajad/${picture}" alt="${name}" class="rounded-img"></td>
                        <td>${name}</td>
                        <td><a href="${website}" target="_blank">Website</a></td>
                    </tr>
                `;
                $("#kasutajadBody").append(userRow);
            });


            $(xml).find("autod").find("auto").each(function() {
                var mark = $(this).find("mark").text();
                var picture = $(this).find("pilt").text();
                var website = $(this).find("website").text();

                var carRow = `
                    <tr>
                        <td>${mark}</td>
                        <td><img src="pildid/${picture}" alt="${mark}" class="rounded-img"></td>
                        <td><a href="${website}" target="_blank">Külastama</a></td>
                    </tr>
                `;
                $("#autodBody").append(carRow);
            });


            $("#kasutajadTable, #autodTable").fadeIn();
        }
    </script>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }

        th, td {
            padding: 10px;
            text-align: center;
            border: 1px solid #ddd;
        }

        th {
            background-color: #f4f4f4;
        }

        .rounded-img {
            width: 300px;
            height: 300px;
            border-radius: 70%;
        }

        #kasutajadTable, #autodTable {
            display: none;
            transition: opacity 0.5s ease;
        }

        #toggleButton {
            margin-top: 20px;
        }
    </style>
</head>
<body>
<h1>Autode ja Õpilaste Kuvamine AJAX meetodi abil</h1>

<button id="toggleButton">Näita/Peida Tabel</button>

<h2>Õpilased</h2>
<table id="kasutajadTable">
    <thead>
    <tr>
        <th>Pilt</th>
        <th>Nimi</th>
        <th>Veebileht</th>
    </tr>
    </thead>
    <tbody id="kasutajadBody"></tbody>
</table>

<h2>Autod</h2>
<table id="autodTable">
    <thead>
    <tr>
        <th>Mark</th>
        <th>Pilt</th>
        <th>Veebileht</th>
    </tr>
    </thead>
    <tbody id="autodBody"></tbody>
</table>

<h1>XML andmete lugemine jQuery abil</h1>
<a href="https://www.metshein.com/unit/xml-xml-andmete-lugemine-jquery-abil/">Leia rohkem teavet XML lugemise kohta jQuery abil</a>

<h2>
    AJAX (Asynchronous JavaScript and XML) on veebiarenduses kasutatav tehnoloogia, mis võimaldab veebilehtedel teha taustal serveripäringuid ja uuendada sisu ilma, et oleks vaja kogu lehte uuesti laadida. See muudab veebilehe interaktiivsemaks ja kiiremaks, kuna kasutaja saab jätkata teiste toimingutega, samal ajal kui server töötleb päringut.
</h2>

<div id="vastus"></div>

<script>

    $("#toggleButton").click(function() {
        $("#kasutajadTable, #autodTable").fadeToggle();
    });
</script>

</body>
</html>




<?xml version="1.0" encoding="UTF-8" ?>
<root>
    <kasutajad>
        <kasutaja>
            <nimi>Miroslav Burdyga</nimi>
            <pilt>miroslav.jpg</pilt>
            <website>https://miroslavburdyga24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Iryna Dmytrenko</nimi>
            <pilt>iryna.jpg</pilt>
            <website>https://irynadmytrenko24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Gleb Dranitson</nimi>
            <pilt>gleb.jpg</pilt>
            <website>https://glebdranitson24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Zhan-Gabriel Gerke</nimi>
            <pilt>zhan.jpg</pilt>
            <website>https://zhan-gabrielgerke24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Nicole Gulojan</nimi>
            <pilt>nicole.jpg</pilt>
            <website>https://nicolegulojan24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Jekaterina Guzek</nimi>
            <pilt>jekaterina.jpg</pilt>
            <website>https://jekaterinaguzek24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Ravil Hasjanov</nimi>
            <pilt>ravil.jpg</pilt>
            <website>https://ravilhasjanov24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Nikita Konkin</nimi>
            <pilt>nikita.jpg</pilt>
            <website>https://nikitakonkin24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Anastassia Kostjuk</nimi>
            <pilt>anastassia.jpg</pilt>
            <website>https://anastassiakostjuk24.thkit.ee/</website>
        </kasutaja>
        <kasutaja>
            <nimi>Deniel Kruusman</nimi>
            <pilt>deniel.jpg</pilt>
            <website>https://denielkruusman24.thkit.ee/</website>
        </kasutaja>
    </kasutajad>

    <autod>
        <auto>
            <mark>Lexus</mark>
            <pilt>lexus.jpg</pilt>
            <website>https://www.tthk.ee/</website>
        </auto>
        <auto>
            <mark>Mazda</mark>
            <pilt>mazda.jpg</pilt>
            <website>https://www.tthk.ee/</website>
        </auto>
        <auto>
            <mark>Peugeot</mark>
            <pilt>peugeot.jpg</pilt>
            <website>https://www.tthk.ee/</website>
        </auto>
        <auto>
            <mark>Mercedes-Benz</mark>
            <pilt>mercedes.jpg</pilt>
            <website>https://www.tthk.ee/</website>
        </auto>
    </autod>
</root>
