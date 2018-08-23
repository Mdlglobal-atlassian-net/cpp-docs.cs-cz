---
title: Eventtargetarray::eventtargetarray – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bbf6cb67973d7538aa7aea0d846cbadf030d585
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590649"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*hr*  
Po operacích tento konstruktor parametr *hr* označuje, zda přidělení pole bylo úspěšné nebo neúspěšné. V následující tabulce jsou uvedeny možné hodnoty pro *hr*.

S_OK operace byla úspěšná.

Nepodařilo se přidělit paměť E_OUTOFMEMORY pro pole.

Parametr S_FALSE *položky* je menší než nebo rovna nule.

*Položky*  
Počet prvků pole pro přidělení.

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy **EventTargetArray** třídy.

**Eventtargetarray –** umožňuje zachovat pole obslužné rutiny událostí v `EventSource` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[EventTargetArray – třída](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)