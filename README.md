# Dummy_Data_Generator

Below is an example of a README.md file that explains the purpose of the provided code, how to set it up, and how to use it, including a brief explanation of each functionality:

markdown
Copy code
# Random Book and Character Data Generator

This project contains a Python code that generates random data for books and characters using NLTK (WordNet) and other libraries like `lorem` and `pandas`. The data generated includes authors, book titles, descriptions, publishing dates, and relationships between books and characters.

## Features

- Generate random book titles, descriptions, and publishing dates.
- Create random author names, genders, and book genres.
- Simulate relationships between characters and books.
- Generate random character names and types.

## Setup Instructions

### Prerequisites

Make sure you have the following installed:

    - Python 3.x
    - Pip (Python package manager)

Install the required Python libraries using the following command:

      pip install -r requirements.txt
### Required Libraries:

    random (Python standard library)
    os (Python standard library)
    glob (Python standard library)
    pandas
    numpy
    datetime (Python standard library)
    lorem
    nltk
## You can install the libraries using the following command:


    pip install pandas numpy lorem nltk
### Additional Setup
Download WordNet Data for NLTK: The script requires WordNet data from the NLTK library. Run the following in Python to download it:

    import nltk
    nltk.download('wordnet')
Random Names Dataset: The script expects a CSV file with random names (Random_names_master.csv). The file should have two columns: first_name and last_name.
## Folder Structure

    .
    ├── Random_names_master.csv   # File with random first and last names
    ├── main.py                   # Main Python script
    ├── README.md                 # This README file
    ├── requirements.txt          # List of required libraries
# Code Explanation
The code is built around the DataGen class, which is used to generate random data for books and characters.

DataGen Class
__init__(self, size): Initializes the class with the size parameter, which controls how many entries will be generated.
list_pick(self, choice_list, uniform=True, probability_array=None): Selects random elements from a list either uniformly or non-uniformly based on probabilities.
descr_gen(self): Generates random lorem ipsum text to simulate descriptions.
title_gen(self, list_of_words=noun_list): Generates random book titles using the WordNet noun list.
date_gen(self, start_year=1950, end_year=2020, set_month=None): Generates random dates between specified years.
gen_random_name(self, list_1=first_name_list, list_2=last_name_list): Generates random full names from provided first and last name lists.

Example Usage
## The script uses the DataGen class to generate:

Books: Titles, descriptions, author names, genres, and publishing dates.
Characters: Names and types (e.g., human, alien).
Character-Book Relationships: Links between characters and books.
Here’s an example of how the script generates 10 random books and 50 random characters, and links them:


    Books = DataGen(10)
    book_data = pd.DataFrame({
        'author_name': Books.gen_random_name(),
        'publishing_date': Books.date_gen(2000,2018),
        'title': Books.title_gen(),
        'descr': Books.descr_gen(),
        'book_type': Books.list_pick(['Fiction', 'Non - Fiction'], False, [0.8, 0.2]),
        'author_sex': Books.list_pick(['Male', 'Female'], False, [0.4, 0.6]),
        'genre': Books.list_pick(['Satire', 'Drama', 'Romance', 'Self help'], False, [0.4, 0.4, 0.1, 0.1]),
        'publisher': Books.list_pick(['Hachette', 'HarperCollins', 'Macmillan', 'Penguin Random'])
    })
    
    character = DataGen(50)
    character_data = pd.DataFrame({
        'character_name': character.gen_random_name(),
        'character_type': character.list_pick(['human', 'alien', 'other'], False, [0.5, 0.3, 0.2])
    })
    
    character_book = DataGen(100)
    character_book_relationship = pd.DataFrame({
        'book': character_book.gen_random_name(book_data['title'].tolist(), ['']),
        'character': character_book.gen_random_name(character_data['character_name'].tolist(), [''])
    })


## Output
book_data: A DataFrame containing the generated books with attributes like author name, publishing date, title, description, book type, author gender, genre, and publisher.
character_data: A DataFrame containing the generated characters with attributes like character name and character type.
character_book_relationship: A DataFrame linking the characters to the books they appear in.
Sample Data

        | author_name | publishing_date | title        | descr                   | book_type | author_sex | genre    | publisher       |
        |-------------|-----------------|--------------|-------------------------|-----------|------------|----------|-----------------|
        | John Doe    | 2005/10/15       | animal house | Lorem ipsum dolor sit...| Fiction   | Male       | Drama    | HarperCollins    |
        | Jane Smith  | 2012/05/22       | music paper  | Lorem ipsum dolor sit...| Non-Fiction| Female     | Romance  | Penguin Random   |
## How to Run the Code
Clone the repository or download the script.
Ensure all dependencies are installed using pip install -r requirements.txt.
Run the Python script:

    python main.py
## Customization
You can customize the size of the dataset by changing the argument passed to the DataGen class. For example, to generate 100 books instead of 10, initialize the class as:


Books = DataGen(100)
## License
This project is licensed under the MIT License. See the LICENSE file for more details.

Contact
For questions or support, contact [Link Text](https://github.com/PrasadReddy81) .



    ### Explanation of Each Section
    
    - **Features**: Lists the functionalities of the script.
    - **Setup Instructions**: Explains how to set up the environment and required libraries.
    - **Folder Structure**: Shows how the files should be organized.
    - **Code Explanation**: Describes the key classes and methods in the script.
    - **Example Usage**: Provides an example of how to use the `DataGen` class to generate random data.
    - **Output**: Shows a sample of the generated data for books.
    - **How to Run the Code**: Provides instructions on running the script.
    - **Customization**: Explains how to modify the script for different dataset sizes.






