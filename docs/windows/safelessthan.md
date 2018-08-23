---
title: SafeLessThan | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 499b621c804f13f6a56bc2ce9be0ba91ab824a48
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592397"
---
# <a name="safelessthan"></a>SafeLessThan

Určuje, zda je jedno číslo menší než jiný.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

[in] *t*  
První číslo. Musí se jednat o typ `T`.

[in] *u*  
Druhé číslo. Musí se jednat o typ `U`.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je menší než *u*; jinak vrátí hodnotu **false**.

## <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje standardní relační operátor protože **SafeLessThan** umožňuje porovnat dva různé typy číslo.

Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci jedno porovnání bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).

> [!NOTE]
> Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy spíše než jednotlivé samostatné funkce volání.

Další informace o typech šablon `T` a `U`, naleznete v tématu [SafeInt – funkce](../windows/safeint-functions.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Viz také

[SafeInt – funkce](../windows/safeint-functions.md)  
[SafeInt – knihovna](../windows/safeint-library.md)  
[SafeInt – třída](../windows/safeint-class.md)  
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)