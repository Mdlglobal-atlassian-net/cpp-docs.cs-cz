---
title: _variant_t – extraktory | Dokumentace Microsoftu
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
ms.openlocfilehash: c18605c7539636e3158bc1dd9fe3a47e1d3146d6
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465952"
---
# <a name="variantt-extractors"></a>_variant_t – extraktory
**Specifické pro Microsoft**  
  
 Extrahovat data z zapouzdřeného `VARIANT` objektu.  
  
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
 Extrahuje nezpracovaných dat z zapouzdřenému `VARIANT`. Pokud `VARIANT` ještě není správný typ. `VariantChangeType` slouží pokusu o převod, a je generována chyba, nebude úspěšná:  
  
-   **(krátký) – operátor** extrahuje **krátký** celočíselnou hodnotu.  
  
-   **– operátor (dlouhé)** extrahuje **dlouhé** celočíselnou hodnotu.  
  
-   **operátor float ()** extrahuje **float** číselnou hodnotu.  
  
-   **operátor double ()** extrahuje **double** celočíselnou hodnotu.  
  
-   **operátor CY ()** extrahuje `CY` objektu.  
  
-   **bool – operátor ()** extrahuje **bool** hodnotu.  
  
-   **operátor DECIMAL ()** extrahuje `DECIMAL` hodnotu.  
  
-   **– operátor (BYTE)** extrahuje `BYTE` hodnotu.  
  
-   **_bstr_t – operátor ()** extrahuje řetězce, který je zapouzdřena v `_bstr_t` objektu.  
  
-   **operátor IDispatch\*()** extrahuje ze zapouzdřený ukazatel dispinterface `VARIANT`. `AddRef` je volán na výsledný ukazatel, tak, aby byl vás volat `Release` ji uvolnit.  
  
-   **operátor IUnknown\*()** extrahuje ze zapouzdřeného ukazatele rozhraní modelu COM `VARIANT`. `AddRef` je volán na výsledný ukazatel, tak, aby byl vás volat `Release` ji uvolnit.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_variant_t – třída](../cpp/variant-t-class.md)