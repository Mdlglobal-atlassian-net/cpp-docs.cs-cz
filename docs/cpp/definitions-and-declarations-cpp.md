---
title: Definice a deklarace (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 5d192234a2b3cd3d72bef15e11678ebc41ccede0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462885"
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C++)
**Specifické pro Microsoft** rozhraní knihovna DLL odkazuje na všechny položky (funkce a data), které je známo, že mají být exportovány nějakým programem v systému; to znamená, že všechny položky, které jsou deklarovány jako **dllimport** nebo **dllexport** . Všechny deklarace, které jsou součástí rozhraní DLL musí určovat buď **dllimport** nebo **dllexport** atribut. Nicméně, definice musí určovat pouze **dllexport** atribut. Následující definice funkce například vygeneruje chybu kompilátoru:

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

 Použití **dllexport** implicitně předpokládá definici, zatímco **dllimport** implicitně předpokládá deklaraci. Je nutné použít **extern** – klíčové slovo s **dllexport** k vynucení deklarace; v opačném případě se předpokládá definice. Následující příklady jsou tedy správné:

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)