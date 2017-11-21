---
title: _variant_t::detach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs: C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 014de597ffbc9a7004f821393902ffe05ac1f278
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Konkrétní Microsoft**  
  
 Umožňuje odpojit zapouzdřené **VARIANT** objekt z tohoto `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Zapouzdřené **VARIANT**.  
  
## <a name="remarks"></a>Poznámky  
 Extrahuje a vrátí zapouzdřené **VARIANT**, pak tato vymaže `_variant_t` objektu bez zničení ho. Tato funkce člen odebere **VARIANT** z zapouzdření a nastaví **VARTYPE** tohoto `_variant_t` do objektu `VT_EMPTY`. Je na vás k uvolnění vrácený **VARIANT** voláním [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835) funkce.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)