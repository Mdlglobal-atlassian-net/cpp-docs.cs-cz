---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559000"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Specifické pro Microsoft**

Načte `IErrorInfo` objekt předaný konstruktoru.

## <a name="syntax"></a>Syntaxe

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Nezpracovaná položka `IErrorInfo` předaná do konstruktoru.

## <a name="remarks"></a>Poznámky

Načítá zapouzdřenou `IErrorInfo` položky v `_com_error` objektu, nebo hodnota NULL, pokud žádné `IErrorInfo` zaznamenává se položek. Volající musí volat `Release` pro vrácený objekt po dokončení jeho použití.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)