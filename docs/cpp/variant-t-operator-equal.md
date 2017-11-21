---
title: _variant_t::Operator = | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t::operator=
dev_langs: C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57ada98b0171711ea93fa8639e7c6c7aa1d7060a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="varianttoperator-"></a>_variant_t::operator =
**Konkrétní Microsoft**  
  
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
  
-   **Operator = (***varSrc***)** přiřadí existující **VARIANT** k `_variant_t` objektu.      
  
-   **Operator = (***pVarSrc***)** přiřadí existující **VARIANT** k `_variant_t` objektu.      
  
-   **Operator = (***var_t_Src***)** přiřadí existující `_variant_t` do objektu `_variant_t` objektu.      
  
-   **Operator = (***sSrc***)** přiřadí **krátké** celočíselnou hodnotu a `_variant_t` objektu.      
  
-   **Operator = (**`lSrc`**)** přiřadí **dlouho** celočíselnou hodnotu a `_variant_t` objektu.      
  
-   **operátor = (***fltSrc***)** přiřadí **float** číselnou hodnotu `_variant_t` objektu.      
  
-   **operátor = (***dblSrc***)** přiřadí **dvojité** číselnou hodnotu `_variant_t` objektu.      
  
-   **Operator = (***cySrc***)** přiřadí **CY** do objektu `_variant_t` objektu.      
  
-   **Operator = (***bstrSrc***)** přiřadí `BSTR` do objektu `_variant_t` objektu.      
  
-   **operátor = (***wstrSrc***)** přiřadí řetězec kódování Unicode `_variant_t` objektu.      
  
-   **Operator = (**`strSrc`**)** přiřadí řetězec vícebajtové tak, aby `_variant_t` objektu.      
  
-   **Operator = (** `bSrc` **)** přiřadí `bool` hodnotu `_variant_t` objektu.    
  
-   **Operator = (***pDispSrc***)** přiřadí **VT_DISPATCH** do objektu `_variant_t` objektu.      
  
-   **Operator = (***pIUnknownSrc***)** přiřadí **VT_UNKNOWN** do objektu `_variant_t` objektu.      
  
-   **operátor = (***decSrc***)** přiřadí **DECIMAL** hodnotu `_variant_t` objektu.      
  
-   **Operator = (** `bSrc` **)** přiřadí **BAJTŮ** hodnotu `_variant_t` objektu.    
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)