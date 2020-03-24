---
title: MixIn – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213691"
---
# <a name="mixin-structure"></a>MixIn – struktura

Zajišťuje, že třída modulu runtime je odvozena z prostředí Windows Runtime rozhraní, pokud existují, a pak rozhraní modelu COM Classic.

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

*Třídy*<br/>
Typ odvozený z struktury [Implements](implements-structure.md) .

*MixInType*<br/>
Základní typ.

*hasImplements*<br/>
**true** , pokud je *MixInType* odvozen z aktuální implementace základního typu; v opačném případě **NEPRAVDA** .

## <a name="remarks"></a>Poznámky

Pokud je třída odvozena z prostředí Windows Runtime i rozhraní třídy COM, seznam deklarací třídy musí nejprve uvést jakákoli prostředí Windows Runtime rozhraní a pak všechna rozhraní modelu COM Classic. **MixIn** zajistí, že rozhraní jsou určena ve správném pořadí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MixIn`

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
