```sql
-- Create Movies table
CREATE TABLE IF NOT EXISTS movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER,
    length_minutes INTEGER,
    aspect_ratio FLOAT,
    language TEXT DEFAULT 'English'
);

-- Insert sample data into Movies table
INSERT INTO movies (id, title, director, year, length_minutes, aspect_ratio, language)
VALUES
(1, 'Toy Story', 'John Lasseter', 1995, 81, 1.33, 'English'),
(2, 'A Bug\'s Life', 'John Lasseter', 1998, 95, 1.33, 'English'),
(3, 'Toy Story 2', 'John Lasseter', 1999, 93, 1.33, 'English'),
(4, 'Monsters, Inc.', 'Pete Docter', 2001, 92, 1.85, 'English'),
(5, 'Finding Nemo', 'Andrew Stanton', 2003, 107, 1.85, 'English'),
(6, 'The Incredibles', 'Brad Bird', 2004, 116, 2.35, 'English'),
(7, 'Cars', 'John Lasseter', 2006, 117, 1.85, 'English'),
(8, 'Ratatouille', 'Brad Bird', 2007, 115, 2.35, 'English'),
(9, 'WALL-E', 'Andrew Stanton', 2008, 104, 1.85, 'English'),
(10, 'Up', 'Pete Docter', 2009, 101, 1.85, 'English'),
(11, 'Toy Story 3', 'Lee Unkrich', 2010, 103, 1.85, 'English'),
(12, 'Cars 2', 'John Lasseter', 2011, 120, 1.85, 'English'),
(13, 'Brave', 'Brenda Chapman', 2012, 102, 2.35, 'English'),
(14, 'Monsters University', 'Dan Scanlon', 2013, 110, 1.85, 'English');

-- Create BoxOffice table
CREATE TABLE IF NOT EXISTS boxoffice (
    movie_id INTEGER PRIMARY KEY,
    rating FLOAT,
    domestic_sales INTEGER,
    international_sales INTEGER,
    FOREIGN KEY (movie_id) REFERENCES movies(id)
);

-- Insert sample data into BoxOffice table
INSERT INTO boxoffice (movie_id, rating, domestic_sales, international_sales)
VALUES
(1, 8.3, 191796000, 242000000),
(2, 6.8, 162000000, 121000000),
(3, 7.9, 245000000, 198000000),
(4, 8.1, 289000000, 527000000),
(5, 8.1, 380000000, 520000000),
(6, 8.0, 261000000, 413000000),
(7, 7.1, 244000000, 190000000),
(8, 8.0, 206000000, 621000000),
(9, 8.4, 223000000, 533000000),
(10, 8.2, 293000000, 344000000),
(11, 8.3, 415000000, 613000000),
(12, 6.2, 191000000, 368000000),
(13, 7.1, 237000000, 150000000),
(14, 7.3, 269000000, 541000000);

-- Create Database table
CREATE TABLE IF NOT EXISTS database_info (
    name TEXT,
    version FLOAT,
    download_count INTEGER
);

-- Insert sample data into Database table
INSERT INTO database_info (name, version, download_count)
VALUES
('MovieDB', 1.0, 50000),
('BoxOfficeDB', 2.1, 30000);

-- Create a Custom Info table (example table for additional data)
CREATE TABLE IF NOT EXISTS custom_info (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    description TEXT,
    value TEXT
);

-- Insert sample data into Custom Info table
INSERT INTO custom_info (description, value)
VALUES
('Highest Grossing Movie', 'Avengers: Endgame'),
('Most Watched Movie', 'Avatar');

-- Create User Activity table
CREATE TABLE IF NOT EXISTS user_activity (
    user_id INTEGER PRIMARY KEY,
    activity TEXT,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Insert sample data into User Activity table
INSERT INTO user_activity (user_id, activity)
VALUES
(1, 'Logged in'),
(2, 'Watched Toy Story'),
(3, 'Added movie to favorites'),
(4, 'Watched Cars 2');
```

### Summary of Data Inserted:

1. **Movies Table**: Movies data with details like title, director, year, length, aspect ratio, and language.
2. **BoxOffice Table**: Box office ratings and sales for each movie.
3. **Database Table**: Information about the database name, version, and download count.
4. **Custom Info Table**: Custom information for tracking additional data.
5. **User Activity Table**: Tracking user activities along with timestamps.

This SQL code creates the tables and populates them with data.
