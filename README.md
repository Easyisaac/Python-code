python code
#library management system
class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn


class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def remove_book(self, book):
        if book in self.books:
            self.books.remove(book)
        else:
            print("Book not found in the library.")

    def search_book(self, title):
        for book in self.books:
            if book.title == title:
                return book
        return None

    def display_books(self):
        if not self.books:
            print("Library is empty.")
        else:
            print("Library Books:")
            for book in self.books:
                print(f"{book.title} by {book.author} (ISBN: {book.isbn})")


def main():
    library = Library()

    while True:
        print("\nLibrary Management System:")
        print("1. Add Book")
        print("2. Remove Book")
        print("3. Search Book")
        print("4. Display Books")
        print("5. Exit")

        choice = int(input("Enter your choice (1-5): "))

        if choice == 1:
            title = input("Enter book title: ")
            author = input("Enter author name: ")
            isbn = input("Enter ISBN: ")
            book = Book(title, author, isbn)
            library.add_book(book)
            print("Book added successfully.")

        elif choice == 2:
            title = input("Enter the title of the book to remove: ")
            book_to_remove = library.search_book(title)
            if book_to_remove:
                library.remove_book(book_to_remove)
                print("Book removed successfully.")
            else:
                print("Book not found in the library.")

        elif choice == 3:
            title = input("Enter the title of the book to search: ")
            book_found = library.search_book(title)
            if book_found:
                print(f"{book_found.title} by {book_found.author} (ISBN: {book_found.isbn})")
            else:
                print("Book not found in the library.")

        elif choice == 4:
            library.display_books()

        elif choice == 5:
            print("Exiting Library Management System.")
            break

        else:
            print("Invalid choice. Please select a valid option (1-5).")


if __name__ == "__main__":
    main()
