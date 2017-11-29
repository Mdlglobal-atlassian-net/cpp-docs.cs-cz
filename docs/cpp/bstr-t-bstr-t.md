---
title: _bstr_t::_bstr_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::_bstr_t
dev_langs: C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 05b157866295bb682ec64f908e5f67b0b7ae505c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t
**Konkrétní Microsoft**  
  
 Vytvoří `_bstr_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `s1`  
 A `_bstr_t` objekt, který se má zkopírovat.  
  
 `s2`  
 Více-bajtové řetězec.  
  
 `s3`  
 Řetězec znaků Unicode  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md) objektu.  
  
 `bstr`  
 Existující objekt `BSTR`.  
  
 `fCopy`  
 Pokud `false`, `bstr` argument je připojen k nového objektu bez vytvoření kopie voláním `SysAllocString`.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou popsány `_bstr_t` konstruktory.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`_bstr_t( )`|Vytvoří výchozí `_bstr_t` objekt, který zapouzdřuje hodnotu null `BSTR` objektu.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Vytvoří `_bstr_t` jako kopii jiného objektu.<br /><br /> Toto je *bez podstruktury* kopie, které zvýší počet odkazů obsah zapouzdřeného `BSTR` místo vytvoření nového objektu.|  
|`_bstr_t( char*`  `s2`  `)`|Vytvoří `_bstr_t` objekt voláním `SysAllocString` pro vytvoření nového `BSTR` objektu a zapouzdří jej.<br /><br /> Tento konstruktor nejprve provádí vícebajtových k převodu znakové sady Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Vytvoří `_bstr_t` objekt voláním `SysAllocString` pro vytvoření nového `BSTR` objektu a zapouzdří jej.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Vytvoří `_bstr_t` objektu z `_variant_t` objekt první načtením `BSTR` objekt z zapouzdřené objektu typu VARIANT.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Vytvoří `_bstr_t` objekt z existující `BSTR` (Naproti tomu `wchar_t*` řetězec). Pokud `fCopy` je nastavena hodnota false, zadaných `BSTR` je připojen k nového objektu bez vytvoření nové kopie s `SysAllocString`.<br /><br /> Tento konstruktor je používaná obálku funkce v hlavičkách knihovny typ k zapouzdření a převzít vlastnictví `BSTR` , je vrácen rutinou metodu rozhraní.|  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)   
 [_variant_t – třída](../cpp/variant-t-class.md)