---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593054"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Specifické pro Microsoft**

Mapuje 16bitové *wCode* 32-bit HRESULT.

## <a name="syntax"></a>Syntaxe

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parametry

*WCode*<br/>
16bitové hodnoty *wCode* namapována na 32bitové HRESULT.

## <a name="return-value"></a>Návratová hodnota

Mapovaná z 16bitové hodnoty HRESULT 32-bit *wCode*.

## <a name="remarks"></a>Poznámky

Zobrazit [WCode](../cpp/com-error-wcode.md) členskou funkci.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)