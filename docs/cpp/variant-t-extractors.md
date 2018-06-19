---
title: _variant_t – extraktory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
dev_langs:
- C++
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65049a473f62e728fcb4d74b581a08c0f1723fc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423315"
---
# <a name="variantt-extractors"></a>_variant_t – extraktory
**Konkrétní Microsoft**  
  
 Extrahovat data z zapouzdřené **VARIANT** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator short( ) const;   
operator long( ) const;   
operator float( ) const;   
operator double( ) const;   
operator CY( ) const;   
operator _bstr_t( ) const;   
operator IDispatch*( ) const;   
operator bool( ) const;   
operator IUnknown*( ) const;   
operator DECIMAL( ) const;   
operator BYTE( ) const;  
operator VARIANT() const throw();  
operator char() const;  
operator unsigned short() const;  
operator unsigned long() const;  
operator int() const;  
operator unsigned int() const;  
operator __int64() const;  
operator unsigned __int64() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Extrahuje nezpracovaná data z zapouzdřené **VARIANT**. Pokud **VARIANT** již není správný typ **VariantChangeType** se používá k pokusu o převod, a je generována chyba při selhání:  
  
-   **krátký () operátor** extrahuje **krátké** celočíselnou hodnotu.  
  
-   **operátor dlouho ()** extrahuje **dlouho** celočíselnou hodnotu.  
  
-   **operátor float ()** extrahuje **float** číselnou hodnotu.  
  
-   **operátor double ()** extrahuje **dvojité** celočíselnou hodnotu.  
  
-   **operátor CY ()** extrahuje **CY** objektu.  
  
-   **operátor bool ()** extrahuje `bool` hodnotu.  
  
-   **operátor DECIMAL ()** extrahuje **DECIMAL** hodnotu.  
  
-   **operátor (BAJTŮ)** extrahuje **BAJTŮ** hodnotu.  
  
-   **operátor _bstr_t ()** extrahuje řetězec, který je zapouzdřený v `_bstr_t` objektu.  
  
-   **operátor IDispatch\*()** extrahuje dispinterface ukazatel z zapouzdřené **VARIANT**. `AddRef` je volána na výsledný ukazatel tak, aby byl až abyste mohli volat **verze** ji uvolnit.  
  
-   **operátor IUnknown\*()** extrahuje ukazatele rozhraní modelu COM z zapouzdřené **VARIANT**. `AddRef` je volána na výsledný ukazatel tak, aby byl až abyste mohli volat **verze** ji uvolnit.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)
