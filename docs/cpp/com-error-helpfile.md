---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190219"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Specifické pro společnost Microsoft**

Volá funkci `IErrorInfo::GetHelpFile`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetHelpFile` pro objekt `IErrorInfo` zaznamenaný v rámci objektu `_com_error`. Výsledný BSTR je zapouzdřen v objektu `_bstr_t`. Pokud není zaznamenána žádná `IErrorInfo`, vrátí prázdnou `_bstr_t`.

## <a name="remarks"></a>Poznámky

Jakékoli selhání při volání metody `IErrorInfo::GetHelpFile` je ignorováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
