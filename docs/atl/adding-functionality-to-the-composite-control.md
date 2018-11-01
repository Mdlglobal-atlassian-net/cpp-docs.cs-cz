---
title: Přidání funkcí do složeného ovládacího prvku
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 1f0759c9182ad2a7e572bacee7707963d9b6ae2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532658"
---
# <a name="adding-functionality-to-the-composite-control"></a>Přidání funkcí do složeného ovládacího prvku

Po vložení všech příslušných ovládacích prvků do složeného ovládacího prvku na další krok zahrnuje přidání nové funkce. Tato nová funkce je obvykle spadá do dvou kategorií:

- Podpora dalších rozhraní a přizpůsobení chování vaší složený ovládací prvek s další specifické funkce.

- Zpracování událostí z obsažených ovládacího prvku ActiveX (nebo ovládací prvky).

Zbytek tohoto oddílu se pro účel a rozsah tohoto článku, zaměřuje výhradně na zpracování událostí z ovládacích prvků ActiveX.

> [!NOTE]
>  Pokud potřebujete zpracovávat zprávy z ovládacích prvků Windows, přečtěte si téma [implementace okna](../atl/implementing-a-window.md) Další informace o zpracování zpráv v knihovně ATL

Po vložení ovládacího prvku ActiveX v prostředku dialogového okna, klikněte pravým tlačítkem na ovládací prvek a klikněte na tlačítko **přidat obslužnou rutinu události**. Vyberte události, které chcete zpracovat a klikněte na tlačítko **přidávat a upravovat**. Kód pro obslužnou rutinu události se přidají do souboru .h ovládacího prvku.

Body připojení pro ovládací prvky ActiveX na složený ovládací prvek automaticky připojené a odpojené prostřednictvím volání do [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Viz také

[Principy vytváření složených prvků](../atl/atl-composite-control-fundamentals.md)

