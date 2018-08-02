---
title: _variant_t::detach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 895df401ab10ae85641fd2eed9f7a9654916f33f
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465223"
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Specifické pro Microsoft**  
  
 Odpojí zapouzdřeného `VARIANT` objektu z tohoto `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VARIANT Detach( );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Zapouzdřený objekt `VARIANT`.  
  
## <a name="remarks"></a>Poznámky  
 Extrahuje a vrátí zapouzdřený objekt `VARIANT`, následně smaže `_variant_t` objekt bez došlo k jeho zničení. Tato členská funkce odebere `VARIANT` ze zapouzdření a nastaví `VARTYPE` tohoto `_variant_t` objekt VT_EMPTY. Je na vás, abyste uvolnili vrácený `VARIANT` voláním [VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835) funkce.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_variant_t – třída](../cpp/variant-t-class.md)