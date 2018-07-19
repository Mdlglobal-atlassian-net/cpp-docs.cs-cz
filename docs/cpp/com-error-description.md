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
ms.openlocfilehash: 4be038bff05ce7a37b09ec3b3c61572635747864
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939894"
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
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)