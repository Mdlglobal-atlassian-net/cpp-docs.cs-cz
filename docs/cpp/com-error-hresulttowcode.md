---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155043"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft Specific**

Mapuje 32-bit HRESULT na 16 bitů `wCode`.

## <a name="syntax"></a>Syntaxe

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parametry

*hr*<br/>
Hodnota HRESULT 32-bit má být mapována na 16 bitů `wCode`.

## <a name="return-value"></a>Návratová hodnota

16bitové `wCode` namapované na základě hodnoty HRESULT 32-bit.

## <a name="remarks"></a>Poznámky

Zobrazit [_com_error::WCode](../cpp/com-error-wcode.md) Další informace.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)