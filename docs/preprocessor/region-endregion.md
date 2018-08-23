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
ms.openlocfilehash: 9e6ec22be873dcec06f224913eb905a2779e4efd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465384"
---
# <a name="region-endregion"></a>region, endregion
`#pragma region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [funkce osnovy](/visualstudio/ide/outlining) z editoru kódu sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>Parametry  
*Komentář* (volitelné)  
Komentář, který se zobrazí v editoru kódu.  
  
*Název* (volitelné)  
Název oblasti.  Tento název se zobrazí v editoru kódu.  
  
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