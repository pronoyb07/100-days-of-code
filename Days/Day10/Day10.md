
# Day10/100

Today I  Learned About TypeScript. I am worked in Javascript and Some Time Finding Bug in Javascript code Become more complex Task. As, TypeScript is Super Set of Javascript and also provide some cool thing like data type, Interface, etc. Thus, I Stated to learnTypeScript.



Today, I Learned about data type, Interface, Class, Function in TypeScript. Here is My Code which I Write for just Practice purposes.

 More:



```Js
//Basic
let zeel:String="zeel"
let x:number=12

let y:number | String=12;
y='zeel'

let t:number | String | String[] | number[]=12;

const a:number[]=[2,3]

type ID=number


let any:any;

interface MyData{
    Id:ID,
    name:String,
    age:number,
    time?:number
}


let obg :MyData | String={
    Id:12,
    name:'zeel',
    age:12
}




// console.log(t1)
// console.log(obg.name);


//diff
//1 variable type
//2 function type
//3 interface
//4 good code control


//functions

const getDate=():string|number|string[]=>{
    return 'this is date';
}

function demo():number{
    return;
}


//if...else
//data type
//class
//synnex

//class

class person{
    gender:String
    name: String
    constructor(name:String){
        this.name=name;
    }

    getName():String{
        return this.name;
    }
}

class male extends person{
    
}

interface Boy{

    setAge(age:number)
}

class Man implements Boy{

    setAge(a:number):number
    {
        console.log(a);
        return a;
    }
   
}

// const m=new Man();
// m.setAge(12);
// const myfirend=new male("zeel");
// console.log(myfirend.getName());


//class ->private/public/protected
//      ->inheritance
//      ->interface


//generic


class List<T extends object>{

    private arr:T[]=[];

    add(n:T):boolean{
        this.arr.push(n);
        return true;
    }

    pritData(){
        console.log(this.arr);
    }
}

interface data{
    Id?:String,
    name?:String
}


const l=new List<data>();
// const l=new List<Required<data>>();
l.add({Id:'zeel'});
l.pritData();
```