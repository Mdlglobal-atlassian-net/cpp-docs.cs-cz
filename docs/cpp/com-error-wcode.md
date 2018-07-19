---
title: _com_error::WCode | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 810a5c16df1027aba976bea3c165b19f765d15a6
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941837"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Specifické pro Microsoft**  
  
 Načte 16bitové chybový kód namapovat na zapouzdřený HRESULT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je hodnota HRESULT v rozsahu 0x80040200 až 0x8004FFFF, `WCode` metoda vrátí hodnotu HRESULT mínus 0x80040200; v opačném případě vrátí 0.  
  
## <a name="remarks"></a>Poznámky  
 `WCode` Metoda se používá k vrácení mapování se děje v kódu podpory modelu COM. Obálka `dispinterface` vlastnost nebo metoda zavolá rutinu podpory, která zabalí argumenty a zavolá `IDispatch::Invoke`. Po návratu, pokud se vrátí selhání HRESULT DISP_E_EXCEPTION, informace o této chybě je načten z `EXCEPINFO` předané do `IDispatch::Invoke`. Kód chyby může být 16bitová hodnota uložená v `wCode` člena `EXCEPINFO` struktury nebo úplná 32bitová hodnota v `scode` člena `EXCEPINFO` struktury. Pokud 16 bitů `wCode` je vrácena, musí být nejprve namapována na 32bitové selhání hodnoty HRESULT.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error – třída](../cpp/com-error-class.md)