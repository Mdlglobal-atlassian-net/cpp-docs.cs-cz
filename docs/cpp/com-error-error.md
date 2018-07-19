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
ms.openlocfilehash: 21f2da8c10b9b796740144f81d0390f1af124cab
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942052"
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
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)