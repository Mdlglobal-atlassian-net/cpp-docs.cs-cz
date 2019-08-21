---
title: Použití IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 9684781ba99d96e2c58d450ee0ff892374e33aef
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630602"
---
# <a name="using-idispeventimpl"></a>Použití IDispEventImpl

Při použití `IDispEventImpl` ke zpracování událostí budete potřebovat:

- Odvodit třídu z [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Přidejte do své třídy mapu jímky událostí.

- Přidejte položky do mapy jímky událostí pomocí makra [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) .

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

V NotSoSimple. h se zobrazí následující kód. Příslušný kód je zaznamenán v komentářích:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)<br/>
[Ukázka ATLEventHandling](../overview/visual-cpp-samples.md)
