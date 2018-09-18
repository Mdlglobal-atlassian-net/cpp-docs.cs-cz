---
title: Definice a Declarations (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae97ecc055ed7e6a448f2f820e762cafb2c5798
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028672"
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C)

**Specifické pro Microsoft**

Rozhraní DLL odkazuje na všechny položky (funkce a data), které jsou známé být exportovány nějakým programem v systému. To znamená, že všechny položky, které jsou deklarovány jako **dllimport** nebo `dllexport`. Všechny deklarace, které jsou součástí rozhraní DLL musí určovat buď **dllimport** nebo `dllexport` atribut. Však můžete pouze zadat definici `dllexport` atribut. Následující definice funkce například vygeneruje chybu kompilátoru:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Tento kód také vygeneruje chybu:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Tato syntaxe je však správná:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

Použití `dllexport` implicitně předpokládá definici, zatímco **dllimport** implicitně předpokládá deklaraci. Klíčové slovo `extern` je nutné použít spolu s atributem `dllexport` k vynucení deklarace. V opačném případě se předpokládá definice.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)