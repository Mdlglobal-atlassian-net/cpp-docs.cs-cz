---
title: Mixin – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ccea9a053f47ae206cbe5c8412c387f07bd5b52
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603424"
---
# <a name="mixin-structure"></a>MixIn – struktura

Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename Derived,
   typename MixInType,
   bool hasImplements = __is_base_of(Details::ImplementsBase,
   MixInType)  
>
struct MixIn;
```

### <a name="parameters"></a>Parametry

*Odvozené*  
Typ odvozený od [implementuje](../windows/implements-structure.md) struktury.

*MixInType*  
Základní typ.

*hasImplements*  
**Hodnota TRUE** Pokud *MixInType* je odvozen od implementace rozhraní aktuální základní typ; **false** jinak.

## <a name="remarks"></a>Poznámky

Pokud je třída odvozená z modulu Windows Runtime a rozhraní třídy modelu COM, seznam deklarací třídy musí nejdříve zobrazit seznam všech rozhraní Windows Runtime a potom všechny klasické rozhraní COM rozhraní. **MixIn** zajistí, že rozhraní jsou zadány ve správném pořadí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MixIn`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)