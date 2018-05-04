---
title: Definice a deklarace (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 742270c77d47c178d0254ca9b9882f73fe3b8293
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C++)
## <a name="microsoft-specific"></a>Specifické pro Microsoft
 Odkazuje na knihovnu DLL rozhraní pro všechny položky (funkce a data), které jsou známé exportovat některé programem v systému. To znamená, všechny položky, které jsou deklarované jako `dllimport` nebo `dllexport`. Všechny deklarace, které jsou součástí rozhraní knihovny DLL musí být buď `dllimport` nebo `dllexport` atribut. Definice však musí určovat pouze atribut `dllexport`. Následující definice funkce například vygeneruje chybu kompilátoru:

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

 Použití `dllexport` znamená definici, zatímco `dllimport` znamená deklaraci. Klíčové slovo `extern` je nutné použít spolu s atributem `dllexport` k vynucení deklarace. V opačném případě se předpokládá definice. Následující příklady jsou tedy správné:

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

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)
