---
title: _com_error::GUID | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c592607732eb5558ce74edb7b71adbc023b2ae52
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402280"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Specifické pro Microsoft**  
  
 Volání `IErrorInfo::GetGUID` funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GUID GUID( ) const throw( );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek `IErrorInfo::GetGUID` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Pokud ne `IErrorInfo` objekt zaznamenán, vrátí `GUID_NULL`.  
  
## <a name="remarks"></a>Poznámky  
 Jakékoli neúspěchy při volání `IErrorInfo::GetGUID` metoda se ignoruje.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)