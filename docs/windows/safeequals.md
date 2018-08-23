---
title: SafeEquals | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b0c2bb91f21b48554ca523a3523e82eee09d2fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600580"
---
# <a name="safeequals"></a>SafeEquals

Porovná dvě čísla, chcete-li zjistit, jestli jsou shodné.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

[in] *t*  
První číslo k porovnání. Toto musí být typu T.

[in] *u*  
Druhé číslo k porovnání. Musí se jednat o typ U.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* a *u* jsou stejné; jinak **false**.

## <a name="remarks"></a>Poznámky

Metoda rozšiřuje `==` protože **SafeEquals** umožňuje porovnat dva různé typy čísel.

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci jedno porovnání bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.

Další informace o typech šablony T a U najdete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)  
[SafeInt – knihovna](../windows/safeint-library.md)  
[SafeInt – třída](../windows/safeint-class.md)  
[SafeNotEquals](../windows/safenotequals.md)