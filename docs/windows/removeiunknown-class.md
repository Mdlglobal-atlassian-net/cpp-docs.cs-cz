---
title: RemoveIUnknown – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 06b3ec86874bcf7968483eb4557b6b6b247ecdfe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556348"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída.

## <a name="remarks"></a>Poznámky

Vytvoří typ, který je ekvivalentní `IUnknown`– podle typu, ale má nevirtuální `QueryInterface`, `AddRef`, a `Release` členské funkce.

Ve výchozím nastavení, poskytují virtuální metody modelu COM `QueryInterface`, `AddRef`, a `Release` metody. Ale `ComPtr` nevyžaduje režijní náklady na virtuální metody. `RemoveIUnknown` Eliminuje režijní náklady na tento tím, že poskytuje privátní, nevirtuální `QueryInterface`, `AddRef`, a `Release` metody.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`ReturnType`|Synonymum pro typ, který se rovná parametru šablony *T* , ale má nevirtuální `IUnknown` členy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)