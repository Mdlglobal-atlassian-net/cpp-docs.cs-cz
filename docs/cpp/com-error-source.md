---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180521"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Specifické pro společnost Microsoft**

Volá funkci `IErrorInfo::GetSource`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetSource` pro objekt `IErrorInfo` zaznamenaný v rámci objektu `_com_error`. Výsledný `BSTR` je zapouzdřený v objektu `_bstr_t`. Pokud není zaznamenána žádná `IErrorInfo`, vrátí prázdnou `_bstr_t`.

## <a name="remarks"></a>Poznámky

Jakékoli selhání při volání metody `IErrorInfo::GetSource` je ignorováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
