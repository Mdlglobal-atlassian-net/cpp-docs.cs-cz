---
title: Definice a deklarace (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628940"
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C++)

**Specifické pro Microsoft**

Rozhraní DLL odkazuje na všechny položky (funkce a data), které jsou známé být exportovány nějakým programem v systému. To znamená, že všechny položky, které jsou deklarovány jako **dllimport** nebo **dllexport**. Všechny deklarace, které jsou součástí rozhraní DLL musí určovat buď **dllimport** nebo **dllexport** atribut. Nicméně, definice musí určovat pouze **dllexport** atribut. Následující definice funkce například vygeneruje chybu kompilátoru:

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