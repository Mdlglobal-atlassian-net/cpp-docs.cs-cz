---
title: Interfacetraits::casttobase – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55a4d7487be5b3565ba3945630cab4388f287a68
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611821"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*  
Typ parametru *ptr*.

*ptr*  
Ukazatel na typ *T*.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `Base`.

## <a name="remarks"></a>Poznámky

Přetypování zadaný ukazatel na ukazatel na `Base`.

Další informace o `Base`, naleznete v části veřejné definice TypeDef [interfacetraits – struktura](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[InterfaceTraits – struktura](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)