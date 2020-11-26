# Javascript Excercise: Build a Library

Building a database for library of books, movies, and CDs in Javascript class
syntax.

### Instructions

Congratulations, you’ve passed the grueling rigmarole of librarian school and have become head librarian at your local Books-‘N-Stuff.

Just as you sit down, eager to utilize all those skills you learned in “Lib 203 - Shushing: How to Maintain Order While Spitting”, you realize you’re still using index cards to handle everything.

But no matter, you know some JavaScript, so let’s get to work modernizing your new digs.

Books-‘N-Stuff carries three different types of media: books, CDs, and movies. In this project you will create a parent class named Media with three subclasses: Book, Movie, and CD. These three subclasses have the following properties and methods:

#### Book
- <stonrg>Properties</strong>: author (string), title (string), pages (number), isCheckedOut (boolean, initially false), and ratings (array, initially empty).
- <stonrg>Getters</strong>: all properties have a getter
- <stonrg>Methods</strong>: .getAverageRating(), .toggleCheckOutStatus(), and .addRating()

#### Movie
- <stonrg>Properties</strong>: director (string), title (string), runTime (number), isCheckedOut (boolean, initially false), and ratings (array, initially empty)
- <stonrg>Getters</strong>: all properties have a getter
- <stonrg>Methods</strong>: .getAverageRating(), .toggleCheckOutStatus(), and .addRating()

#### CD
- <stonrg>Properties</strong>: artist (string), title (string), isCheckedOut (boolean, initially false), and ratings (array, initially empty), songs (array of strings)
- <stonrg>Getters</strong>: all properties have a getter
- <stonrg>Methods</strong>: .getAverageRating(), .toggleCheckOutStatus(), and .addRating()


## Javascript
```
//creating a parent class Media
class Media{
  constructor(title){
    this._title = title;
    this._isCheckedOut = false;
    this._ratings = [];
  }
  //creating a getters for tittle, isCheckedOut and ratings
  get title(){
    return this._title;
  }
  
  get isCheckedOut(){
    return this._isCheckedOut;
  }
  
	get ratings(){
    return this._ratings;
  }
  //creating a method toggleCheckOutStatus that changes the valuse saved to the _isCheckedOut property
  toggleCheckOutStatus(){
    this._isCheckedOut = !this._isCheckedOut;
  }
  
  //creating a method getAverageRating that returns an average value of ratings array
  getAverageRating(){
    let ratingsSum = this.ratings.reduce((currentSum, rating) => currentSum + rating, 0)/this._ratings.length;
     return ratingsSum;
    }
  
  //creating a method addRating 
  addRating(ratings){
    this._ratings.push(ratings);
  }
}

//creating a Book class that extends Media/parent class
  class Book extends Media {
    constructor(author, title, pages){
     super(title);
      this._author = author;
      this._pages = pages;
    }
    
    
    //creating a getters for author and pages
    get author(){
      return this._author;
    }
    
    get pages(){
      return this._pages;
    }
  }
  
//creating a Movie class that extends Media/parent class
class Movie extends Media{
  constructor(director, title, runTime){
    super(title);
    this._director = director;
    this._runTime = runTime;
  }
  
  //creating a getters for director and runTime
  get director(){
    return this._director;
  }
  
  get runTime(){
    return this._runTime;
  }
}
 
//creating a Book instance with the following properties
const historyOfEverything = new Book('Bill Bryson', 'A Short History of Nearly Everything', 544);

//calling .toggleCheckOutStatus() on the historyOfEverything instance
historyOfEverything.toggleCheckOutStatus();

//log the value
console.log(historyOfEverything.isCheckedOut);

//call .addRating
historyOfEverything.addRating(4);
historyOfEverything.addRating(5);
historyOfEverything.addRating(5);
historyOfEverything.getAverageRating();

//log the result
console.log(historyOfEverything.getAverageRating());


//creating a Movie instance with the following properties
const speed = new Movie('Jan de Bont', 'Speed', 116);

//Call .toggleCheckOutStatus() on the speed instance.
speed.toggleCheckOutStatus();

//log the value
console.log(speed.isCheckedOut);

//call .addRating
speed.addRating(1);
speed.addRating(1);
speed.addRating(5);
speed.getAverageRating();

//log the result
console.log(speed.getAverageRating());

console.log(historyOfEverything);
console.log(speed);
```