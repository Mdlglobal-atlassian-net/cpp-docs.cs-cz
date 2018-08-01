---
title: _bstr_t::_bstr_t | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba2935dcec7863e43c0dd6a0a4e55ee5c4f3d28d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401643"
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t
**Specifické pro Microsoft**  
  
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
 *S1*  
 A `_bstr_t` objektů, které se mají zkopírovat.  
  
 *S2*  
 Vícebajtový řetězec.  
  
 *S3*  
 Řetězec s kódováním Unicode  
  
 *var*  
 A [_variant_t](../cpp/variant-t-class.md) objektu.  
  
 *BSTR*  
 Existující objekt `BSTR`.  
  
 *fCopy*  
 Pokud má hodnotu FALSE, *bstr* argument je připojen nový objekt bez vytvoření kopie voláním `SysAllocString`.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou popsány `_bstr_t` konstruktory.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`_bstr_t( )`|Vytvoří výchozí `_bstr_t` objekt, který zapouzdřuje hodnotu null `BSTR` objektu.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Vytvoří `_bstr_t` jako kopii jiného objektu.<br /><br /> Jde *bez podstruktury* kopie, která zvýší počet odkazů zapouzdřené proměnné `BSTR` místo vytvoření nového objektu.|  
|`_bstr_t( char*`  `s2`  `)`|Vytvoří `_bstr_t` objektu voláním `SysAllocString` k vytvoření nového `BSTR` objekt a potom zapouzdřuje.<br /><br /> Tento konstruktor provádí nejprve vícebajtovým formátem pro převod kódování Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Vytvoří `_bstr_t` objektu voláním `SysAllocString` k vytvoření nového `BSTR` objekt a potom zapouzdřuje.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Vytvoří `_bstr_t` objektu z `_variant_t` objekt prvním načtením `BSTR` objekt z zapouzdřeného objektu VARIANT.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Vytvoří `_bstr_t` objekt z existující `BSTR` (nikoli `wchar_t*` řetězec). Pokud *fCopy* má hodnotu false, zadané `BSTR` je připojen nový objekt bez provedení nová kopie `SysAllocString`.<br /><br /> Tento konstruktor používá funkce obálky v záhlaví typu knihovny k zapouzdření a převzít vlastnictví `BSTR` , která je vrácena metodou rozhraní.|  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)   
 [_variant_t – třída](../cpp/variant-t-class.md)