---
title: Issame – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7d1879217ac43e2d7d3714f491f44b8245f4f27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390516"
---
# <a name="issame-structure"></a>IsSame – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T1,
   typename T2
>
struct IsSame;
template <
   typename T1
>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ.

*T2*<br/>
Jiného typu.

## <a name="remarks"></a>Poznámky

Testy, zda jeden zadaný typ je stejný jako jiný určený typ.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[IsSame::value – konstanta](../windows/issame-value-constant.md)|Označuje, zda jeden typ. je stejný jako jiný.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsSame`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)