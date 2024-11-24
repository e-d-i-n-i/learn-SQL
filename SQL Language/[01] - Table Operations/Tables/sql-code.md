```sql
-- Create Movies table
CREATE TABLE IF NOT EXISTS movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER,
    length_minutes INTEGER
);

-- Insert data into Movies table
INSERT INTO movies (id, title, director, year, length_minutes)
VALUES
(1, 'Toy Story', 'John Lasseter', 1995, 81),
(2, 'A Bug\'s Life', 'John Lasseter', 1998, 95),
(3, 'Toy Story 2', 'John Lasseter', 1999, 93),
(4, 'Monsters, Inc.', 'Pete Docter', 2001, 92),
(5, 'Finding Nemo', 'Andrew Stanton', 2003, 107),
(6, 'The Incredibles', 'Brad Bird', 2004, 116),
(7, 'Cars', 'John Lasseter', 2006, 117),
(8, 'Ratatouille', 'Brad Bird', 2007, 115),
(9, 'WALL-E', 'Andrew Stanton', 2008, 104),
(10, 'Up', 'Pete Docter', 2009, 101),
(11, 'Toy Story 3', 'Lee Unkrich', 2010, 103),
(12, 'Cars 2', 'John Lasseter', 2011, 120),
(13, 'Brave', 'Brenda Chapman', 2012, 102),
(14, 'Monsters University', 'Dan Scanlon', 2013, 110),
(87, 'WALL-G', 'Brenda Chapman', 2042, 97);

-- Create North American Cities table
CREATE TABLE IF NOT EXISTS north_american_cities (
    city TEXT,
    country TEXT,
    population INTEGER,
    latitude FLOAT,
    longitude FLOAT
);

-- Insert data into North American Cities table
INSERT INTO north_american_cities (city, country, population, latitude, longitude)
VALUES
('Guadalajara', 'Mexico', 1500800, 20.659699, -103.349609),
('Toronto', 'Canada', 2795060, 43.653226, -79.383184),
('Houston', 'United States', 2195914, 29.760427, -95.369803),
('New York', 'United States', 8405837, 40.712784, -74.005941),
('Philadelphia', 'United States', 1553165, 39.952584, -75.165222),
('Havana', 'Cuba', 2106146, 23.05407, -82.345189),
('Mexico City', 'Mexico', 8555500, 19.432608, -99.133208),
('Phoenix', 'United States', 1513367, 33.448377, -112.074037),
('Los Angeles', 'United States', 3884307, 34.052234, -118.243685),
('Ecatepec de Morelos', 'Mexico', 1742000, 19.601841, -99.050674),
('Montreal', 'Canada', 1717767, 45.501689, -73.567256),
('Chicago', 'United States', 2718782, 41.878114, -87.629798);

-- Create Boxoffice table
CREATE TABLE IF NOT EXISTS boxoffice (
    movie_id INTEGER,
    rating FLOAT,
    domestic_sales INTEGER,
    international_sales INTEGER,
    PRIMARY KEY (movie_id),
    FOREIGN KEY (movie_id) REFERENCES movies(id)
);

-- Insert data into Boxoffice table
INSERT INTO boxoffice (movie_id, rating, domestic_sales, international_sales)
VALUES
(5, 8.2, 380843261, 555900000),
(14, 7.4, 268492764, 475066843),
(8, 8.0, 206445654, 417277164),
(12, 6.4, 191452396, 368400000),
(3, 7.9, 245852179, 239163000),
(6, 8.0, 261441092, 370001000),
(9, 8.5, 223808164, 297503696),
(11, 8.4, 415004880, 648167031),
(1, 8.3, 191796233, 170162503),
(7, 7.2, 244082982, 217900167),
(10, 8.3, 293004164, 438338580),
(4, 8.1, 289916256, 272900000),
(2, 7.2, 162798565, 200600000),
(13, 7.2, 237283207, 301700000);

-- Create Buildings table
CREATE TABLE IF NOT EXISTS buildings (
    building_name TEXT,
    capacity INTEGER
);

-- Insert data into Buildings table
INSERT INTO buildings (building_name, capacity)
VALUES
('1e', 24),
('1w', 32),
('2e', 16),
('2w', 20);

-- Create Employees table
CREATE TABLE IF NOT EXISTS employees (
    role TEXT,
    name TEXT,
    building TEXT,
    years_employed INTEGER
);

-- Insert data into Employees table
INSERT INTO employees (role, name, building, years_employed)
VALUES
('Engineer', 'Becky A.', '1e', 4),
('Engineer', 'Dan B.', '1e', 2),
('Engineer', 'Sharon F.', '1e', 6),
('Engineer', 'Dan M.', '1e', 4),
('Engineer', 'Malcom S.', '1e', 1),
('Artist', 'Tylar S.', '2w', 2),
('Artist', 'Sherman D.', '2w', 8),
('Artist', 'Jakob J.', '2w', 6),
('Artist', 'Lillia A.', '2w', 7),
('Artist', 'Brandon J.', '2w', 7),
('Manager', 'Scott K.', '1e', 9),
('Manager', 'Shirlee M.', '1e', 3),
('Manager', 'Daria O.', '2w', 6);
```

### Summary of Data Inserted:

1. **Movies Table**: Movies data with titles, directors, release years, and lengths.
2. **North American Cities Table**: Data on cities across North America, including population, latitude, and longitude.
3. **Boxoffice Table**: Box office information for each movie (rating, domestic sales, and international sales).
4. **Buildings Table**: Information about different buildings and their capacities.
5. **Employees Table**: Employee details, including role, name, building, and years employed.

This SQL code creates the tables and inserts the data into them as you specified.
