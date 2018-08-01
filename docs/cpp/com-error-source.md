---
title: _com_error::source | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f722d1c4e8fc3d534403c2d18713e64dc2069011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404896"
---
# <a name="comerrorsource"></a>_com_error::Source
**Specifické pro Microsoft**  
  
 Volání `IErrorInfo::GetSource` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t Source() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek `IErrorInfo::GetSource` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledná `BSTR` zapouzdřena v `_bstr_t` objektu. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Jakékoli neúspěchy při volání `IErrorInfo::GetSource` metoda se ignoruje.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)