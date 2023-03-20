import psycopg2


# connect to "chinook" database
connection = psycopg2.connect(database="chinook")

# build a cursor object of the database
cursor = connection.cursor()

# Query 1 - select all records from the "Artist" table
# cursor.execute('SELECT * FROM "Artist"')

# Query 2 - select only the "Name" column from the "Artist" table
# cursor.execute('SELECT "Name" FROM "Artist"')

# Query 3 - select only "Queen" from the "Artist" table
# cursor.execute('SELECT * FROM "Artist" WHERE "Name" = %s', ["Queen"])

# Query 4 - select only by "ArtistId" #51 from the "Artist" table
# cursor.execute('SELECT * FROM "Artist" WHERE "ArtistId" = %s', [51])

# Query 5 - select only the albums with "ArtistId" #51 on the "Album" table
# cursor.execute('SELECT * FROM "Album" WHERE "ArtistId" = %s', [51])

# Query 6 - select all tracks where the composer is "Queen" from the "Track" table
# cursor.execute('SELECT * FROM "Track" WHERE "Composer" = %s', ["Queen"])

# fetch the results (multiple)
results = cursor.fetchall()

# fetch the result (single)
# results = cursor.fetchone()

# close the connection
connection.close()

# print results
for result in results:
    print(result)


pip3 install psycopg2   #install psycopg2
touchsql-psycopg2.py    # create the file
python3 sql-psycopg2.py # run the file
pip3 install sqlalchemy==1.4.46 #install SQL Alchemy

Create a new file called "sql-expression.py"
touch sql-expression.py
Query 1 - select all records from the "Artist" table
select_query = artist_table.select()
Query 2 - select only the "Name" column from the "Artist" table
select_query = artist_table.select().with_only_columns([artist_table.c.Name])
Query 3 - select only 'Queen' from the "Artist" table
select_query = artist_table.select().where(artist_table.c.Name == "Queen")
Query 4 - select only by 'ArtistId' #51 from the "Artist" table
select_query = artist_table.select().where(artist_table.c.ArtistId == 51)
Query 5 - select only the albums with 'ArtistId' #51 on the "Album" table
select_query = album_table.select().where(album_table.c.ArtistId == 51)
Query 6 - select all tracks where the composer is 'Queen' from the "Track" table
select_query = track_table.select().where(track_table.c.Composer == "Queen")

python3 sql-expression.py

