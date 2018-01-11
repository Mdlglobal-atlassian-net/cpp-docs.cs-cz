---
title: TLBID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tlbid
dev_langs: C++
helpviewer_keywords: tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 812b105fc02782b611b3f55061e448062dcd07c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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