<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python List Methods</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
        }
        h1 {
            text-align: center;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
        }
        th, td {
            padding: 10px;
            border: 1px solid #ddd;
            text-align: left;
        }
        th {
            background-color: #333;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Python List Methods</h1>
    <table>
        <tr>
            <th>Method</th>
            <th>Description</th>
        </tr>
        <tr><td>append(item)</td><td>Adds an item to the end of the list.</td></tr>
        <tr><td>extend(iterable)</td><td>Extends the list by adding elements from an iterable.</td></tr>
        <tr><td>insert(index, item)</td><td>Inserts an item at a specified index.</td></tr>
        <tr><td>remove(item)</td><td>Removes the first occurrence of an item.</td></tr>
        <tr><td>pop(index=-1)</td><td>Removes and returns the item at the given index (default is last).</td></tr>
        <tr><td>clear()</td><td>Removes all elements from the list.</td></tr>
        <tr><td>index(item, start=0, end=len(list))</td><td>Returns the index of the first occurrence of an item.</td></tr>
        <tr><td>count(item)</td><td>Returns the number of times an item appears.</td></tr>
        <tr><td>sort(key=None, reverse=False)</td><td>Sorts the list in ascending order (default) or descending if reverse=True.</td></tr>
        <tr><td>reverse()</td><td>Reverses the elements in the list.</td></tr>
        <tr><td>copy()</td><td>Returns a shallow copy of the list.</td></tr>
    </table>
</body>
</html>
