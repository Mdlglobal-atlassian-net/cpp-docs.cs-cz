---
title: Idispeventsimpleimpl – použití (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 2da4c017f686f35f721dd2bff45436e95fb33630
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57811189"
---
# <a name="using-idispeventsimpleimpl"></a>Idispeventsimpleimpl – použití

Při použití `IDispEventSimpleImpl` zpracování událostí, budete muset:

- Odvodit třídu z [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md).

- Přidáte mapu jímky událostí do vaší třídy.

- Definování [_atl_func_info –](../atl/reference/atl-func-info-structure.md) struktury popisující události.

- Přidání položky do pomocí mapě událostí jímky [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) – makro.

- Implementace metody, že máte zájem zpracování.

- Dokáží a zrušíte avízo o zdroji události.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak naložit `DocumentChange` události vyvolané Wordu **aplikace** objektu. Tato událost je definována jako metody na `ApplicationEvents` dispinterface.

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Jediná informace z knihovny typů ve skutečnosti použitý v tomto příkladu je identifikátor CLSID slova `Application` objektu a identifikátor IID `ApplicationEvents` rozhraní. Tyto informace slouží jenom v době kompilace.

Následující kód se zobrazí v Simple.h. Příslušný kód je uvedeno ve komentáře:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Následující kód je z Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)<br/>
[Ukázka ATLEventHandling](../visual-cpp-samples.md)
