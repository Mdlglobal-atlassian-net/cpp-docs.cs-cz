---
title: _variant_t::SetString | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ef72cfd256a2676c73223723f37374c50cb56f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947618"
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Specifické pro Microsoft**  
  
 Přiřadí řetězec tomuto `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void SetString(const char* pSrc);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pSrc*  
 Ukazatel na řetězec znaků.  
  
## <a name="remarks"></a>Poznámky  
 Převede řetězec znaků standardu ANSI na řetězec `BSTR` znakové sady Unicode a přiřadí jej tomuto objektu `_variant_t`.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)