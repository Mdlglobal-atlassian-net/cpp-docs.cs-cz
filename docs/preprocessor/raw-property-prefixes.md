---
title: raw_property_prefixes – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 423a66b698f4e421ff29e6ac3dfddd11fa11c58f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466302"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Specifické pro C++**  
  
Určuje alternativní předpony pro tři metody vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parametry  
*GetPrefix*  
Předpona se použije pro `propget` metody.  
  
*PutPrefix*  
Předpona se použije pro `propput` metody.  
  
*PutRefPrefix*  
Předpona se použije pro `propputref` metody.  
  
## <a name="remarks"></a>Poznámky  
 
Ve výchozím nastavení, nízké úrovně `propget`, `propput`, a `propputref` metody jsou vystaveny členským funkcím pojmenovaným s **get_**, **put_**, a **putref_** v uvedeném pořadí. Tyto předpony jsou kompatibilní s názvy používanými v souborech hlaviček generovaných jazykem MIDL.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)