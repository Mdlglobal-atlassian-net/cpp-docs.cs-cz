---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180560"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Specifické pro společnost Microsoft**

Mapuje 32-bit HRESULT na 16 bitů `wCode`.

## <a name="syntax"></a>Syntaxe

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parametry

*oddělení*<br/>
32 bitová hodnota HRESULT, která má být mapována na 16 bitů `wCode`.

## <a name="return-value"></a>Návratová hodnota

16bitová `wCode` namapována z 32.-bit HRESULT.

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [_com_error:: wCode](../cpp/com-error-wcode.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)
