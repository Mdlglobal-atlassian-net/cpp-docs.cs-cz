---
title: _com_error::source | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a725ddb3ff72acc749a5dbf09d2ddcc94856590c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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