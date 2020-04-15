---
title: Přidání funkcí do složeného ovládacího prvku
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317430"
---
# <a name="adding-functionality-to-the-composite-control"></a>Přidání funkcí do složeného ovládacího prvku

Po vložení všech potřebných ovládacích prvků do složeného ovládacího prvku, další krok zahrnuje přidání nové funkce. Tato nová funkce obvykle spadá do dvou kategorií:

- Podpora dalších rozhraní a přizpůsobení chování složeného ovládacího prvku s dalšími specifickými funkcemi.

- Zpracování událostí z obsaženého ovládacího prvku ActiveX (nebo ovládacích prvků).

Pro účely a rozsah tohoto článku zbývající část této části se zaměřuje výhradně na zpracování událostí z ovládacích prvků ActiveX.

> [!NOTE]
> Pokud potřebujete zpracovat zprávy z ovládacích prvků systému Windows, naleznete [v tématu implementace okna](../atl/implementing-a-window.md) další informace o zpracování zpráv v atl.

Po vložení ovládacího prvku ActiveX do prostředku dialogového okna klepněte pravým tlačítkem myši na ovládací prvek a klepněte na příkaz **Přidat obslužnou rutinu události**. Vyberte událost, kterou chcete zpracovat, a klepněte na **tlačítko Přidat a upravit**. Kód obslužné rutiny události bude přidán do souboru H ovládacího prvku.

Spojovací body pro ovládací prvky ActiveX na složeném ovládacím prvku jsou automaticky připojeny a odpojeny prostřednictvím volání [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Viz také

[Základy kompozitního řízení](../atl/atl-composite-control-fundamentals.md)
