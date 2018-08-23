---
title: SafeCast | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27c049b57d51f173e2a388e48f24d9b9674ae46b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606094"
---
# <a name="safecast"></a>SafeCast

Přetypování jednom typu čísla do jiného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

[in] *z*  
Zdroj číslo k převedení. Musí se jednat o typ `T`.

[out] *Do*  
Odkaz na nový typ number. Musí se jednat o typ `U`.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro přetypování jedné operace bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze pokud jedné operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.

Další informace o typech šablony T a U najdete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)  
[SafeInt – knihovna](../windows/safeint-library.md)  
[SafeInt – třída](../windows/safeint-class.md)