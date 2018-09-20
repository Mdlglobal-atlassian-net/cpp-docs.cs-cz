---
title: SafeAdd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ddf4f69c3c897c8f462554ce6a9db6b2a03408f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400577"
---
# <a name="safeadd"></a>SafeAdd

Sečte dvě čísla způsobem, který chrání proti přetečení.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Chcete-li přidat o první číslo. Toto musí být typu T.

*u*<br/>
[in] Druhé číslo, které chcete přidat. Musí se jednat o typ U.

*výsledek*<br/>
[out] Parametr kde **SafeAdd** výsledek je uložen.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci sčítání jeden bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.

Další informace o typech šablony T a U najdete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)<br/>
[SafeInt – knihovna](../windows/safeint-library.md)<br/>
[SafeInt – třída](../windows/safeint-class.md)<br/>
[SafeSubtract](../windows/safesubtract.md)