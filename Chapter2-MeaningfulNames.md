```java
/*** YES: what we should do to create good names ***/

// Use Intention-Revealing Names 
//wrong: this reveal nothing.
int d; 
// correct
int elapsedTimeInDays;
int daysSinceCreation ;


// Make Meaningful Distinctions
// wrong: Number-series naming is noninformative
Employee1 = new Employee();
Employee2 = new Employee(); 
// correct
Susan = new Employee();
Tim = new Employee();


// Use Pronounceable Names
// wrong: 使用人都看不懂的单词(比如自己瞎编的缩写)
private Date genymdhms;
// correct: 使用人能看懂的单词(只要意思表达清楚，名字长一点也没关系)
private Date generationTimestamp;


// Use Searchable Names
// correct: 使用constant
const int WORK_DAYS_PER_WEEK = 5;


// Pick One Word per Concept
pick, fetch, get, retrieve是同义词，都表示抓取/获取的概念。确定使用其中的一个之后，不要随意替换


// Use Solution/Problem Domain Names
电商中的SKU，DAU
设计模式 Factor


// Add Meaningful Context	
// wrong: 缺少必要的context 不方便理解
firstName 
// correct: 可以直接从命名中看出该变量表示地址中填写的姓名
addrFirstName 


// Class Name -> noun  Method Name -> verb
// wrong 
class setAccount
String Account()
// correct
class Account
String getAccount()


/*** NO: Avoid doing this to create good names ***/

// Gratuitous Context
GSDAccountAddress // GSD is an imaginary application
GSDMailingAddress // it's a bad idea to prefix every class with GSD


// Avoid Disinformation: leave false clues that obscure the meaning of code
// wrong
hp, ftp, http 不要使用常用的缩写以及保留字
将本身并不是List类型的数据命名为 accountList


// Mental Mapping: have to mentally translate your names into other names they already know
// wrong
for loop 里面明明可以使用i,j,k, 却偏要使用c v h
```
