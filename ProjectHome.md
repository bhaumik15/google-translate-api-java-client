This project implements a java client that communicates with Google Translate API service to do translations.
It supports the following functionalities as described in  http://code.google.com/intl/zh-TW/apis/ajaxlanguage/documentation/reference.html

1. Translate several strings, all from the same source language to the same target language. This is accomplished through the use of multiple q arguments.

2. Translate one string into several languages. This is accomplished through the use of multiple langpair arguments.

3. Translate a single string from one language to another

Installation is easy: **[download the GoogleTranslateJavaClient.jar](http://google-translate-api-java-client.googlecode.com/files/GoogleTranslateJavaClient.jar)** and include it in your classpath.

The following is a demo code snippet for using this client.

```
import java.util.ArrayList;

import com.google.api.translate.Language;
import com.google.api.translate.Translator;

public class TranslateClientDemo {

	public static void main(String[] args) {		
		// Translate a single English String to French
		Translator translator = new Translator();
		System.out.println("Saying goodbye in French:");
		System.out.println(translator.translate("goodbye", Language.ENGLISH, Language.FRENCH));
		
		System.out.println();
		
		// Translate a single English String to various different languages
		System.out.println("Saying goodbye in different languages:");
		ArrayList<String> translations = translator.translate("goodbye", Language.ENGLISH, Language.ITALIAN, Language.DUTCH, Language.CHINESE_TRADITIONAL);
		for (String translation : translations) {
			System.out.println(translation);
		}
		
		System.out.println();
		
		// Translate multiple strings from one language to another
		System.out.println("Saying goodbye and hello in French:");
		translations = translator.translate(Language.ENGLISH, Language.FRENCH, "goodbye", "hello");
		for (String translation : translations) {
			System.out.println(translation);
		}
	}

}
```