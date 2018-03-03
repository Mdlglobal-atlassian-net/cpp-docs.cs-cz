---
title: _com_error::WCode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74f79491b9d4f88e19bcd0f7a20c94b26d0f7909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Konkrétní Microsoft**  
  
 Načte kód chyby 16bitové namapovat na zapouzdřené `HRESULT`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `HRESULT` je v rozsahu 0x80040200 0x8004FFFF **wcode –** metoda vrátí `HRESULT` minus 0x80040200; jinak vrátí hodnotu nula.  
  
## <a name="remarks"></a>Poznámky  
 **Wcode –** metoda se používá k mapování, který se stane v kódu Podpora COM vrátit zpět. Obálka pro **dispinterface** vlastnost nebo metoda k volání rutiny podpory, které balíčky argumentů a volání **volání metody IDispatch::Invoke**. Po návratu, pokud selhání `HRESULT` z `DISP_E_EXCEPTION` se vrátí informace o chybě se načítají **EXCEPINFO** struktura předaný **volání metody IDispatch::Invoke**. Kód chyby může to být 16bitové hodnotou uloženou v `wCode` členem **EXCEPINFO** struktura nebo úplné 32bitovou hodnotu v **kód scode** členem **EXCEPINFO**struktura. Je-li vrácena 16bitová hodnota `wCode`, musí být nejprve namapována na 32bitové selhání `HRESULT`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error – třída](../cpp/com-error-class.md)