---
title: _variant_t::Operator = | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4772c62db1443beaf6a5fff962a52a71823674bc
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947669"
---
# <a name="varianttoperator-"></a>_variant_t::operator =
**Specifické pro Microsoft**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
_variant_t& operator=(  
   const VARIANT& varSrc   
);  
  
_variant_t& operator=(  
   const VARIANT* pVarSrc   
);  
  
_variant_t& operator=(  
   const _variant_t& var_t_Src   
);  
  
_variant_t& operator=(  
   short sSrc   
);  
  
_variant_t& operator=(  
   long lSrc   
);  
  
_variant_t& operator=(  
   float fltSrc   
);  
  
_variant_t& operator=(  
   double dblSrc   
);  
  
_variant_t& operator=(  
   const CY& cySrc   
);  
  
_variant_t& operator=(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t& operator=(  
   const wchar_t* wstrSrc   
);  
  
_variant_t& operator=(  
   const char* strSrc   
);  
  
_variant_t& operator=(  
   IDispatch* pDispSrc   
);  
  
_variant_t& operator=(  
   bool bSrc   
);  
  
_variant_t& operator=(  
   IUnknown* pSrc   
);  
  
_variant_t& operator=(  
   const DECIMAL& decSrc   
);  
  
_variant_t& operator=(  
   BYTE bSrc   
);  
  
_variant_t& operator=(  
   char cSrc  
);  
  
_variant_t& operator=(  
   unsigned short usSrc  
);  
  
_variant_t& operator=(  
   unsigned long ulSrc  
);  
  
_variant_t& operator=(  
   int iSrc  
);  
  
_variant_t& operator=(  
   unsigned int uiSrc  
);  
  
_variant_t& operator=(  
   __int64 i8Src  
);  
  
_variant_t& operator=(  
   unsigned __int64 ui8Src  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátor přiřadí novou hodnotu objektu `_variant_t`:  
  
-   **Operator = (***varSrc***)** přiřadí existující `VARIANT` k `_variant_t` objektu.      
  
-   **Operator = (***pVarSrc***)** přiřadí existující `VARIANT` k `_variant_t` objektu.      
  
-   **Operator = (***var_t_Src***)** přiřadí existující `_variant_t` do objektu `_variant_t` objektu.      
  
-   **operátor = (***sSrc***)** přiřadí **krátký** celočíselnou hodnotu `_variant_t` objektu.      
  
-   **operátor = (**`lSrc`**)** přiřadí **dlouhé** celočíselnou hodnotu `_variant_t` objektu.      
  
-   **operátor = (***fltSrc***)** přiřadí **float** číselnou hodnotu `_variant_t` objektu.      
  
-   **operátor = (***dblSrc***)** přiřadí **double** číselnou hodnotu `_variant_t` objektu.      
  
-   **operátor = (***cySrc***)** přiřadí `CY` do objektu `_variant_t` objektu.      
  
-   **operátor = (***bstrSrc***)** přiřadí `BSTR` do objektu `_variant_t` objektu.      
  
-   **Operator = (***wstrSrc***)** přiřadí řetězec znakové sady Unicode `_variant_t` objektu.      
  
-   **Operator = (**`strSrc`**)** přiřadí vícebajtový řetězec `_variant_t` objektu.      
  
-   **Operator = (** `bSrc` **)** přiřadí **bool** hodnota, která se `_variant_t` objektu.    
  
-   **operátor = (***pDispSrc***)** přiřadí `VT_DISPATCH` do objektu `_variant_t` objektu.      
  
-   **operátor = (***pIUnknownSrc***)** přiřadí `VT_UNKNOWN` do objektu `_variant_t` objektu.      
  
-   **Operator = (***decSrc***)** přiřadí `DECIMAL` hodnota, která se `_variant_t` objektu.      
  
-   **Operator = (** `bSrc` **)** přiřadí `BYTE` hodnota, která se `_variant_t` objektu.    
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)