---
title: _com_error::ErrorInfo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52935c81849ded072cb20d6c835b3a71b66c2871
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941311"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Specifické pro Microsoft**  
  
 Načte `IErrorInfo` objekt předaný konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Nezpracovaná položka `IErrorInfo` předaná do konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Načítá zapouzdřenou `IErrorInfo` položky v `_com_error` objektu, nebo hodnota NULL, pokud žádné `IErrorInfo` zaznamenává se položek. Volající musí volat `Release` pro vrácený objekt po dokončení jeho použití.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)