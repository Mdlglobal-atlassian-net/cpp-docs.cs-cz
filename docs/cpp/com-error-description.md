---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180768"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Specifické pro společnost Microsoft**

Volá funkci `IErrorInfo::GetDescription`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetDescription` pro objekt `IErrorInfo` zaznamenaný v rámci objektu `_com_error`. Výsledný `BSTR` je zapouzdřený v objektu `_bstr_t`. Pokud není zaznamenána žádná `IErrorInfo`, vrátí prázdnou `_bstr_t`.

## <a name="remarks"></a>Poznámky

Zavolá funkci `IErrorInfo::GetDescription` a načte `IErrorInfo` zaznamenanou v rámci objektu `_com_error`. Jakékoli selhání při volání metody `IErrorInfo::GetDescription` je ignorováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
