---
title: Removeiunknown – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81892b624425032c8f0e69fe667ad24026c40ca4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410261"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
struct RemoveIUnknown;

template <
   typename T
>
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