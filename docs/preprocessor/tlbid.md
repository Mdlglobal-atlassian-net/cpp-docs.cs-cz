---
title: TLBID | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ec0150e63209728cf2f02c854fe03702b8a45b4
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466096"
---
# <a name="tlbid"></a>tlbid
**Specifické pro C++**  
  
Umožňuje načítání knihoven jiné než primární typ knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>Parametry  
*Číslo*  
Počet knihovnu typů v `filename`.  
  
## <a name="remarks"></a>Poznámky  
 
Pokud více knihoven typů jsou součástí jedné knihovny DLL, je možné načítat knihovny jiné než primární typ knihovny pomocí **tlbid**.  
  
Příklad:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
je ekvivalentní:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)