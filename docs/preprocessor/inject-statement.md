---
title: "inject_statement – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: inject_statement
dev_langs: C++
helpviewer_keywords: inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb3bd5c1456daad18d374e5befa6936a0535dd38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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