# Javascript-snippets

## Object creating Patterns



###      Dynamic Prototype pattern


```

var peopleDynamic = function(name , age , state){
  this.age = age;   //create new property as a new object
  this.state = state ;
  this.name = name;
  
  
  if(typeof this.printPerson !== 'function'){   // create new function if  not defined 
  peopleDynamic.prototype.printPerson = function(){  
  console.log(this.name + ', ', + this.age + ', ' + this.state);
  };    
  }
  
};
 

var person1 = new peopleDynamic('talha', 23 , 'CA'); //create object with params

person1.printPerson();

```





###      Prototype Pattern

```

var peopleProto = function(){  //create an empty object as function
  
  };

peopleProto.prototype.age = 0; // create property to prototype
peopleProto.prototype.name = 'no name';
peopleProto.prototype.city = 'no city';
peopleProto.prototype.printPerson = function(){
  
  
  console.log(this.name + ', ', + this.age + ',' + this.city);
};

var person1  = new peopleProto();  // create new object from object
person1.name = 'talha'; //overriding prototype values
person1.age = 26;
person1.city = 'PTA';

person1.printPerson();  // calls prototype function  of object
console.log('name' in person1);

console.log(person1.hasOwnProperty('name'));

```




###      Constructor

```

var peopleConstructor = function(name ,age , state){
  
  this.name = name; // create new property of same object function
  this.age = age;
  this.state = state;
  
  this.printPerson = function(){
     console.log(this.name + ', ' + this.age + ', '+ this.state);
  };
    
};



var person1 = new peopleConstructor('talha' , 27 , 'PTA'); 
// create new object of function object

person1.printPerson();
// call function of created object

```



###      Factory 

```

var peopleFactory = function(name, age, state){
  
  var temp = {};  // create empty object
  
  temp.age = age;  //assigns properties to variables
  temp.name = name; 
  temp.state = state;
  
  temp.printPerson = function(){  // add a function as a property
    
    console.log(this.name + ', ',this.age + ', ' + this.state);
  };
  
  return temp;  // return object itself after adding properties
};

var person1 = peopleFactory('john' , 23 , 'CA'); // create object using returned object 

var person2 = peopleFactory('kim' , 25 , 'SA');

person1.printPerson();  // call property(function) of the created object
person2.printPerson();

```
