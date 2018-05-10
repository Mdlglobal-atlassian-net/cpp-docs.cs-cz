---
title: inject_statement – | Microsoft Docs
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
ms.openlocfilehash: 115f5b3d7012ae3e9073d81e0c1005dcb513e045
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="injectstatement"></a>inject_statement
**Konkrétní C++**  
  
 Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>Parametry  
 `source_text`  
 Zdrojový text, který má být vložen do souboru hlaviček knihovny typů.  
  
## <a name="remarks"></a>Poznámky  
 Text je umístěn na začátek deklarace oboru názvů, který zaobaluje obsah knihovny typů v souboru hlaviček.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)