---
title: _bstr_t::Operator += + | Dokumentace Microsoftu
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
ms.openlocfilehash: aad73939b8fd011fd6e1c9bf16f8dfe6eb303ff3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405740"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Specifické pro Microsoft**  
  
 Připojí znaky na konec objektu `_bstr_t` objektu nebo spojuje dva řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t& operator+=( const _bstr_t& s1 );  
_bstr_t operator+( const _bstr_t& s1 );  
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);  
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` objektu.  
  
 *S2*  
 Vícebajtový řetězec.  
  
 *S3*  
 Řetězec znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Tyto operátory provádějí zřetězení řetězců:  
  
-   **+= – operátor (***s1***)** připojí znaky v zapouzdřeného `BSTR` z *s1* na konec tohoto objektu zapouzdřený `BSTR`.  
  
-   **Operator + (***s1***)** vrátí nový `_bstr_t` zřetězením tento objekt, který je vytvořen `BSTR` se specifikací *s1*.  
  
-   **Operator + (***s2***&#124;***s1***)** vrátí nový `_bstr_t` , který je vytvořený zřetězením vícebajtový řetězec *s2*, převedeno na kódování Unicode, se `BSTR` zapouzdřena v *s1*.          
  
-   **Operator + (***s3* **,***s1***)** vrátí nový `_bstr_t` , který je vytvořen pomocí zřetězení řetězců kódování Unicode *s3* s `BSTR` zapouzdřena v *s1*.        
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)