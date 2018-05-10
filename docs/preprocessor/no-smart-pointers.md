---
title: no_smart_pointers – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4503ab027589f54c5b5bce60dc405a570dcc59
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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