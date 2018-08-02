---
title: _variant_t – relační operátory | Dokumentace Microsoftu
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
ms.openlocfilehash: 32f9a45fcfaaff02cfb7cf765857957f20c41ba1
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463038"
---
# <a name="variantt-relational-operators"></a>_variant_t – relační operátory
**Specifické pro Microsoft**  
  
 Porovnat dva `_variant_t` objekty a zjistí rovnost či nerovnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool operator==(  
   const VARIANT& varSrc) const;  
bool operator==(  
   const VARIANT* pSrc) const;  
bool operator!=(  
   const VARIANT& varSrc) const;  
bool operator!=(  
   const VARIANT* pSrc) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A `VARIANT` která bude porovnána `_variant_t` objektu.  
  
 *pSrc*  
 Ukazatel `VARIANT` k porovnání s `_variant_t` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** pokud obsahuje porovnání **false** Pokud tomu tak není.  
  
## <a name="remarks"></a>Poznámky  
 Porovná `_variant_t` objektu `VARIANT`, testování a zjistí rovnost či nerovnost.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_variant_t – třída](../cpp/variant-t-class.md)