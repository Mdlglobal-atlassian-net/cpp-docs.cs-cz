---
title: _com_error::HelpFile | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3afcda41d5dc4ad3cc1fd74ed5449d574946f1e5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402039"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Specifické pro Microsoft**  
  
 Volání `IErrorInfo::GetHelpFile` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t HelpFile() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek `IErrorInfo::GetHelpFile` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledný BSTR je zapouzdřen v objektu `_bstr_t`. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Jakékoli neúspěchy při volání `IErrorInfo::GetHelpFile` metoda se ignoruje.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)