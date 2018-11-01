---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 606f553060e71ece18b3d48159ec40133be28965
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465465"
---
# <a name="comerrorerror"></a>_com_error::Error

**Specifické pro Microsoft**

Načte hodnotu HRESULT předaný konstruktoru.

## <a name="syntax"></a>Syntaxe

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Nezpracovaná položka HRESULT předaná do konstruktoru.

## <a name="remarks"></a>Poznámky

Načte položku zapouzdřený HRESULT v `_com_error` objektu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error – třída](../cpp/com-error-class.md)