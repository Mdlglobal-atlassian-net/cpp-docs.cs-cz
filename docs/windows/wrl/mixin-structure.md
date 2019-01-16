---
title: MixIn – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: d0306f4c497dd26e782b1ef2c012cb7d348db07f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334764"
---
# <a name="mixin-structure"></a>MixIn – struktura

Zajišťuje, že runtime třídy je odvozen z rozhraní Windows Runtime, pokud existuje a potom klasické rozhraní COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>Parametry

*Odvozené*<br/>
Typ odvozený od [implementuje](implements-structure.md) struktury.

*MixInType*<br/>
Základní typ.

*hasImplements*<br/>
**Hodnota TRUE** Pokud *MixInType* je odvozen od implementace rozhraní aktuální základní typ; **false** jinak.

## <a name="remarks"></a>Poznámky

Pokud je třída odvozená z modulu Windows Runtime a rozhraní třídy modelu COM, seznam deklarací třídy musí nejdříve zobrazit seznam všech rozhraní Windows Runtime a potom všechny klasické rozhraní COM rozhraní. **MixIn** zajistí, že rozhraní jsou zadány ve správném pořadí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MixIn`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)