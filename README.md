```
{
	  "printStack": {
		"prefix": "printStack",
		"body": [
			"var Color = {",
			"    RESET: \"\\x1b[39;49;00m\",",
			"    Black: \"0;01\",",
			"    Blue: \"4;01\",",
			"    Cyan: \"6;01\",",
			"    Gray: \"7;11\",",
			"    Green: \"2;01\",",
			"    Purple: \"5;01\",",
			"    Red: \"1;01\",",
			"    Yellow: \"3;01\",",
			"    Light: {",
			"        Black: \"0;11\",",
			"        Blue: \"4;11\",",
			"        Cyan: \"6;11\",",
			"        Gray: \"7;01\",",
			"        Green: \"2;11\",",
			"        Purple: \"5;11\",",
			"        Red: \"1;11\",",
			"        Yellow: \"3;11\",",
			"    }",
			"};",
			"var LOG = function (input, kwargs) {",
			"    kwargs = kwargs || {};",
			"    var logLevel = kwargs['l'] || 'log',",
			"        colorPrefix = '\\x1b[3',",
			"        colorSuffix = 'm';",
			"    if (typeof input === 'object')",
			"        input = JSON.stringify(input, null, kwargs['i'] ? 2 : null);",
			"    if (kwargs['c'])",
			"        input = colorPrefix + kwargs['c'] + colorSuffix + input + Color.RESET;",
			"    console[logLevel](input);",
			"};",
		  "var printStack = function () {",
		  "    Java.perform(function() {",
		  "        var android_util_Log = Java.use('android.util.Log'),",
		  "            java_lang_Exception = Java.use('java.lang.Exception');",
		  "        LOG(android_util_Log.getStackTraceString(java_lang_Exception.$$new()), { c: Color.Gray });",
		  "    });",
		  "};"
		],
		"description": "Prints the stack trace."
	  },
	"begin frida":{
		"scope": "javascript,typescript",
		"prefix": "setim",
		"body": ["function hook_java(){\n\tJava.perform(function(){\n\n});\n}\n\nfunction main(){\n\thook_java();\n\thook_native();\n}\n\nfunction hook_native(){\n\n}\nsetImmediate(main)"	
		
		]},
	"frida impl":{
		"scope": "javascript,typescript",
		"prefix": "impl",
		"body": ["implementation= function(){$1}"]
		
	}
}
```
