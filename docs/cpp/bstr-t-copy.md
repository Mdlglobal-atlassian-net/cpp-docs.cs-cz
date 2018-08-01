---
title: _bstr_t::copy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b7032d9344ec9375059d5584d080854ffe5c775
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405337"
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Specifické pro Microsoft**  
  
 Vytvoří kopii zapouzdřeného `BSTR`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BSTR copy( bool fCopy = true ) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *fCopy*  
 Při hodnotě TRUE se **kopírování** vrátí kopii obsaženého objektu `BSTR`, jinak **kopírování** vrátí skutečný objekt BSTR.  
  
## <a name="remarks"></a>Poznámky  
 Vrátí nově přidělenou kopii zapouzdřeného objektu `BSTR`.  
  
## <a name="example"></a>Příklad  
  
```cpp 
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)