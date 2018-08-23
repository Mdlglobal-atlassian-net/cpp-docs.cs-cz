---
title: inject_statement – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4142b742ae6c2a758c2a2fb5e09c604959433f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465751"
---
# <a name="injectstatement"></a>inject_statement
**Specifické pro C++**  
  
Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inject_statement("source_text")  
```  
  
### <a name="parameters"></a>Parametry  
*source_text*  
Zdrojový text, který má být vložen do souboru hlaviček knihovny typů.  
  
## <a name="remarks"></a>Poznámky  
 
Text je umístěn na začátek deklarace oboru názvů, který zaobaluje obsah knihovny typů v souboru hlaviček.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)