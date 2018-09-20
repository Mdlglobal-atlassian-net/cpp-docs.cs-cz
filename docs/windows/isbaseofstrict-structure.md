---
title: Isbaseofstrict – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52db5abd0487624f52f692e785007adaf9eac7ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428262"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*základ*<br/>
Základní typ.

*Odvozené*<br/>
Odvozeného typu.

## <a name="remarks"></a>Poznámky

Ověřuje, zda je jeden typ základ jiného.

První šablona testuje, jestli typ je odvozen od základního typu, který může přinést **true** nebo **false**. Druhá šablona testuje, jestli je typ odvozený od sebe sama, který vždy dává **false**.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[IsBaseOfStrict::value – konstanta](../windows/isbaseofstrict-value-constant.md)|Označuje, zda je jeden typ základ jiného.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsBaseOfStrict`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)