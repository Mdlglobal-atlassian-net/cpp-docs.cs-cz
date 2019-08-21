---
title: Použití IDispEventSimpleImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 8a5e64093d2687efc6c6c5e9b0ce89402d2b99a4
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630574"
---
# <a name="using-idispeventsimpleimpl"></a>Použití IDispEventSimpleImpl

Při použití `IDispEventSimpleImpl` ke zpracování událostí budete potřebovat:

- Odvodit třídu z [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Přidejte do své třídy mapu jímky událostí.

- Definujte struktury [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) popisující události.

- Pomocí makra [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) přidejte položky do mapy jímky událostí.

- Implementujte metody, které zajímáte o zpracování.

- Poraďte a informujte zdroj události.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zpracovat `DocumentChange` událost vyvolaná objektem **aplikace** v aplikaci Word. Tato událost je definována jako metoda pro odesílající rozhraní `ApplicationEvents` .

Příklad se nachází v [ukázce ATLEventHandling](../overview/visual-cpp-samples.md).

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

Tento příklad používá `#import` ke generování požadovaných hlavičkových souborů z knihovny typů aplikace Word. Chcete-li použít tento příklad pro jiné verze aplikace Word, je nutné zadat správný soubor DLL knihovny Mso. Například sada Office 2000 poskytuje Mso9. dll a OfficeXP poskytuje Mso. dll. Tento kód je zjednodušený z *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší):

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Jediné informace z knihovny typů, které jsou aktuálně použity v tomto příkladu, jsou CLSID objektu aplikace `Application` Word a identifikátorem IID `ApplicationEvents` rozhraní. Tyto informace se používají pouze v době kompilace.

Následující kód se zobrazí v jednoduchém. h. Příslušný kód je zaznamenán v komentářích:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Následující kód pochází z jednoduché. cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)<br/>
[Ukázka ATLEventHandling](../overview/visual-cpp-samples.md)
