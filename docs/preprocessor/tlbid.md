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
ms.openlocfilehash: f5bd922089bcf189c403a97679a593a985603a12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446254"
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
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)