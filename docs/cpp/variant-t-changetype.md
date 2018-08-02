---
title: _variant_t::ChangeType | Dokumentace Microsoftu
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
ms.openlocfilehash: 5f3790f4cb357ed830ba2c61b3c2906356dc64da
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465585"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Specifické pro Microsoft**  
  
 Typ se změní `_variant_t` objekt označený `VARTYPE`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *VarType*  
 `VARTYPE` To `_variant_t` objektu.  
  
 *pSrc*  
 Ukazatel na objekt `_variant_t`, který má být převeden. Pokud je tato hodnota NULL, převod se provádí na místě.  
  
## <a name="remarks"></a>Poznámky  
 Tato členská funkce převede `_variant_t` na zadaný objekt `VARTYPE`. Pokud *pSrc* má hodnotu NULL, převod se provede na místě, jinak to `_variant_t` objekt zkopírován z *pSrc* a poté převeden.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_variant_t – třída](../cpp/variant-t-class.md)