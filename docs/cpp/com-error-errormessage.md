---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500581"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Specifické pro společnost Microsoft**

Načte řetězcovou zprávu pro HRESULT uloženou v `_com_error` objektu.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí řetězcovou zprávu pro hodnotu HRESULT zaznamenanou v `_com_error` rámci objektu. Pokud je HRESULT namapovaná 16bitová [wCode](../cpp/com-error-wcode.md), pak je vrácena obecná zpráva "`IDispatch error #<wCode>`". Není-li nalezena žádná zpráva, je vrácena obecná zpráva „`Unknown error #<hresult>`“. Vrácený řetězec je buď Unicode, nebo vícebajtový řetězec, v závislosti na stavu makra _UNICODE.

## <a name="remarks"></a>Poznámky

Načte příslušný text systémové zprávy pro HRESULT zaznamenanou v rámci `_com_error` objektu. Text systémové zprávy se získá voláním funkce Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . Vrácený řetězec je alokován pomocí rozhraní API `FormatMessage` a je uvolněn po zničení objektu `_com_error`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)