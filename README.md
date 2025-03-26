# OOP-Assignment
Activity 1
class Book:  
    def __init__(self, title, author, year, genre):  
        self.title = title          # Public attribute  
        self.author = author        # Public attribute  
        self.year = year            # Public attribute  
        self.genre = genre          # Public attribute  
        self.__is_available = True   # Private attribute  

    def read(self):  
        """Method to simulate reading the book."""  
        if self.__is_available:  
            print(f"Reading '{self.title}' by {self.author}.")  
        else:  
            print(f"'{self.title}' is currently checked out.")  

    def check_out(self):  
        """Method to check out the book."""  
        if self.__is_available:  
            self.__is_available = False  
            print(f"You have checked out '{self.title}'.")  
        else:  
            print(f"'{self.title}' is already checked out.")  

    def return_book(self):  
        """Method to return the book."""  
        if not self.__is_available:  
            self.__is_available = True  
            print(f"You have returned '{self.title}'.")  
        else:  
            print(f"'{self.title}' was not checked out.")  

    def get_info(self):  
        """Return a summary of the book's information."""  
        return f"Title: {self.title}, Author: {self.author}, Year: {self.year}, Genre: {self.genre}"  


# Subclass for EBook  
class EBook(Book):  
    def __init__(self, title, author, year, genre, file_size, format_type):  
        super().__init__(title, author, year, genre)  # Initialize parent class  
        self.file_size = file_size  # Public attribute  
        self.format_type = format_type  # Public attribute  
        self.__downloaded = False      # Private attribute  

    def download(self):  
        """Method to download the e-book."""  
        if not self.__downloaded:  
            self.__downloaded = True  
            print(f"Downloaded '{self.title}' in {self.format_type} format.")  
        else:  
            print(f"'{self.title}' is already downloaded.")  

    def read(self):  
        """Override the read method for EBook."""  
        if self.__downloaded:  
            print(f"Reading '{self.title}' (e-book format: {self.format_type}).")  
        else:  
            print(f"'{self.title}' must be downloaded before reading.")  

    def get_info(self):  
        """Override to include e-book specific information."""  
        parent_info = super().get_info()  
        return f"{parent_info}, File Size: {self.file_size} MB, Format: {self.format_type}"  

# Example usage:  
# Create a regular book instance  
book = Book("1984", "George Orwell", 1949, "Dystopian")  
print(book.get_info())         # Output book details  
book.read()                    # Reading when available  
book.check_out()               # Checking out  
book.read()                    # Try reading after checkout  
book.return_book()             # Returning the book  
book.read()                    # Reading after return  

# Create an e-book instance  
ebook = EBook("Python Programming", "John Doe", 2021, "Technology", 5, "PDF")  
print(ebook.get_info())        # Output e-book details  
ebook.download()               # Downloading the e-book  
ebook.read()                   # Reading the downloaded e-book  
ebook.check_out()              # This method isn't needed for e-books  


Activity 2
class Vehicle:  
    """Base class for all vehicles."""  
    def move(self):  
        raise NotImplementedError("Subclasses must implement this method.")  


class Car(Vehicle):  
    """Class representing a car."""  
    def move(self):  
        print("Driving 🚗")  


class Bike(Vehicle):  
    """Class representing a bike."""  
    def move(self):  
        print("Riding 🚲")  


class Plane(Vehicle):  
    """Class representing a plane."""  
    def move(self):  
        print("Flying ✈️")  


class Boat(Vehicle):  
    """Class representing a boat."""  
    def move(self):  
        print("Sailing ⛵")  


# Example usage  
def move_all_vehicles(vehicles):  
    for vehicle in vehicles:  
        vehicle.move()  

# Creating instances of different vehicles  
vehicles = [  
    Car(),  
    Bike(),  
    Plane(),  
    Boat()  
]  

# Make all vehicles move  
move_all_vehicles(vehicles)  '
