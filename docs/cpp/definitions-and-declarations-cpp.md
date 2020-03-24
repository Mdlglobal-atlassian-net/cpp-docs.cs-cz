---
title: Definice a deklarace (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 20683f3d2e12f7ffead573cbac46fdd4e106c383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189374"
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C++)

**Specifické pro společnost Microsoft**

Rozhraní DLL odkazuje na všechny položky (funkce a data), u kterých je známo, že jsou exportovány některým z programů v systému. To znamená, že všechny položky, které jsou deklarovány jako **dllimport** nebo **dllexport**. Všechny deklarace zahrnuté v rozhraní knihovny DLL musí určovat atribut **dllimport** nebo **dllexport** . Definice však musí určovat pouze atribut **dllexport** . Následující definice funkce například vygeneruje chybu kompilátoru:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

Tento kód také vygeneruje chybu:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

Tato syntaxe je však správná:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

Použití **dllexport** implikuje definici, zatímco **dllimport** implikuje deklaraci. Chcete-li vynutit deklaraci deklarace, je nutné použít klíčové slovo **extern** s objektem **dllexport** . v opačném případě je odvozena definice. Následující příklady jsou tedy správné:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

Následující příklady objasňují předchozí:

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
