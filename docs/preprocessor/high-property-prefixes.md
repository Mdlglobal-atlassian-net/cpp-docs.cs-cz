---
title: "high_property_prefixes – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: high_property_prefixes
dev_langs: C++
helpviewer_keywords: high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed37cdc51c5e08899786ce82a9c3e5e3224f9f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)