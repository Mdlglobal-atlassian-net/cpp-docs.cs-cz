---
title: _variant_t – relační operátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 663d8e24af8362de8ea809bc37a68c33d3278bc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="variantt-relational-operators"></a>_variant_t – relační operátory
**Konkrétní Microsoft**  
  
 Porovnat `_variant_t` objekty pro rovnosti nebo nerovnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** být porovnána s `_variant_t` objektu.  
  
 `pSrc`  
 Ukazatel **VARIANT** být porovnána s `_variant_t` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** pokud obsahuje porovnání, **false** není-li.  
  
## <a name="remarks"></a>Poznámky  
 Porovná `_variant_t` objektu s **VARIANT**, testování rovnosti nebo nerovnosti.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)