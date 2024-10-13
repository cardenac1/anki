<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSV Parser App</title>
    <style>
        body {
            background-color: #121212;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        .container {
            width: 100%;
            max-width: 800px;
            margin: auto;
            padding: 20px;
        }

        h1 {
            text-align: center;
        }

        input[type="file"] {
            display: block;
            margin: 20px auto;
        }

        .row-list {
            list-style: none;
            padding: 0;
        }

        .row-item {
            background-color: #1e1e1e;
            padding: 10px;
            margin: 5px 0;
            cursor: pointer;
            border-radius: 5px;
        }

        .row-item:hover {
            background-color: #333333;
        }

        .details-view {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #222222;
            padding: 20px;
            overflow-y: auto;
            z-index: 1000;
        }

        .details-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        label {
            display: block;
            margin-top: 10px;
        }

        textarea {
            width: 100%;
            resize: vertical;
            padding: 10px;
            background-color: #333333;
            color: #ffffff;
            border: 1px solid #444444;
            border-radius: 5px;
        }

        .data-view {
            white-space: pre-line;
            margin-bottom: 20px;
        }

        .data-view strong {
            display: block;
            margin-top: 10px;
        }

        button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #1976d2;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #145a9d;
        }

        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }

        select {
            margin-top: 20px;
            padding: 10px;
            background-color: #333333;
            color: white;
            border: none;
            border-radius: 5px;
        }

        .column-selector {
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .column-button {
            padding: 10px;
            margin: 5px;
            background-color: #444444;
            border: 1px solid #666666;
            border-radius: 5px;
            cursor: pointer;
            color: white;
        }

        .column-button.selected {
            background-color: #28a745;
            border-color: #28a745;
        }

        @media (max-width: 600px) {
            .container {
                padding: 10px;
            }

            textarea {
                font-size: 14px;
            }

            button, select {
                width: 100%;
            }

            .row-item {
                font-size: 14px;
            }
        }

    </style>
</head>
<body>
    <div class="container">
        <h1 id="title">CSV Parser & Editor</h1>
        <input type="file" id="fileInput" accept=".csv">
        <div class="column-selector" id="columnSelector"></div>
        <select id="columnSelect" onchange="sortRows()">
            <option value="">Select Column to Sort</option>
        </select>
        <ul class="row-list" id="rowList"></ul>
        
        <div class="details-view" id="detailsView">
            <div class="details-header">
                <h2 id="detailsTitle">Details View</h2>
                <button onclick="backToList()">Back to List</button>
            </div>
            <div id="dataView" class="data-view"></div>
            <form id="editForm" style="display:none;"></form>
            <div class="nav-buttons">
                <button id="toggleButton" onclick="toggleEditMode()">Switch to Edit</button>
                <button id="prevButton" onclick="navigateDetails(-1)">Previous</button>
                <button id="nextButton" onclick="navigateDetails(1)">Next</button>
            </div>
        </div>

        <button onclick="exportCSV()">Export CSV</button>
    </div>

    <!-- Include Papa Parse from CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.3.0/papaparse.min.js"></script>

    <script>
        let parsedData = [];
        let headers = [];
        let currentRowIndex = -1;
        let isEditMode = false;
        let selectedColumns = [0, 1, 2]; // Default selected columns for row label

        document.getElementById('fileInput').addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (file) {
                Papa.parse(file, {
                    complete: function(results) {
                        parsedData = results.data.slice(1); // Data excluding headers
                        headers = results.data[0]; // First row as headers
                        populateColumnSelector();
                        populateColumnSelect();
                        displayRows();
                    },
                    header: false,
                    skipEmptyLines: true
                });
            }
        });

        function populateColumnSelector() {
            const columnSelector = document.getElementById('columnSelector');
            columnSelector.innerHTML = '';
            headers.forEach((header, colIndex) => {
                const button = document.createElement('div');
                button.className = 'column-button';
                button.textContent = header;
                if (selectedColumns.includes(colIndex)) {
                    button.classList.add('selected');
                }
                button.onclick = () => toggleColumnSelection(colIndex, button);
                columnSelector.appendChild(button);
            });
        }

        function toggleColumnSelection(colIndex, button) {
            if (selectedColumns.includes(colIndex)) {
                selectedColumns = selectedColumns.filter(col => col !== colIndex);
                button.classList.remove('selected');
            } else {
                selectedColumns.push(colIndex);
                button.classList.add('selected');
            }
            displayRows();
        }

        function populateColumnSelect() {
            const columnSelect = document.getElementById('columnSelect');
            columnSelect.innerHTML = '<option value="">Select Column to Sort</option>';
            headers.forEach((header, colIndex) => {
                const option = document.createElement('option');
                option.value = colIndex;
                option.textContent = header;
                columnSelect.appendChild(option);
            });
        }

        function displayRows() {
            const rowList = document.getElementById('rowList');
            rowList.innerHTML = '';
            parsedData.forEach((row, index) => {
                if (row.length > 3) {
                    const listItem = document.createElement('li');
                    listItem.className = 'row-item';
                    listItem.textContent = `Row ${index + 1}: ${selectedColumns.map(colIndex => row[colIndex]).join(', ')}`;
                    listItem.onclick = () => showDetails(index);
                    rowList.appendChild(listItem);
                }
            });
        }

        function sortRows() {
            const columnIndex = document.getElementById('columnSelect').value;
            if (columnIndex !== "") {
                parsedData.sort((a, b) => {
                    const valueA = a[columnIndex] ? a[columnIndex].toLowerCase() : "";
                    const valueB = b[columnIndex] ? b[columnIndex].toLowerCase() : "";
                    return valueA.localeCompare(valueB);
                });
                displayRows();
            }
        }

        function showDetails(index) {
            currentRowIndex = index;
            const detailsView = document.getElementById('detailsView');
            const dataView = document.getElementById('dataView');
            const form = document.getElementById('editForm');

            let detailsText = '';
            parsedData[index].forEach((value, colIndex) => {
                detailsText += `<strong>${headers[colIndex]}:</strong><br>${value}<br><br>`;
            });

            dataView.innerHTML = detailsText;
            dataView.style.display = 'block';
            form.style.display = 'none';
            document.getElementById('toggleButton').textContent = 'Switch to Edit';

            isEditMode = false;
            detailsView.style.display = 'block';
            updateNavButtons();
        }

        function toggleEditMode() {
            const dataView = document.getElementById('dataView');
            const form = document.getElementById('editForm');
            const toggleButton = document.getElementById('toggleButton');

            if (isEditMode) {
                showDetails(currentRowIndex);
            } else {
                form.innerHTML = '';

                // Convert data to editable fields in edit mode
                parsedData[currentRowIndex].forEach((value, colIndex) => {
                    if (colIndex > 2) {
                        const label = document.createElement('label');
                        label.textContent = headers[colIndex];
                        const textarea = document.createElement('textarea');
                        textarea.value = value;
                        textarea.oninput = function() {
                            parsedData[currentRowIndex][colIndex] = textarea.value; // Auto-save on input
                        };
                        form.appendChild(label);
                        form.appendChild(textarea);
                    }
                });

                // Hide text view and show the form for editing
                dataView.style.display = 'none';
                form.style.display = 'block';
                toggleButton.textContent = 'Switch to View';
            }

            isEditMode = !isEditMode;
        }

        function navigateDetails(step) {
            const newIndex = currentRowIndex + step;
            if (newIndex >= 0 && newIndex < parsedData.length) {
                showDetails(newIndex);
            }
        }

        function updateNavButtons() {
            document.getElementById('prevButton').disabled = currentRowIndex === 0;
            document.getElementById('nextButton').disabled = currentRowIndex === parsedData.length - 1;
        }

        function backToList() {
            document.getElementById('detailsView').style.display = 'none';
        }

        function exportCSV() {
            const csvContent = Papa.unparse([headers, ...parsedData]);
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.setAttribute('href', URL.createObjectURL(blob));
            link.setAttribute('download', 'updated_data.csv');
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
    </script>
</body>
</html>
