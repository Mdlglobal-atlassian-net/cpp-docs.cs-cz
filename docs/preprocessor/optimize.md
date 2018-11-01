---
title: optimize
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 65948f2b466bdd40bd753dbba99e2e235c57b0f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615862"
---
# <a name="optimize"></a>optimize

Určuje optimalizace, které provádí na základě funkce funkce.

## <a name="syntax"></a>Syntaxe

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>Poznámky

**Optimalizovat** – Direktiva pragma musí být uvedena mimo funkci a na první funkci definovanou po viděli direktivy pragma se projeví. *Na* a *vypnout* argumenty zapnutí možnosti zadané v *seznamu optimalizací* zapnutí nebo vypnutí.

*Seznamu optimalizací* může být nula nebo více parametrů je znázorněno v následující tabulce.

### <a name="parameters-of-the-optimize-pragma"></a>Parametry optimize – direktiva Pragma

|Parametry|Typ optimalizace|
|--------------------|--------------------------|
|*g*|Povolte globální optimalizace.|
|*s* nebo *t*|Zadejte krátký nebo rychlý sekvence strojového kódu.|
|*y*|Generovat ukazatelů rámců v zásobníku programu.|

Toto jsou stejná písmena použít s [/O](../build/reference/o-options-optimize-code.md) – možnosti kompilátoru. Například následující direktivu pragma je ekvivalentní `/Os` – možnost kompilátoru:

```
#pragma optimize( "ts", on )
```

Použití **optimalizovat** – Direktiva pragma se prázdný řetězec (**""**) je zvláštní forma direktivy:

Při použití *vypnout* parametr, ukazuje všechny optimalizace *g*, *s*, *t*, a *y*, vypnuto.

Při použití *na* parametr resetuje optimalizace na ty, které jste zadali pomocí [/O](../build/reference/o-options-optimize-code.md) – možnost kompilátoru.

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)