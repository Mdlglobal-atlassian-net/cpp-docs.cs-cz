---
title: region, endregion – direktivy pragma
ms.date: 08/29/2019
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
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222377"
---
# <a name="region-endregion-pragmas"></a>region, endregion – direktivy pragma

`#pragma region`umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití [funkce sbalení](/visualstudio/ide/outlining) editoru Visual Studio Code.

## <a name="syntax"></a>Syntaxe

> **oblast #pragma** *název*\
> **#pragma endregion** *Komentář*

### <a name="parameters"></a>Parametry

*vytvořena*\
Volitelné Komentář, který se má zobrazit v editoru kódu

*Jméno*\
Volitelné Název oblasti Tento název se zobrazí v editoru kódu.

## <a name="remarks"></a>Poznámky

`#pragma endregion`označuje konec `#pragma region` bloku.

Blok musí končit `#pragma endregion`direktivou. `#region`

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
