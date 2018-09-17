---
title: oblast, endregion | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: dac2df26f393b7491d94abdb6d987a8e424723e1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715553"
---
# <a name="region-endregion"></a>region, endregion
`#pragma region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [funkce osnovy](/visualstudio/ide/outlining) z editoru kódu sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>Parametry  
*Komentář*  
(Volitelné) Komentář, který se zobrazí v editoru kódu.  
  
*Jméno*  
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