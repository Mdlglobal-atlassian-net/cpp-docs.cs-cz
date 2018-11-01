---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: a517c40e9adfbda2d790ce41a48ccf8658bcd3e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544388"
---
# <a name="comerrordescription"></a>_com_error::Description

**Specifické pro Microsoft**

Volání `IErrorInfo::GetDescription` funkce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetDescription` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledná `BSTR` zapouzdřena v `_bstr_t` objektu. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.

## <a name="remarks"></a>Poznámky

Volání `IErrorInfo::GetDescription` funkce a načte `IErrorInfo` zaznamenaný v `_com_error` objektu. Jakékoli neúspěchy při volání `IErrorInfo::GetDescription` metoda se ignoruje.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)