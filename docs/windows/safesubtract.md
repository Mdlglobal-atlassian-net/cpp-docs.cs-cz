---
title: SafeSubtract | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 055c1a0c19afce43338df90a92afef2a8469f3f7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584026"
---
# <a name="safesubtract"></a>SafeSubtract

Odečte dvě čísla způsobem, který chrání proti přetečení.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

[in] *t*  
První číslo v odčítání. Musí se jednat o typ `T`.

[in] *u*  
Číslo, které se má odečíst od *t*. Musí se jednat o typ `U`.

[out] *výsledek*  
Parametr kde **SafeSubtract** výsledek je uložen.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a slouží k odečtení jedné operace bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.

Další informace o typech šablon `T` a `U`, naleznete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)  
[SafeInt – knihovna](../windows/safeint-library.md)  
[SafeInt – třída](../windows/safeint-class.md)  
[SafeAdd](../windows/safeadd.md)