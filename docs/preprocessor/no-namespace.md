---
title: "no_namespace – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_namespace
dev_langs: C++
helpviewer_keywords: no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b83e60aca7ea0e39ba67834ad1def0896dcdc07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nonamespace"></a>no_namespace
**Konkrétní C++**  
  
 Určuje, že název oboru názvů není generované kompilátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Poznámky  
 Knihovny typů obsah v `#import` soubor hlaviček jsou obvykle definovány v oboru názvů. Název oboru názvů je zadán v **knihovny** prohlášení o původní soubor IDL. Pokud `no_namespace` zadaný atribut, bude tento obor názvů není generované kompilátorem.  
  
 Pokud chcete použít jiný obor názvů název, použijte [rename_namespace –](../preprocessor/rename-namespace.md) atribut místo.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)