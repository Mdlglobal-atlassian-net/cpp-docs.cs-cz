---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: f33871634b516723c94fead847f64ef20d25513f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399314"
---
# <a name="comerrorwcode"></a>_com_error::WCode

**Microsoft Specific**

Načte 16bitové chybový kód namapovat na zapouzdřený HRESULT.

## <a name="syntax"></a>Syntaxe

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Pokud je hodnota HRESULT v rozsahu 0x80040200 až 0x8004FFFF, `WCode` metoda vrátí hodnotu HRESULT mínus 0x80040200; v opačném případě vrátí 0.

## <a name="remarks"></a>Poznámky

`WCode` Metoda se používá k vrácení mapování se děje v kódu podpory modelu COM. Obálka `dispinterface` vlastnost nebo metoda zavolá rutinu podpory, která zabalí argumenty a zavolá `IDispatch::Invoke`. Po návratu, pokud selhání hodnoty HRESULT z `DISP_E_EXCEPTION` se vrátí informace o této chybě je načten z `EXCEPINFO` předané do `IDispatch::Invoke`. Kód chyby může být 16bitová hodnota uložená v `wCode` člena `EXCEPINFO` struktury nebo úplná 32bitová hodnota v `scode` člena `EXCEPINFO` struktury. Pokud 16 bitů `wCode` je vrácena, musí být nejprve namapována na 32bitové selhání hodnoty HRESULT.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)