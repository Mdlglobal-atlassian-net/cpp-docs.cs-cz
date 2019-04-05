---
title: region, endregion
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: c73a90aa2be83d643b74dde4645081e89da3ff73
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037923"
---
# <a name="region-endregion"></a>region, endregion

`#pragma region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [funkce osnovy](/visualstudio/ide/outlining) z editoru kódu sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>Parametry

*comment*<br/>
(Volitelné) Komentář, který se zobrazí v editoru kódu.

*name*<br/>
(Volitelné) Název oblasti.  Tento název se zobrazí v editoru kódu.

## <a name="remarks"></a>Poznámky

`#pragma endregion` označuje konec `#pragma region` bloku.

A `#region` bloku musí být ukončen direktivou `#pragma endregion`.

## <a name="example"></a>Příklad

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)