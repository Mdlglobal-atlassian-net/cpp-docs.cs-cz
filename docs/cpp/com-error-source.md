---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 682070877f269967405677d027b20707c8366f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154954"
---
# <a name="comerrorsource"></a>_com_error::Source

**Microsoft Specific**

Volání `IErrorInfo::GetSource` funkce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetSource` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledná `BSTR` zapouzdřena v `_bstr_t` objektu. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.

## <a name="remarks"></a>Poznámky

Jakékoli neúspěchy při volání `IErrorInfo::GetSource` metoda se ignoruje.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)