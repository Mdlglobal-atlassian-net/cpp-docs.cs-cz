---
title: Idispeventimpl – použití (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d28a9a8bad8ced772d5c698e76d3d08f09c8db2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066471"
---
# <a name="using-idispeventimpl"></a>Idispeventimpl – použití

Při použití `IDispEventImpl` zpracování událostí, budete muset:

- Odvodit třídu z [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Přidáte mapu jímky událostí do vaší třídy.

- Přidání položky do pomocí mapě událostí jímky [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) – makro.

- Implementace metody, že máte zájem zpracování.

- Dokáží a zrušíte avízo o zdroji události.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zpracovat `DocumentChange` události vyvolané Wordu **aplikace** objektu. Tato událost je definována jako metody na `ApplicationEvents` dispinterface.

Příklad je z [ATLEventHandling ukázka](../visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

V příkladu `#import` ke generování požadované záhlaví soubory z knihovny typů Wordu. Pokud chcete použít tento příklad s jinými verzemi aplikace Word, musíte zadat správné mso souboru knihovny dll. Například Office 2000 poskytuje mso9.dll a OfficeXP poskytuje mso.dll. Tento kód je jednodušší z stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Následující kód se zobrazí v NotSoSimple.h. Příslušný kód je uvedeno ve komentáře:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Viz také

[Zpracování událostí](../atl/event-handling-and-atl.md)<br/>
[Ukázka ATLEventHandling](../visual-cpp-samples.md)

