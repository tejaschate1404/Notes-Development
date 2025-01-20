

<div class="container mt-5">
        <h2>Django ORM Queries</h2>
           <p>Django's ORM (Object-Relational Mapping) provides a powerful and intuitive way to interact with the database using Python code, abstracting away SQL 
           queries. Here's a deeper dive into how to use Django ORM to interact with your models and retrieve data.</p>
        <div class="mt-4">
            <h4>Retrieve All Records</h4>
            <p><strong>Fetch all records of a model:</strong></p>
            <pre><code>records = Model.objects.all()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Filter Records</h4>
            <p><strong>Filter records by specific conditions:</strong></p>
            <pre><code>records = Model.objects.filter(field=value)</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve a Single Record</h4>
            <p><strong>Fetch a single record by primary key or other fields:</strong></p>
            <pre><code>record = Model.objects.get(id=1)</code></pre>
            <p><strong>Note:</strong> Raises <code>DoesNotExist</code> or <code>MultipleObjectsReturned</code> if no or multiple records are found.</p>
        </div>
        <div class="mt-4">
            <h4>Exclude Records</h4>
            <p><strong>Exclude records that match certain conditions:</strong></p>
            <pre><code>records = Model.objects.exclude(field=value)</code></pre>
        </div>
        <div class="mt-4">
            <h4>Order Records</h4>
            <p><strong>Order records by a field:</strong></p>
            <pre><code>records = Model.objects.all().order_by('field')</code></pre>
            <p><strong>Reverse order:</strong></p>
            <pre><code>records = Model.objects.all().order_by('-field')</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve Distinct Records</h4>
            <p><strong>Get distinct records:</strong></p>
            <pre><code>records = Model.objects.distinct()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Count Records</h4>
            <p><strong>Get the number of records:</strong></p>
            <pre><code>count = Model.objects.count()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve Specific Fields</h4>
            <p><strong>Get specific fields (returns QuerySet of dictionaries):</strong></p>
            <pre><code>records = Model.objects.values('field')</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve List of Values</h4>
            <p><strong>Get values as a list:</strong></p>
            <pre><code>records = Model.objects.values_list('field', flat=True)</code></pre>
        </div>
        <div class="mt-4">
            <h4>Aggregate Values</h4>
            <p><strong>Calculate sum, average, count, etc.:</strong></p>
            <pre><code>from django.db.models import Count, Max, Min, Avg, Sum
aggregate = Model.objects.aggregate(Count('field'))</code></pre>
        </div>
        <div class="mt-4">
            <h4>Create a New Record</h4>
            <p><strong>Create and save a new record:</strong></p>
            <pre><code>record = Model.objects.create(field1=value1, field2=value2)</code></pre>
        </div>
        <div class="mt-4">
            <h4>Update Records</h4>
            <p><strong>Update records matching conditions:</strong></p>
            <pre><code>Model.objects.filter(field=value).update(field2=value2)</code></pre>
        </div>
        <div class="mt-4">
            <h4>Delete Records</h4>
            <p><strong>Delete a specific record:</strong></p>
            <pre><code>record = Model.objects.get(id=1)
record.delete()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Check if Records Exist</h4>
            <p><strong>Check if records exist based on a condition:</strong></p>
            <pre><code>exists = Model.objects.filter(field=value).exists()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve the First Record</h4>
            <p><strong>Fetch the first record:</strong></p>
            <pre><code>first_record = Model.objects.first()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Retrieve the Last Record</h4>
            <p><strong>Fetch the last record:</strong></p>
            <pre><code>last_record = Model.objects.last()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Select Related Models (ForeignKey)</h4>
            <p><strong>Optimize queries with ForeignKey relationships:</strong></p>
            <pre><code>records = Model.objects.select_related('related_model').all()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Prefetch Related Models (Many-to-Many)</h4>
            <p><strong>Optimize queries with ManyToMany or reverse ForeignKey relationships:</strong></p>
            <pre><code>records = Model.objects.prefetch_related('many_to_many_field').all()</code></pre>
        </div>
        <div class="mt-4">
            <h4>Raw SQL Queries</h4>
            <p><strong>Execute raw SQL queries:</strong></p>
            <pre><code>records = Model.objects.raw('SELECT * FROM app_model WHERE field = %s', [value])</code></pre>
        </div>
        <div class="mt-4">
            <h4>Q Objects for Complex Queries</h4>
            <p><strong>Use Q objects to create complex queries:</strong></p>
            <pre><code>from django.db.models import Q
records = Model.objects.filter(Q(field1=value) | Q(field2=value2))</code></pre>
        </div>
        <div class="mt-4">
            <h4>Limit Results (Slice)</h4>
            <p><strong>Limit the number of results returned:</strong></p>
            <pre><code>records = Model.objects.all()[:5]  # First 5 records</code></pre>
        </div>
        <div class="mt-4">
            <h4>Update or Insert if Not Exists (get_or_create)</h4>
            <p><strong>Retrieve an object if it exists, or create a new one:</strong></p>
            <pre><code>record, created = Model.objects.get_or_create(field=value, defaults={'field2': value2})</code></pre>
        </div>
        <div class="mt-4">
            <h4>Update or Return Instance (update_or_create)</h4>
            <p><strong>Update an existing record, or create a new one if it doesn’t exist:</strong></p>
            <pre><code>record, created = Model.objects.update_or_create(field=value, defaults={'field2': value2})</code></pre>
        </div>
    </div>
