---
title: _variant_t::SetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t::SetString
dev_langs: C++
helpviewer_keywords: SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc0fd027bbb4a1049e46351a8a544dac8c5a47aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Konkrétní Microsoft**  
  
 To přiřadí řetězec `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void SetString(  
   const char* pSrc   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSrc`  
 Ukazatel na řetězec znaků.  
  
## <a name="remarks"></a>Poznámky  
 Převede řetězec znaků standardu ANSI na řetězec `BSTR` znakové sady Unicode a přiřadí jej tomuto objektu `_variant_t`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)