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
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329313"
---
# <a name="supporting-idispeventimpl"></a>Podpora IDispEventImpl

Třídu šablony [IDispEventImpl](../atl/reference/idispeventimpl-class.md) lze použít k poskytování podpory pro propady spojovacích bodů ve vaší třídě ATL. Jímka spojovacího bodu umožňuje třídy pro zpracování událostí vyvolaný z externích objektů COM. Tyto jímky spojovacího bodu jsou mapovány s mapou jímky událostí, poskytované vaší třídy.

Chcete-li správně implementovat jímky spojovacího bodu pro vaši třídu, je nutné provést následující kroky:

- Import knihoven typů pro každý externí objekt

- Deklarovat `IDispEventImpl` rozhraní

- Deklarovat mapu jímky událostí

- Poradit a neporadit spojovací body

Kroky zapojené do implementace jímky spojovacího bodu jsou všechny provedeny úpravou pouze soubor záhlaví (.h) vaší třídy.

## <a name="importing-the-type-libraries"></a>Import knihoven typů

Pro každý externí objekt, jehož události chcete zpracovat, je nutné importovat knihovnu typů. Tento krok definuje události, které mohou být zpracovány a poskytuje informace, které se používá při deklarování mapy jímky událostí. K dosažení tohoto cíle lze použít [#import](../preprocessor/hash-import-directive-cpp.md) direktivu. Přidejte `#import` řádky nezbytné směrnice pro každé rozhraní odeslání, které budete podporovat do souboru záhlaví (.h) vaší třídy.

Následující příklad importuje knihovnu typů externího serveru COM (`MSCAL.Calendar.7`):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Pro každou externí `#import` knihovnu typů, kterou budete podporovat, musíte mít samostatný příkaz.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarování rozhraní IDispEventImpl

Nyní, když jste importovali knihovny typů každého rozhraní odeslání, je třeba deklarovat samostatná `IDispEventImpl` rozhraní pro každé externí rozhraní odeslání. Upravte deklaraci třídy `IDispEventImpl` přidáním deklarace rozhraní pro každý externí objekt. Další informace o parametrech naleznete v tématu [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Následující kód deklaruje dvě propady spojovacích bodů pro `DCalendarEvents` `CMyCompositCtrl2`rozhraní pro objekt COM implementovaný třídou :

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Deklarování mapy jímky událostí

Aby oznámení událostí zpracována správnou funkcí, musí vaše třída směrovat každou událost na správnou obslužnou rutinu. Toho je dosaženo deklarováním mapy jímky událostí.

Seznam ATL poskytuje několik maker, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)a [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), které toto mapování usnadňují. Standardní formát je následující:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

Následující příklad deklaruje mapu jímky událostí se dvěma obslužnými rutinami událostí:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

Implementace je téměř dokončena. Poslední krok se týká poradenství a neposkytování poradenství externím rozhraním.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Poradenství a unadvising IDispEventImpl rozhraní

Posledním krokem je implementace metody, která poradí (nebo neradí) všechny spojovací body ve správný čas. Toto poradenství musí být provedeno před komunikací mezi externími klienty a vaším objektem. Před objekt se stane viditelným, každé externí odeslání rozhraní podporované objektem je dotazován pro odchozí rozhraní. Je navázáno připojení a odkaz na odchozí rozhraní se používá ke zpracování událostí z objektu. Tento postup se označuje jako "poradenství".

Po dokončení objektu s externími rozhraními by odchozí rozhraní měla být upozorněna, že již nejsou používána vaší třídou. Tento proces se označuje jako "unadvising."

Vzhledem k jedinečné povaze objektů COM se tento postup v detailech a provádění liší mezi implementacemi. Tyto podrobnosti jsou nad rámec tohoto tématu a nejsou řešeny.

## <a name="see-also"></a>Viz také

[Základy objektů ATL COM](../atl/fundamentals-of-atl-com-objects.md)
