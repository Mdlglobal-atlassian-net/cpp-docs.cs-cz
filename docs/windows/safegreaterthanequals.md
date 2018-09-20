---
title: SafeGreaterThanEquals | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5b7ab93665ce4f5f15aed68520a130897bdcd90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397153"
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Porovná dvě čísla.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
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

**Hodnota TRUE** Pokud *t* je větší než nebo rovna hodnotě *u*; jinak vrátí hodnotu **false**.

## <a name="remarks"></a>Poznámky

**SafeGreaterThanEquals** zvyšuje standard relační operátor, protože ho můžete porovnat dva různé typy čísel.

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
[SafeGreaterThan](../windows/safegreaterthan.md)<br/>
[SafeLessThanEquals](../windows/safelessthanequals.md)<br/>
[SafeLessThan](../windows/safelessthan.md)