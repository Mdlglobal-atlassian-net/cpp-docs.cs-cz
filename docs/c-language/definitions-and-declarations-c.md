---
title: Definice a deklarace (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 1ec42f17d22b24aac3d19a3b129babe723930ae7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620230"
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