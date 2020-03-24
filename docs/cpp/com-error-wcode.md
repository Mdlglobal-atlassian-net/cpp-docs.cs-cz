---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190193"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Specifické pro společnost Microsoft**

Načte 16bitový kód chyby mapovaný do zapouzdřené hodnoty HRESULT.

## <a name="syntax"></a>Syntaxe

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Pokud je HRESULT v rozsahu 0x80040200 až 0x8004FFFF, metoda `WCode` vrátí HRESULT minus 0x80040200; v opačném případě vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

Metoda `WCode` slouží k vrácení mapování, ke kterému dochází v kódu podpory modelu COM. Obálka pro `dispinterface` vlastnost nebo metoda volá rutinu podpory, která zabalí argumenty a volá `IDispatch::Invoke`. Pokud se po návratu vrátí hodnota HRESULT z `DISP_E_EXCEPTION`, informace o chybě se načtou ze struktury `EXCEPINFO` předané do `IDispatch::Invoke`. Kód chyby může být 16bitová hodnota uložená v `wCode` členu struktury `EXCEPINFO` nebo plná hodnota 32 v `scode` členu `EXCEPINFO` struktury. Pokud je vrácena 16bitová `wCode`, musí být nejprve namapována na 32. # 0-bit selhání HRESULT.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)
