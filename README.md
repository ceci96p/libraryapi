# libraryapi
Developer Library Test Project

The api is located at: https://aka-library-api.azurewebsites.net/api

The api help is located at: https://aka-library-api.azurewebsites.net/docs

NOTE: just navigation to the https://aka-library-api.azurewebsites.net/api in your browser will not produce any results, as intended.

# Notes

#1 (Compilation Error) Fix “Type '(items: any) => any' is not assignable to type 'NumericDictionary<unknown>' ” error. 
  
  - I understand the 'getBooks' function in 'BooksService' was calling the wrong map function from lodash when it should have been the one from rxjs


#2 (Bug) Fix the AuthGuard to ensure that the member is logged in properly. 
 
 - I changed the 'login' function in 'AuthService' to update the loggedIn observable to true once authetication had happened and was true
 
#3 Update the listing of the library books to show if the book can be signed out (any copies left). A book is not available if all copies are signed out.  This is found on the book listing page for a library.

 - The way I understood this task was that I had to only display the books that were available for each library book list, so I filtered the array of books before      displaying to only those that were available

#4 Create a new component in the checked-out module that lists all previously checked out books of the logged in member.
  +Add a route to access this component in the of checked-out module 
  +Verify that the user can load the page when clicking the navigation button.
  
  - I did not got the chance to look at this indepth but I understood that I had to create a new Angular component and then make a route that woud allow me to get there from the checked-out module and that it had to be viewable from 'Checked Out' option from the main menu

#5 On the profile page please add the existing components for the two checkout module components in the tab on the page
  +Currently checked-out books components
  +Checked-out books history
  
  - I did not got the chance to look at this in-depth but the idea would be to get the list of the checked-out by userID when calling GET '/api/members/{id}' and then use the fields "whenSignedOut"  and "whenReturned" dates to display the 'Checked-out books history' and for the objects that have "whenReturned" value == null then would be part of the 'Currently checked-out books components" list

#6 In the BooksService the getBookMetaData should return the books metadata(GoogleBooksMetadata). Please integrate with the google books api to get meta data for the book and display it in the book details component.

  - I tried to write this function by doing a get REST operation to get the json file from the Google Books API and then navigate through the file to return a           'GoogleBooksMetadata' Observable from the fields I needed to fill in the interface for the 'GoogleBooksMetadata'. I did not get a chance to test this because I     could not get the Book Details component to display.


#7 On books details component please complete the following
  +display the number of copies of that book that are available to be checked out.
  +A “Return” link should be available beside each book.  The user can click on the “Return” link to return the book. (The book ID, library ID, and member ID are      known here.)
  +Enforce this restriction No member can have more than two books signed out of the library at any one time.
  +Allow multiple (different) books to be signed out by a member at once.
  +The user cannot sign out more copies than are available of that book.
  +Validation needs to be enforced.
  
  - I wanted to implement this but couldn't figure out why 'BookDetails" wasn't displaying at all, I started implementing some functions without testing, but I understand most of this was to add code to already implemented functions for validation and restrictions

#8 On the library list page fix the layout of the table to look like the sample image below (bug)
  - I fixed this one by making the 'flex-direction' on the css file of the container of the input filter and the list to column instead of row
