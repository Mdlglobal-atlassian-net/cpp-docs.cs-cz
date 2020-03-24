---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180664"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Specifické pro společnost Microsoft**

Načte řetězcovou zprávu pro HRESULT uloženou v objektu `_com_error`.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí řetězcovou zprávu pro hodnotu HRESULT zaznamenanou v objektu `_com_error`. Pokud je HRESULT namapovaná 16bitová [wCode](../cpp/com-error-wcode.md), je vrácena obecná zpráva "`IDispatch error #<wCode>`". Není-li nalezena žádná zpráva, je vrácena obecná zpráva „`Unknown error #<hresult>`“. Vrácený řetězec je typu Unicode nebo vícebajtový řetězec, v závislosti na stavu makra _UNICODE.

## <a name="remarks"></a>Poznámky

Načte příslušný text systémové zprávy pro HRESULT zaznamenaný v rámci objektu `_com_error`. Text systémové zprávy se získá voláním funkce Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . Vrácený řetězec je alokován pomocí rozhraní API `FormatMessage` a je uvolněn po zničení objektu `_com_error`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
