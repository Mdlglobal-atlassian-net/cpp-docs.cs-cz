---
title: _com_error::HelpContext | Microsoft Docs
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
ms.openlocfilehash: 7123fcf5859ce3fc373b29b4cb3e7b32109b464e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410821"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Konkrétní Microsoft**  
  
 Volání **IErrorInfo::GetHelpContext** funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek **IErrorInfo::GetHelpContext** pro **IErrorInfo** objekt zaznamenávají v rámci `_com_error` objektu. Pokud žádné **IErrorInfo** objekt se zaznamená, vrátí nulu.  
  
## <a name="remarks"></a>Poznámky  
 Jakákoli chyba při volání **IErrorInfo::GetHelpContext** metoda je ignorována.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)