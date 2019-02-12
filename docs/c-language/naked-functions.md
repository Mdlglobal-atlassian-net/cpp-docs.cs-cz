---
title: Holé funkce
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
ms.openlocfilehash: b752dd6fa378bc1275e8a7da90420aa2b8247e4e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152193"
---
# <a name="naked-functions"></a>Holé funkce

**Microsoft Specific**

Atribut třídy úložiště `naked` je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště `naked` generuje kompilátor kód bez kódu prologu a epilogu. Tuto funkci lze použít pro psaní vlastních sekvencí kódu epilogu nebo prologu pomocí vloženého kódu assembleru. Neviditelné funkce jsou zvláště užitečné při psaní ovladačů virtuálních zařízení.

Vzhledem k tomu, `naked` atribut platí pouze pro definici funkce a není modifikátorem typu, neviditelné funkce používají syntaxi rozšířeného atributu, je popsáno v [rozšířené atributy tříd úložiště](../c-language/c-extended-storage-class-attributes.md).

Následující příklad definuje funkci s atributem `naked`:

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

Nebo alternativně:

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

Atribut `naked` ovlivňuje pouze povahu generování kódu kompilátoru pro sekvence prologu a epilogu funkce. Neovlivňuje kód, který je generován pro volání těchto funkcí. Navíc atribut `naked` není považován za součást typu funkce a ukazatele funkce nemohou mít atribut `naked`. Kromě toho nelze atribut `naked` použít pro definici dat. Například následující kód vygeneruje chyby:

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

Atribut `naked` je relevantní pouze pro definici funkce a nemůže být zadán v prototypu funkce. Následující deklarace generuje chybu kompilátoru:

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
