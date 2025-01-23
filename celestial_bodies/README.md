## 1. Create the `universe` Database and Connect to It
```sql
CREATE DATABASE universe;
\c universe;
```

---

## 2. Create the Tables with the Specified Requirements

### a. `galaxy` Table
```sql
CREATE TABLE galaxy (
    galaxy_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    size_in_light_years NUMERIC NOT NULL,
    spiral BOOLEAN NOT NULL,
    description TEXT
);
```

### b. `star` Table
```sql
CREATE TABLE star (
    star_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    galaxy_id INT NOT NULL REFERENCES galaxy(galaxy_id),
    temperature INT NOT NULL,
    main_sequence BOOLEAN NOT NULL
);
```

### c. `planet` Table
```sql
CREATE TABLE planet (
    planet_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    star_id INT NOT NULL REFERENCES star(star_id),
    radius_in_km NUMERIC NOT NULL,
    habitable BOOLEAN NOT NULL
);
```

### d. `moon` Table
```sql
CREATE TABLE moon (
    moon_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    planet_id INT NOT NULL REFERENCES planet(planet_id),
    diameter_in_km INT NOT NULL,
    atmosphere BOOLEAN NOT NULL
);
```

### e. Additional Table (`space_station`)
```sql
CREATE TABLE space_station (
    space_station_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE,
    crew_capacity INT NOT NULL,
    orbiting_planet_id INT REFERENCES planet(planet_id),
    active BOOLEAN NOT NULL
);
```

---

## 3. Insert Rows into the Tables

### a. Insert Rows into `galaxy`
```sql
INSERT INTO galaxy (name, size_in_light_years, spiral, description) VALUES
('Milky Way', 105700, TRUE, 'The galaxy that contains our solar system.'),
('Andromeda', 220000, TRUE, 'A neighboring galaxy.'),
('Triangulum', 60000, TRUE, 'A member of the Local Group.'),
('Large Magellanic Cloud', 14000, FALSE, 'A satellite galaxy of the Milky Way.'),
('Small Magellanic Cloud', 7000, FALSE, 'Another satellite galaxy of the Milky Way.'),
('Whirlpool', 76000, TRUE, 'Known for its spiral arms.');
```

### b. Insert Rows into `star`
```sql
INSERT INTO star (name, galaxy_id, temperature, main_sequence) VALUES
('Sun', 1, 5778, TRUE),
('Sirius', 1, 9940, TRUE),
('Betelgeuse', 1, 3500, FALSE),
('Rigel', 1, 11000, FALSE),
('Proxima Centauri', 1, 3042, TRUE),
('Vega', 2, 9602, TRUE);
```

### c. Insert Rows into `planet`
```sql
INSERT INTO planet (name, star_id, radius_in_km, habitable) VALUES
('Earth', 1, 6371, TRUE),
('Mars', 1, 3389, FALSE),
('Venus', 1, 6051, FALSE),
('Jupiter', 1, 69911, FALSE),
('Saturn', 1, 58232, FALSE),
('Proxima b', 5, 7200, TRUE),
('Kepler-22b', 6, 12800, TRUE),
('Gliese 581g', 5, 2500, TRUE),
('Neptune', 1, 24622, FALSE),
('Uranus', 1, 25362, FALSE),
('Mercury', 1, 2440, FALSE),
('Alpha Centauri Bb', 6, 1500, FALSE);
```

### d. Insert Rows into `moon`
```sql
INSERT INTO moon (name, planet_id, diameter_in_km, atmosphere) VALUES
('Moon', 1, 3474, FALSE),
('Phobos', 2, 22, FALSE),
('Deimos', 2, 12, FALSE),
('Io', 4, 3642, TRUE),
('Europa', 4, 3122, TRUE),
('Ganymede', 4, 5262, TRUE),
('Callisto', 4, 4820, FALSE),
('Titan', 5, 5150, TRUE),
('Rhea', 5, 1528, FALSE),
('Iapetus', 5, 1469, FALSE),
('Triton', 9, 2706, TRUE),
('Oberon', 10, 1523, FALSE),
('Umbriel', 10, 1190, FALSE),
('Titania', 10, 1577, FALSE),
('Miranda', 10, 471, FALSE),
('Enceladus', 5, 504, TRUE),
('Mimas', 5, 396, FALSE),
('Hyperion', 5, 270, FALSE),
('Dione', 5, 1123, FALSE),
('Tethys', 5, 1062, FALSE);
```

### e. Insert Rows into `space_station`
```sql
INSERT INTO space_station (name, crew_capacity, orbiting_planet_id, active) VALUES
('ISS', 6, 1, TRUE),
('Mars Base Alpha', 50, 2, FALSE),
('Lunar Gateway', 10, 1, TRUE);
```

---

## 4. Verify the Database Structure
- **List Tables**:
    ```sql
    \dt
    ```
- **Describe Each Table**:
    ```sql
    \d galaxy
    \d star
    \d planet
    \d moon
    \d space_station
    ```

This setup satisfies all the requirements, including:
- Primary and foreign keys.
- Constraints (`NOT NULL`, `UNIQUE`, etc.).
- Use of appropriate data types (`NUMERIC`, `TEXT`, `BOOLEAN`, etc.).
- Sufficient rows for each table.
