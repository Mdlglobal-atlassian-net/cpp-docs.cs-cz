---
title: _com_error::source | Microsoft Docs
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
ms.openlocfilehash: a33834df20606e8380e6a328a41435522185ac70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412342"
---
# <a name="comerrorsource"></a>_com_error::Source
**Konkrétní Microsoft**  
  
 Volání **IErrorInfo::GetSource** funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek **IErrorInfo::GetSource** pro **IErrorInfo** objekt zaznamenávají v rámci `_com_error` objektu. Výsledný BSTR je zapouzdřen v objektu `_bstr_t`. Pokud žádné **IErrorInfo** se zaznamenávají, vrátí prázdnou `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Jakákoli chyba při volání **IErrorInfo::GetSource** metoda je ignorována.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)