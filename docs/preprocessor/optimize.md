---
title: Optimalizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98275f6e0a16c6d07b66ce592eb12b9391157653
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069734"
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