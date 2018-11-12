// Class for creating and using structured string. A structured string is a string that  
// contains only alphanumeric chars between squared brackets like [foo]. A string may be
// composed for one or more strings like: [foo][bar]. When a new string is added, the 
// current value get nested: if you add [zoop] to [foo][bar] the result will be
// [[foo][bar]][zoop].  
class StructuredString{

	constructor(str){
		if(!this.isNullOrEmpty(str)&&this.validateString(str))
			this._strucStr = str;
	}
	
	
	//Verifies that the square brackets are balanced
	//Returns <true> if the brackets are balanced
	isStringBalanced([...str]) {return str.reduce((bracketCount, thisChar) => {
		 if(thisChar === '[' ) {
				return ++bracketCount;
			} else if ( thisChar === ']') {
				return --bracketCount;
			}
	
		return bracketCount;
	}, 0) === 0 }
	
	//Verifies that the string contains only squared brackets
	//and alfanumeric chars
	//Returns <true> if the string contains only  valid chars 
	containsOnlyValidChars(str){
		return !new RegExp(/[^a-zA-Z0-9\[\]]/g).test(str);
	}

	//Verifies that all chars are enclosed between brackets
	//[abc[foo]] would return false
	//Returns <true> if all chars are enclosed in [] brackets
	areCharsEnclosed(str){
		return !new RegExp(/(\][A-Za-z0-9]+|[A-Za-z0-9]+\[)/g).test(str);
	}

	//Checks if a string has empty brackets []
	//Returns <true> if there is 1+ empty brackets set
	areEmptyBrackets(str){
		return new RegExp(/\[\]/g).test(str);
	}
	
	//Checks if a string is null or empty
	//returns <true> if the string is null or empty
	isNullOrEmpty(str){return !str;}

	//Validates if a string has the right format
	validateString(str){
		return !this.areEmptyBrackets(str)&&this.isStringBalanced(str)&&this.containsOnlyValidChars(str)&&this.areCharsEnclosed(str);
	}


	//Concats a new string, nesting the current one 
	//If current string is [foo][bar] and new string is [zop]
	//the resulting string would be [[foo][bar]][zop]
	addString(newStr){
		if(!this.isNullOrEmpty(newStr)){
			//if the current value is null or empty 
			//assign the new value as is
			//If the current value is not empty, nest the current value
			//and concat the new one
			if(this.isNullOrEmpty(this._strucStr))
				this._strucStr = newStr;
			else
				if(this.validateString(newStr))
					this._strucStr = "["+this._strucStr+"]"+newStr;
		}
	}	
	
	//Gets the current value
	getValue(){
		return this._strucStr;
	}
	
	//Sets the value
	setValue(nStr){
		if(this.isNullOrEmpty(nStr))
			this._strucStr = ""; 
		else if(this.validateString(nStr))
			this._strucStr = nStr; 
	}
	
}

