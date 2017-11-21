---
title: _bstr_t::Operator += + | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs: C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 503f021a9ef0f798af8d82f33dac84d3eb0ccc51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Konkrétní Microsoft**  
  
 Přidá konec znaků `_bstr_t` objektu nebo řetězí dva řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` objektu.  
  
 *s2*  
 Více-bajtové řetězec.  
  
 `s3`  
 Řetězec znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Proveďte tyto operátory zřetězení řetězců:  
  
-   **+= – operátor (***s1***)** připojí znakům zapouzdřené `BSTR` z *s1* na konec tohoto objektu zapouzdřené `BSTR`.      
  
-   **operátor + (***s1***)** vrátí nové `_bstr_t` která je tvořena zřetězením tento objekt `BSTR` s třídou *s1*.      
  
-   **operátor + (***s2***&#124;** *s1***)** vrátí novou `_bstr_t` která je tvořena zřetězením vícebajtové řetězec *s2*, převést na kódování Unicode s `BSTR` zapouzdřené v *s1*.          
  
-   **operátor + (** `s3` **,***s1***)** vrátí novou `_bstr_t` která je tvořena zřetězením řetězec znaků Unicode `s3` pomocí `BSTR` zapouzdřené v *s1*.        
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)