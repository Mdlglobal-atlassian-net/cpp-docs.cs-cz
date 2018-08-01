---
title: _bstr_t::Attach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f69811b7b25a793d11ef6d53aaf0638c752a11
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408620"
---
# <a name="bstrtattach"></a>_bstr_t::Attach
**Specifické pro Microsoft**  
  
 Odkazy `_bstr_t` obálky `BSTR`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Attach(  
   BSTR s  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *s*  
 Proměnná `BSTR`, která má být přidružena nebo přiřazena k proměnné `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud byla proměnná `_bstr_t` dříve připojena k jiné proměnné `BSTR`, vyčistí proměnná `_bstr_t` prostředky proměnné `BSTR`, pokud žádné jiné proměnné `_bstr_t` nepoužívají proměnnou `BSTR`.  
  
## <a name="example"></a>Příklad  
 Zobrazit [_bstr_t::Assign](../cpp/bstr-t-assign.md) příklad použití **připojit**.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)