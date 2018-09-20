---
title: SafeIntException::SafeIntException | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24138db5ab772990f050fc8fcb6e5dad640a662d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396776"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException

Vytvoří **SafeIntException** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*kód*<br/>
[in] Hodnota výčtu dat, popisující chybu, ke které došlo.

## <a name="remarks"></a>Poznámky

Možné hodnoty parametru *kód* jsou definovány v souboru Safeint.h. Pro usnadnění práce možné hodnoty jsou také uvedeny zde.

- `SafeIntNoError`

- `SafeIntArithmeticOverflow`

- `SafeIntDivideByZero`

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** msl::utilities

## <a name="see-also"></a>Viz také

[SafeInt – knihovna](../windows/safeint-library.md)<br/>
[SafeIntException – třída](../windows/safeintexception-class.md)<br/>
[SafeInt – třída](../windows/safeint-class.md)