---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180703"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Specifické pro společnost Microsoft**

Načte objekt `IErrorInfo` předaný konstruktoru.

## <a name="syntax"></a>Syntaxe

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Nezpracovaná položka `IErrorInfo` předaná do konstruktoru.

## <a name="remarks"></a>Poznámky

Načte zapouzdřenou `IErrorInfo` položku v objektu `_com_error` nebo hodnotu NULL, pokud není zaznamenána žádná `IErrorInfo` položka. Volající musí volat `Release` vráceného objektu po jeho dokončení pomocí.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
