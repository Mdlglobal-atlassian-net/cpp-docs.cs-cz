---
title: _com_error::HelpContext | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e800bd3100fa0199534f3e9bdf6646aa0ffc6860
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940895"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Specifické pro Microsoft**  
  
 Volání `IErrorInfo::GetHelpContext` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek `IErrorInfo::GetHelpContext` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Pokud ne `IErrorInfo` objekt zaznamenán, vrátí nulu.  
  
## <a name="remarks"></a>Poznámky  
 Jakékoli neúspěchy při volání `IErrorInfo::GetHelpContext` metoda se ignoruje.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)