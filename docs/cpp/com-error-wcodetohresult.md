---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180508"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Specifické pro společnost Microsoft**

Mapuje 16 bitů *wCode* na 32-bit HRESULT.

## <a name="syntax"></a>Syntaxe

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parametry

*wCode*<br/>
16bitový *wCode* , který má být namapován na 32-bit HRESULT.

## <a name="return-value"></a>Návratová hodnota

32. bit HRESULT namapovaný z 16bitové *wCodey*.

## <a name="remarks"></a>Poznámky

Podívejte se na členskou funkci [wCode](../cpp/com-error-wcode.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)
