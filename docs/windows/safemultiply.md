---
title: SafeMultiply | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeMultiply
dev_langs:
- C++
helpviewer_keywords:
- SafeMultiply function
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0eb1b8b37737d1c0c36af28da9b0c656e26de7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396740"
---
# <a name="safemultiply"></a>SafeMultiply

Vynásobí dvě čísla společně způsobem, který chrání proti přetečení.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo pro vynásobení. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo pro vynásobení. Musí se jednat o typ `U`.

*výsledek*<br/>
[out] Parametr kde **SafeMultiply** výsledek je uložen.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci násobení jeden bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.

Další informace o typech šablon `T` a `U`, naleznete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)<br/>
[SafeInt – knihovna](../windows/safeint-library.md)<br/>
[SafeInt – třída](../windows/safeint-class.md)<br/>
[SafeDivide](../windows/safedivide.md)