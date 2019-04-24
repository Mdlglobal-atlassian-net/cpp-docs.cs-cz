---
title: Podpora IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 3652aae2a6c84833ed32e52599d3834d6e66a5ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274284"
---
# <a name="supporting-idispeventimpl"></a>Podpora IDispEventImpl

Třída šablony [IDispEventImpl](../atl/reference/idispeventimpl-class.md) slouží k poskytování podpory pro připojení bodu jímky ve své třídě ATL. Jímka bodu připojení umožňuje vaší třídy pro zpracování událostí vyvolaných z externí objekty modelu COM. Tyto jímky bod připojení se mapují s mapou jímky událostí, poskytnuté vaší třídy.

Jímka bod připojení pro vaši třídu správně implementovat, musí dokončit následující kroky:

- Import knihovny typů pro každý externí objekt

- Deklarovat `IDispEventImpl` rozhraní

- Deklarovat mapu jímky událostí

- Dokáží a zrušíte avízo o spojovací body

Kroky při implementaci jímky bod připojení se provádí úpravou pouze souboru hlaviček (.h) vaší třídy.

## <a name="importing-the-type-libraries"></a>Import knihoven typů

Pro každý externí objekt jehož události, které chcete zpracovat je nutné naimportovat knihovny typů. Tento krok definuje události, které mohou být zpracovány a poskytuje informace, které se používá při deklarování na mapě událostí jímky. [#Import](../preprocessor/hash-import-directive-cpp.md) – direktiva je možné dosáhnout. Přidat nezbytné `#import` direktiv řádky pro každého rozhraní odbavení bude podporovat do souboru hlaviček (.h) vaší třídy.

Následující příklad importuje knihovna typů externího serveru COM (`MSCAL.Calendar.7`):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
>  Musíte mít samostatný `#import` prohlášení pro každou knihovnu externí bude podporovat.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarování idispeventimpl – rozhraní

Teď, když jste naimportovali knihovny typů rozhraní každé odeslání, musíte deklarovat samostatné `IDispEventImpl` rozhraní pro každé rozhraní externí odeslání. Upravte deklaraci vaší třídy tak, že přidáte `IDispEventImpl` rozhraní prohlášení pro každý externí objekt. Další informace o parametrech najdete v tématu [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Následující kód deklaruje dvě jímky bodu připojení, pro `DCalendarEvents` rozhraní COM objekty implementované ve třídě `CMyCompositCtrl2`:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Deklarování mapu jímky událostí

V pořadí pro oznamování událostí zpracovávat správné funkce musí vaše třída směrování každou událost do jeho správné obslužné rutiny. Tím se dosahuje deklarace mapu jímky událostí.

Knihovna ATL poskytuje několik maker [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), a [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), která usnadňují toto mapování. Standardní formát je následující:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

Následující příklad deklaruje mapu jímky událostí s dvě obslužné rutiny události:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

Implementace je téměř dokončena. Poslední krok se týká informací a unadvising externí rozhraní.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Nutnost a Unadvising idispeventimpl – rozhraní

Posledním krokem je implementace metody, která dokáží (nebo zrušíte avízo o) všechny body připojení ve správnou dobu. Tato předobjednávky je třeba provést předtím, než může probíhat komunikace mezi externími klienty a objektu. Předtím, než se objekt stane viditelnou, každé odeslání externí rozhraní nepodporuje objekt se dotazují pro odchozí rozhraní. Navázat připojení a odkaz na odchozí rozhraní se používá ke zpracování událostí z objektu. Tento postup se označuje jako "předobjednávky."

Po dokončení objektu s externí rozhraní by měla odchozí rozhraní oznámení, aby se už používaly vaší třídy. Tento proces se označuje jako "unadvising."

Vzhledem k jedinečné povaze objekty modelu COM tento postup se liší v podrobností a provádění mezi implementací. Tyto podrobnosti jsou nad rámec tohoto tématu a nebudou řešit.

## <a name="see-also"></a>Viz také:

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)
