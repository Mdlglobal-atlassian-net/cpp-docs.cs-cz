---
title: _com_error::Error | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d56fcf7faaee9d3b0e02964163aa62372a30a78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109289"
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