---
title: no_dual_interfaces – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1e919e48b79c9fe98a7a33257ebd0f70061d788
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465565"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Specifické pro C++**  
  
Změny způsobu, jakým kompilátor generuje funkce obálky pro duální rozhraní metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Poznámky  
 
Za normálních okolností se obálky volání metody prostřednictvím tabulku virtuálních funkcí pro rozhraní. S **no_dual_interfaces –**, místo volání obálky `IDispatch::Invoke` k vyvolání metody.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)