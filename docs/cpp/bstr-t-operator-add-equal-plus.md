---
title: _bstr_t::Operator += + | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e443b233e19f6cdc64d7d6021a9a9c078a4f327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
  
 *S2*  
 Více-bajtové řetězec.  
  
 `s3`  
 Řetězec znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Proveďte tyto operátory zřetězení řetězců:  
  
-   **+= – operátor (***s1***)** připojí znakům zapouzdřené `BSTR` z *s1* na konec tohoto objektu zapouzdřené `BSTR`.      
  
-   **operátor + (***s1***)** vrátí nové `_bstr_t` která je tvořena zřetězením tento objekt `BSTR` s třídou *s1*.      
  
-   **operátor + (***s2***&#124;***s1***)** vrátí novou `_bstr_t` která je tvořena zřetězením více-bajtové řetězec *s2*, převést na kódování Unicode s `BSTR` zapouzdřené v *s1*.          
  
-   **operátor + (** `s3` **,***s1***)** vrátí novou `_bstr_t` která je tvořena zřetězením řetězec znaků Unicode `s3` s `BSTR` zapouzdřené v *s1*.        
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)