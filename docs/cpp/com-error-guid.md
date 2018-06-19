---
title: _com_error::GUID | Microsoft Docs
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
ms.openlocfilehash: ee1952e50251cfac7563357c7626ab8603589e4d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409678"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Konkrétní Microsoft**  
  
 Volání **IErrorInfo::GetGUID** funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek **IErrorInfo::GetGUID** pro **IErrorInfo** objekt zaznamenávají v rámci `_com_error` objektu. Pokud žádné **IErrorInfo** objekt se zaznamená, vrátí `GUID_NULL`.  
  
## <a name="remarks"></a>Poznámky  
 Jakákoli chyba při volání **IErrorInfo::GetGUID** metoda je ignorována.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)