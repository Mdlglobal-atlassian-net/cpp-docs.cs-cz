---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180755"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Specifické pro společnost Microsoft**

Načte HRESULT předaný konstruktoru.

## <a name="syntax"></a>Syntaxe

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Návratová hodnota

Nezpracovaná položka HRESULT byla předána do konstruktoru.

## <a name="remarks"></a>Poznámky

Načte zapouzdřenou položku HRESULT v objektu `_com_error`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
