---
title: _bstr_t::Operator = | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::operator=
dev_langs: C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed1de7a529d8c4c1b0d7ae8623d0f1c4a58b5075
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Konkrétní Microsoft**  
  
 Přiřadí novou hodnotu na stávající `_bstr_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` objekt, který chcete přiřadit k existující `_bstr_t` objektu.  
  
 *s2*  
 Více-bajtové řetězec k přiřazení ke stávající `_bstr_t` objektu.  
  
 `s3`  
 Řetězec znaků Unicode k přiřazení ke stávající `_bstr_t` objektu.  
  
 `var`  
 A `_variant_t` objekt, který chcete přiřadit k existující `_bstr_t` objektu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="example"></a>Příklad  
 V tématu [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití `operator=`.  
  
## <a name="see-also"></a>Viz také  
 [_bstr_t – třída](../cpp/bstr-t-class.md)