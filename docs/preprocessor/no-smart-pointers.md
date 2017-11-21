---
title: "no_smart_pointers – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_search_pointers
dev_langs: C++
helpviewer_keywords: no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0837a702eb54ac19ba1a034d4c899284aba6cb37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Konkrétní C++**  
  
 Potlačí vytvoření chytré ukazatele pro všechna rozhraní v knihovně typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení se při použití `#import`, získat deklaraci chytré ukazatele pro všechna rozhraní v knihovně typů. Tyto chytré ukazatele jsou typu [_com_ptr_t – třída](../cpp/com-ptr-t-class.md).  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)