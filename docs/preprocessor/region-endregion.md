---
title: oblast, endregion | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e360009eb9126604d4466daed2445c7dfc582d4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808066"
---
# <a name="region-endregion"></a>region, endregion

`#pragma region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [funkce osnovy](/visualstudio/ide/outlining) z editoru kódu sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>Parametry

*Komentář*<br/>
(Volitelné) Komentář, který se zobrazí v editoru kódu.

*Jméno*<br/>
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

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)