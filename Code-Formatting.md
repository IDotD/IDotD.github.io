<pre><code>{
    "tabs and indents":{
        "expand tabs to spaces":true,
        "tab size":4,
        "spaces per indent":4,
        "initial indentation":0,
        "continuation integration":8,
        "example":"var engine = {\n    cylinders: 8,\n    power: \"22k\",\n    getDescription: function () {\n        if ( enabled ) {\n            println ( 'Cylinders: '\n                    + this.cylinders + ' with power: ' + this.power );\n        }\n    }\n}\n\nvar color = computeColor ();\nswitch ( color ) {\n    case 'white':\n    case 'black':\n        code = 0;\n        break;\n    case 'red':\n        code = 1;\n        break;\n    default:\n        code = undefined\n}\n\n"
    },
    "spaces": {
        "beforeKeyword":{
            "while":true,
            "else":true,
            "catch":true,
            "finally":true
        },
        "before parentheses":{
            "anonymus function declaration":true,
            "function declaration":true,
            "function call":true,
            "if":true,
            "for":true,
            "while":true,
            "catch":true,
            "switch":true,
            "with":true
        },
        "around operators":{
            "unary operators":false,
            "binary operators":true,
            "ternary operators":true,
            "assignment operators":true
        },
        "before left braces": {
            "function declaration":true,
            "if":true,
            "else":true,
            "while":true,
            "for":true,
            "do":true,
            "switch":true,
            "try":true,
            "catch":true,
            "finally":true,
            "with":true
        },
        "within parentheses":{
            "parentheses":true,
            "function declaration":true,
            "function call":true,
            "if":true,
            "for":false,
            "while":true,
            "switch":true,
            "catch":true,
            "with":true,
            "braces":true,
            "array initializer brackets":true
        },
        "other":{
            "before comma":false,
            "after comma":true,
            "before semicolon":false,
            "after semicolon":true,
            "before colon":false,
            "after colon":true
        },
        "example":"var engine = {\n    cylinders: 8,\n    power: \"22k\",\n    getDescription: function () {\n        with ( this ) {\n            if ( !disabled ) {\n                println ( 'Cylinders: '\n                        + cylinders + ' with power: ' + power );\n            } else {\n                log ();\n            }\n        }\n    },\n    get parameter () {\n        return power;\n    }\n}\n\nvar colors = [ 0, 1, 2 ]\nfunction computeColor ( limit ) {\n    try {\n        color = 0;\n        for (var a = -1; a < limit; a++) {\n            color += Math.round ( Math.random () * 2 );\n        }\n    } catch ( error ) {\n        println ( error );\n    } finally {\n        log ();\n    }\n    while ( color > 100 ) {\n        do {\n            color = ( color / 2 ) + 1;\n        } while ( isOk () );\n    }\n    color = color < 1 ? 1 : color\n}\n\nvar color = computeColor ();\nswitch ( color ) {\n    case 0:\n    case 1:\n        code = 'low';\n        break;\n    case 2:\n        code = 'high';\n        break;\n    default:\n        code = undefined\n}\n"
    },
    "wrapping":{
        "variables":"never",
        "function parameters":"never",
        "function call arguments":"never",
        "chained function calls":"never",
        "wrap dot in chained function calls":true,
        "array initializer":"never",
        "array initializer items":"never",
        "for":"never",
        "for statement":"always",
        "if statement":"always",
        "while statement":"always",
        "do ... while statement":"always",
        "with statement":"always",
        "objects":"always",
        "object properties":"always",
        "binary operators":"never",
        "wrap after binary operators":false,
        "ternary operators":"never",
        "wrap after ternary operators":false,
        "example":"var engine = {\n    cylinders: 8,\n    power: \"22k\",\n    getDescription: function () {\n        with ( this )\n            if ( !disabled )\n                println ( 'Cylinders: ' + cylinders + ' with power: ' + power );\n            else\n                log ();\n    },\n    get parameter () {\n        return power;\n    }\n}\n\nvar colors = [ 0, 1, 2 ];\nlength = colors.length ();\n\nfunction computeColor ( limit ) {\n    try {\n        color = 0;\n        for (var a = -1; a < limit; a++)\n            color += Math.round ( Math.random () * 2 );\n    } catch ( error ) {\n        error.cause ().dump ();\n    } finally {\n        log ();\n    }\n    while ( color > 100 )\n        do\n            color = ( color / 2 ) + 1;\n        while ( isOk( ) );\n    color = color < 1 ? 1 : color\n}\n\nvar a, b, c, x = function () {\n    return \"yes\"\n}\n"
    }
}<code></pre>