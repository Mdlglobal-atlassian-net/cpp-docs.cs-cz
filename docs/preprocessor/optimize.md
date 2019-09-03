---
title: optimize – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220512"
---
# <a name="optimize-pragma"></a>optimize – direktiva pragma

Určuje optimalizace na základě funkce.

## <a name="syntax"></a>Syntaxe

> **#pragma optimalizovat ("**  | [ *optimalizace-seznam* ] **",** {**vypnuto** } **)**

## <a name="remarks"></a>Poznámky

Direktiva pragma **optimize** musí být mimo funkci. Projeví se v první funkci definované po výskytu direktivy pragma. Argumenty **on** a **off** zapínají možnosti zadané v *seznamu optimalizace – seznam* zapnuto nebo vypnuto.

*Seznam optimalizace* může být nula nebo více parametrů uvedených v následující tabulce.

### <a name="parameters-of-the-optimize-pragma"></a>Parametry direktivy pragma optimize

| Parametr (y) | Typ optimalizace |
|--------------------|--------------------------|
| **g** | Povolit globální optimalizace. |
| **s** nebo **t** | Zadejte krátké nebo rychlé sekvence strojového kódu. |
| **y** | Vygeneruje ukazatele na snímky v zásobníku programu. |

Tyto parametry jsou stejná písmena, která jsou použita s možnostmi kompilátoru [/o](../build/reference/o-options-optimize-code.md) . Například následující direktiva pragma je ekvivalentní `/Os` možnosti kompilátoru:

```cpp
#pragma optimize( "s", on )
```

Použití direktivy pragma **optimize** s prázdným řetězcem ( **""** ) je zvláštní forma direktivy:

Použijete-li parametr **off** , dojde k vypnutí všech optimalizací, **g**, **s**, **t**a **y**.

Použijete-li parametr **on** , resetuje optimalizace na ty, které jste zadali pomocí možnosti kompilátoru [/o](../build/reference/o-options-optimize-code.md) .

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
