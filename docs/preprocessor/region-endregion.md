---
title: "oblast, endregion – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs: C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c807e4c6c6850182e913b5a1bba394d33ad2cc3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="region-endregion"></a>region, endregion
**#pragma oblast** umožňují určit blok kódu, který můžete rozbalit nebo sbalit při použití [osnovy funkce](/visualstudio/ide/outlining) z editoru kódu sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### <a name="parameters"></a>Parametry  
 `comment`(volitelné)  
 Komentář, který se zobrazí v editoru kódu.  
  
 *název*(volitelné)  
 Název oblasti.  Tento název se zobrazí v editoru kódu.  
  
## <a name="remarks"></a>Poznámky  
 **endregion – #pragma** označuje konec **oblast #pragma** bloku.  
  
 A `#region` bloku musí být ukončena s **endregion – #pragma**.  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)