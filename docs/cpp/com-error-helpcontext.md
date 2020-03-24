---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180586"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Specifické pro společnost Microsoft**

Volá funkci `IErrorInfo::GetHelpContext`.

## <a name="syntax"></a>Syntaxe

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí výsledek `IErrorInfo::GetHelpContext` pro objekt `IErrorInfo` zaznamenaný v rámci objektu `_com_error`. Pokud není zaznamenán žádný objekt `IErrorInfo`, vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

Jakékoli selhání při volání metody `IErrorInfo::GetHelpContext` je ignorováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
