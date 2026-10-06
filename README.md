# Media Catalogue App

A robust Python application built using Object-Oriented Programming (OOP) principles to manage, categorize, and format collections of movies and TV series with custom error handling and strict data validation.

## Features

- **Class Hierarchy & Inheritance**: Built a foundational `Movie` parent class and extended it with a specialized `TVSeries` child class using `super().__init__()`.
- **Strict Data Validation**: Validates inputs during instantiation to prevent empty titles, invalid release years (< 1895), empty directors, and non-positive durations or season counts.
- **Custom Exception Handling**: Implemented a dedicated `MediaError` class to catch and report media validation failures while preserving the failing object context.
- **Type Discrimination**: Uses `type()` checks to strictly separate base `Movie` objects from `TVSeries` instances.
- **Formatted String Representation**: Overrides `__str__` methods to output organized catalog listings with 1-based indexing, dynamic category headers, and clear multi-line formatting.

## Code Structure

- **`Movie` Class**: Represents standalone movie items with properties for title, release year, director, and duration in minutes.
- **`TVSeries` Class**: Inherits from `Movie` while adding specific attributes for seasons and total episode count.
- **`MediaCatalogue` Class**: Stores media objects in an internal list (`self.items`) and provides methods to add items, filter by type (`get_movies`, `get_tv_series`), and display the complete catalogue.
- **`MediaError` Class**: A custom exception class inheriting from `Exception` that stores the invalid object causing the runtime error.

## Example Usage

```python
catalogue = MediaCatalogue()

try:
    movie1 = Movie('The Matrix', 1999, 'The Wachowskis', 136)
    movie2 = Movie('Inception', 2010, 'Christopher Nolan', 148)
    series1 = TVSeries('Scrubs', 2001, 'Bill Lawrence', 24, 9, 182)
    series2 = TVSeries('Breaking Bad', 2008, 'Vince Gilligan', 47, 5, 62)

    catalogue.add(movie1)
    catalogue.add(movie2)
    catalogue.add(series1)
    catalogue.add(series2)

    print(catalogue)
except MediaError as e:
    print(f"Catalogue Error: {e}")