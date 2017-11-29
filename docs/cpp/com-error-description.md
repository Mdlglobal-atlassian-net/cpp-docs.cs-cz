---
title: _com_error::Description | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::Description
dev_langs: C++
helpviewer_keywords: Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4bf868fd548cc7e0c72559f3754d7e1a035cfa5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comerrordescription"></a>_com_error::Description
**Konkrétní Microsoft**  
  
 Volání **IErrorInfo::GetDescription** funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek **IErrorInfo::GetDescription** pro **IErrorInfo** objekt zaznamenávají v rámci `_com_error` objektu. Výsledná `BSTR` je zapouzdřené v `_bstr_t` objektu. Pokud žádné **IErrorInfo** se zaznamenávají, vrátí prázdnou `_bstr_t`.  
  
## <a name="remarks"></a>Poznámky  
 Volání **IErrorInfo::GetDescription** funkce a načte **IErrorInfo** zaznamenávají v rámci `_com_error` objektu. Jakákoli chyba při volání **IErrorInfo::GetDescription** metoda je ignorována.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)