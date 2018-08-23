---
title: Argtraitshelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb0377de88ef5e782e0e11bc563409b7094eecf5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598681"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*  
Rozhraní delegáta.

## <a name="remarks"></a>Poznámky

Pomáhá definovat běžné vlastnosti argumenty delegátů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`methodType`|Synonymum pro `decltype(&TDelegateInterface::Invoke)`.|
|`Traits`|Synonymum pro `ArgTraits<methodType>`.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[ArgTraitsHelper::args – konstanta](../windows/argtraitshelper-args-constant.md)|Pomáhá [ArgTraits::args](../windows/argtraits-args-constant.md) zachovat počet parametrů na `Invoke` metoda rozhraní delegáta.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ArgTraitsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)