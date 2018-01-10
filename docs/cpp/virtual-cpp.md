---
title: "virtuální (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs: C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 041939197f18861d27d1f99708e27415de2b7787
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="virtual-c"></a>virtual (C++)
Klíčové slovo `virtual` deklaruje virtuální funkci nebo virtuální základní třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>Parametry  
 `type-specifiers`  
 Určuje návratový typ virtuální členské funkce.  
  
 `member-function-declarator`  
 Deklaruje členskou funkci.  
  
 `access-specifier`  
 Definuje úroveň přístupu k základní třídě, `public`, `protected` nebo `private`. Může se objevit před nebo za klíčovým slovem `virtual`.  
  
 `base-class-name`  
 Identifikuje dříve deklarovaný typ třídy.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [virtuální funkce](../cpp/virtual-functions.md) Další informace.  
  
 Viz také následující klíčová slova: [– třída](../cpp/class-cpp.md), [privátní](../cpp/private-cpp.md), [veřejné](../cpp/public-cpp.md), a [chráněné](../cpp/protected-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)