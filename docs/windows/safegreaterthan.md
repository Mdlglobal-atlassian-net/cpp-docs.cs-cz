---
title: SafeGreaterThan | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThan
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThan function
ms.assetid: 32cecac9-ba88-43eb-a7a4-30e390456739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eab7af0a5a72c8f5b08e046a527026e77ca67dea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411461"
---
# <a name="safegreaterthan"></a>SafeGreaterThan

Porovná dvě čísla.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ `U`.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je větší než *u*; jinak vrátí hodnotu **false**.

## <a name="remarks"></a>Poznámky

**SafeGreaterThan** rozšiřuje regulární relační operátor tím, že můžete porovnat dva různé typy čísel.

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci jedno porovnání bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

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
[SafeLessThan](../windows/safelessthan.md)<br/>
[SafeLessThanEquals](../windows/safelessthanequals.md)<br/>
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)