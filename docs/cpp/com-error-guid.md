---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 905b67577a65b81be0b4d18c7513652dd8c5f055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661627"
---
# <a name="comerrorguid"></a>_com_error::GUID

**Specifické pro Microsoft**

Volání `IErrorInfo::GetGUID` funkce.

## <a name="syntax"></a>Syntaxe

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetGUID` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Pokud ne `IErrorInfo` objekt zaznamenán, vrátí `GUID_NULL`.

## <a name="remarks"></a>Poznámky

Jakékoli neúspěchy při volání `IErrorInfo::GetGUID` metoda se ignoruje.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)