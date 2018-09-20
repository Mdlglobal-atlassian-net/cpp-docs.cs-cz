---
title: Removereference – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
dev_langs:
- C++
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6ab085e1bed3909090990cfa8e265bea792a483
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447021"
---
# <a name="removereference-structure"></a>RemoveReference – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
struct RemoveReference;
template<class T>
struct RemoveReference<T&>;
template<class T>
struct RemoveReference<T&&>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída.

## <a name="remarks"></a>Poznámky

Odebere odkaz nebo odkaz na r-hodnoty vlastností z dané třídy parametru šablony.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`Type`|Synonymum pro parametr šablony třídy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RemoveReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)