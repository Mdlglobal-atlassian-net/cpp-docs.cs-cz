---
title: SafeIntException::SafeIntException | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs: C++
helpviewer_keywords: SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d9a1e2666aef593cde385f121065397226bad9d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Vytvoří `SafeIntException` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`code`  
 Hodnota výčtové dat, která popisuje chybu, která došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Možné hodnoty `code` jsou definovány v souboru Safeint.h. Pro usnadnění práce možné hodnoty jsou také uvedeny zde.  
  
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