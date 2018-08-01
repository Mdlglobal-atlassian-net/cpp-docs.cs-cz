---
title: _com_error::Description | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 848709fa6cbbbfb4166750f86540de2433a73023
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404025"
---
# <a name="comerrordescription"></a>_com_error::Description
**Specifické pro Microsoft**  
  
 Volání `IErrorInfo::GetDescription` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t Description( ) const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek `IErrorInfo::GetDescription` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledná `BSTR` zapouzdřena v `_bstr_t` objektu. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Volání `IErrorInfo::GetDescription` funkce a načte `IErrorInfo` zaznamenaný v `_com_error` objektu. Jakékoli neúspěchy při volání `IErrorInfo::GetDescription` metoda se ignoruje.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)