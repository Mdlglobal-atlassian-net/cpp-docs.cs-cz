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
ms.openlocfilehash: 6f188cd833551542e636e764e76784635ae2ccf2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422763"
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
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)