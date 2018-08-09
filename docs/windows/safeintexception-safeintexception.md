---
title: SafeIntException::SafeIntException | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 393c424feb2a84fff85ba0efb5de7cbcaf54737c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016756"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Vytvoří **SafeIntException** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kódu*  
 Hodnota výčtu dat, popisující chybu, ke které došlo.  
  
## <a name="remarks"></a>Poznámky  
 Možné hodnoty parametru *kód* jsou definovány v souboru Safeint.h. Pro usnadnění práce možné hodnoty jsou také uvedeny zde.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeIntException – třída](../windows/safeintexception-class.md)   
 [SafeInt – třída](../windows/safeint-class.md)