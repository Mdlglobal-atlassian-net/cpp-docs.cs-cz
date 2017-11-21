---
title: "raw_property_prefixes – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_property_prefixes
dev_langs: C++
helpviewer_keywords: raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aec8daa33e5fc734168bcb3096c4111536250c68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Konkrétní C++**  
  
 Určuje alternativní předpony pro tři metody vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `GetPrefix`  
 Předpona, která má být použit pro **propget –** metody.  
  
 `PutPrefix`  
 Předpona, která má být použit pro **propput –** metody.  
  
 `PutRefPrefix`  
 Předpona, která má být použit pro **propputref** metody.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, nízké úrovně **propget –**, **propput –**, a **propputref** metody jsou vystaveny členské funkce předpony z **get_**, **put_**, a **putref_** v uvedeném pořadí. Tyto předpony jsou kompatibilní s názvy používanými v souborech hlaviček generovaných jazykem MIDL.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)