---
title: "high_property_prefixes – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7df4ef6cded98c19ead86160aa772e349ebfd37
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Konkrétní C++**  
  
 Určuje alternativní předpony pro tři metody vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `GetPrefix`  
 Předpona, která má být použit pro **propget –** metody.  
  
 `PutPrefix`  
 Předpona, která má být použit pro **propput –** metody.  
  
 `PutRefPrefix`  
 Předpona, která má být použit pro **propputref** metody.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení souhrnné zpracování chyb **propget –**, **propput –**, a **propputref** metody jsou vystaveny členské funkce předpony **získat** , `Put`, a **typu PutRef**, v uvedeném pořadí.  
  
 Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)