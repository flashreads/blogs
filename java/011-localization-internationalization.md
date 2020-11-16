---
id: 011-localization-internationalization.md
title: Localization and Internationalization
tags:
  - language-support
  - localization
  - internationalization
author: Kushagra Shukla
meta-description: Add multiple language support to your application without changing the code base.
date: 2020-10-31 04:49:28 +0530
template: post
categories:
  - java
cover: ../images/categories/java.png
---

# Localization and Internationalization
You have made an application in Java and everyone is liking your work but there is one issue, not many people know your local language and hence the larger audience is unable to use your application. You want to add support for mutiple languages so that people from across the world can use your application. But there is one small problem you only know 3-4 languages :stuck_out_tongue_winking_eye:

Do not worry `Locale` and `ResourceBundle` have come to your rescue. These two classes are available under `java.util` package. 

## Locale
Locale class will be used to store information about language as per ISO language codes.
Now what is this?
Each Locale is defined usign two things:
- language code 
- country code

In ISO format two letters are used for describing language code (small) as well as country code (capitalized).
For example: **English** and **Indian** locale would be **en IN**, similarly **Portuguese** and **Brazil** locale would be **pt BR**.
In code a Locale object will be instantiated like this: `Locale localeObj = new Locale(language,country);` where language could be String containing "en" or "pt" or any other language code. Similarly, country String could hold "IN" or "BR" or any other country code.

## Properties Files
It's fancy name for a file that stores **key-value pairs**. Basically we will use this file to store all the strings that we display in our application. Now, you can see how this will function. We will use same keys but change values for supporting different laguages and store it in a new properties file `MessageBundle_<lannguage code>_<country code>.properties`.
There will be one **default** properties file which will contain original strings that you have used in application. This properties files will be named as `MessageBundle.properties`. Let's assume that the application was written in Portuguese and now we want to add support for English then we will have to create a `MessageBundle_en_IN.properties` file. You can see what the contents may look like.
![Two Properties Files](https://i.imgur.com/rh5ZZ8r.png)

## ResourceBundle
This class provides functionality to read properties files. But as you can see there can be many such files. Thus, it requires `Locale` object and `"path/to/MessageBundle"` to narrow down on which file to use.
In code an object will be instantiated like this: `Resource messageObj = ResourceBundle("MessageBundle", localeObj);`
We read values from properies files using **getString()** function by passing **key** as argument as shown, `String str = messageObj.getString("Norte")` where Norte is a key in properties file.

## Code more Talk less
Create Language.java file (only to follow SPOC and modularize the code)
```
import java.util.ResourceBundle;
import java.util.Locale;

public class Language {
    private Locale locale;
    public static ResourceBundle messages;
    public String lang;
    public String country;

    Language(){
        // default lamguage is potuguese
        this.lang = "pt";
        this.country = "PT";
        this.locale = new Locale(this.lang, this.country);
        messages = ResourceBundle.getBundle("MessageBundle", this.locale);
    }

    Language(String lang, String country){
        this.lang = lang;
        this.country = country;
        this.locale = new Locale(this.lang,this.country);
        messages = ResourceBundle.getBundle("MessageBundle", this.locale);
    }

    public String getMessage(String key){
        return messages.getString(key);
    } 

}
```
Create Work.java
```
class Work.java{

// Language class defined above
private static Language langObj;

public static void main(String[] args){

		// user input
		try{	
			String language = new String(args[0]);
			String country = new String(args[1]);
			langObj = new Language(language,country);
		}
		catch(Exception e){
      // use default language
			langObj = new Language();
		}
    
    // before when Strings were written 
    // String Monstro_Cachorro_Dormindo = "ha um cachorro grande dormindo ao pe de uma arvore";
    
    // after replacing it 
    String Monstro_Cachorro_Dormindo = langObj.getMessage("Monstro_Cachorro_Dormindo");
    
    // Can also write as below, for cases where object cannot be referenced or passed.
    // String Monstro_Cachorro_Dormindo = Language.messages.getString("Monstro_Cachorro_Dormindo");
    
    System.out.println(Monstro_Cachorro_Dormindo);
    
    }
  }
}
```
In above program, if no input is given then we get output in Portuguese `ha um cachorro grande dormindo ao pe de uma arvore` and if `en IN` is given as input then output is in English `there is a big dog sleeping at the foot of a tree`.
Similarly, if we want to add support for French then we will have to create a MessageBundle_fr_FR.properties file only and pass `fr FR` as input for language selection and get the output in desired language without changing even a single line of code.

The example code shown is very simple but works well to explain the working. Similar functionality can be achieved in any kind of application large or small.
