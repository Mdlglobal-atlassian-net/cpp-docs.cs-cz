---
title: Definice a deklarace (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 8723c3f09a5e9a8eecf0e552c9f5a7fd9b7f6c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234355"
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C)

**Specifické pro Microsoft**

Rozhraní DLL odkazuje na všechny položky (funkce a data), u kterých je známo, že jsou exportovány některým z programů v systému. To znamená, že všechny položky, které jsou **dllimport** deklarovány `dllexport`jako dllimport nebo. Všechny deklarace zahrnuté v rozhraní knihovny DLL musí určovat buď **dllimport** atribut dllimport `dllexport` , nebo. Definice však může specifikovat pouze `dllexport` atribut. Následující definice funkce například vygeneruje chybu kompilátoru:

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

Použití `dllexport` implikuje definici, zatímco **dllimport** implikuje deklaraci. Klíčové slovo `extern` je nutné použít spolu s atributem `dllexport` k vynucení deklarace. V opačném případě se předpokládá definice.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)
