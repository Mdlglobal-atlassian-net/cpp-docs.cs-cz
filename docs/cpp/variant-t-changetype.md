---
title: _variant_t::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53fd73fc9606053dda6f8c143618373ad9bb7e4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Konkrétní Microsoft**  
  
 Typ se změní `_variant_t` objekt, který má uvedené **VARTYPE**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vartype`  
 **VARTYPE** pro tento `_variant_t` objektu.  
  
 `pSrc`  
 Ukazatel na objekt `_variant_t`, který má být převeden. Pokud je tato hodnota **NULL**, převod se provádí na místě.  
  
## <a name="remarks"></a>Poznámky  
 Převede tento – členská funkce `_variant_t` objektu do uvedené **VARTYPE**. Pokud `pSrc` je **NULL**, převod se se provádí na místě, jinak hodnota `_variant_t` objektu se zkopíruje z `pSrc` a následně převeden.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)