---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180638"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Specifické pro společnost Microsoft**

Volá funkci `IErrorInfo::GetGUID`.

## <a name="syntax"></a>Syntaxe

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetGUID` pro objekt `IErrorInfo` zaznamenaný v rámci objektu `_com_error`. Pokud není zaznamenán žádný objekt `IErrorInfo`, vrátí `GUID_NULL`.

## <a name="remarks"></a>Poznámky

Jakékoli selhání při volání metody `IErrorInfo::GetGUID` je ignorováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
