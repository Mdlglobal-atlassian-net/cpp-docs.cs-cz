---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 826ac53f001355127f16b7ad2a7583a0f8800de7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155030"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile

**Microsoft Specific**

Volání `IErrorInfo::GetHelpFile` funkce.

## <a name="syntax"></a>Syntaxe

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetHelpFile` pro `IErrorInfo` zaznamenaný v rámci `_com_error` objektu. Výsledný BSTR je zapouzdřen v objektu `_bstr_t`. Pokud ne `IErrorInfo` je zaznamenán, vrátí prázdný `_bstr_t`.

## <a name="remarks"></a>Poznámky

Jakékoli neúspěchy při volání `IErrorInfo::GetHelpFile` metoda se ignoruje.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)