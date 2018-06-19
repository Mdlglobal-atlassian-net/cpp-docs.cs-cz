---
title: TLBID | Microsoft Docs
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
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839865"
---
# <a name="tlbid"></a>tlbid
**Konkrétní C++**  
  
 Umožňuje načítání knihoven než knihovny primární typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>Parametry  
 `number`  
 Počet knihovny typů v `filename`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud více knihovny typů jsou součástí jednoho knihovny DLL, možné načítat knihovny než knihovny primární typů pomocí `tlbid`.  
  
 Příklad:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 je ekvivalentní:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)