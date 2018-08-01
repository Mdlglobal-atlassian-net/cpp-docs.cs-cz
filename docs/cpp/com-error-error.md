---
title: _com_error::Error | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408424"
---
# <a name="comerrorerror"></a>_com_error::Error
**Specifické pro Microsoft**  
  
 Načte hodnotu HRESULT předaný konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Nezpracovaná položka HRESULT předaná do konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Načte položku zapouzdřený HRESULT v `_com_error` objektu.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)