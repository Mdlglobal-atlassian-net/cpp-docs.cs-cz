---
title: high_property_prefixes – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ce21958dbb928a29debe21fb7cfaed4b9036141
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465095"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Specifické pro C++**  
  
Určuje alternativní předpony pro tři metody vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parametry  
*GetPrefix*  
Předpona se použije pro `propget` metody.  
  
*PutPrefix*  
Předpona se použije pro `propput` metody.  
  
*PutRefPrefix*  
Předpona se použije pro `propputref` metody.  
  
## <a name="remarks"></a>Poznámky  
 
Ve výchozím nastavení základní zpracování chyb `propget`, `propput`, a `propputref` metody jsou vystaveny členským funkcím pojmenovaným s předponami `Get`, `Put`, a `PutRef`v uvedeném pořadí.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)