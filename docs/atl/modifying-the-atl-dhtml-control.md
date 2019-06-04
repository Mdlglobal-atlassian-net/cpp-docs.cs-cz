---
title: Změna ovládacího prvku ATL DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: e594360cc6752a60bf2e07a1fb1d02041604d959
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503008"
---
# <a name="modifying-the-atl-dhtml-control"></a>Změna ovládacího prvku ATL DHTML

Průvodce ovládacími prvky ATL obsahuje počáteční kód, tak můžete sestavit a spustit ovládací prvek, a abyste viděli, jak metody se zapisují do souborů projektu a jak DHTML volá kód C++ ovládacího prvku pomocí metody odeslání. Můžete přidat libovolnou metodu odeslání rozhraní. Pak můžete volat metody ve zdroji HTML.

## <a name="to-modify-the-atl-dhtml-control"></a>Chcete-li změnit ovládacího prvku ATL DHTML

1. V **zobrazení tříd**, rozbalte projekt ovládacího prvku.

   Všimněte si, že rozhraní, které končí na "Rozhraní" má jednu metodu `OnClick`. Rozhraní, které nekončí "Rozhraní" nemá žádné metody.

1. Přidat metodu nazvanou `MethodInvoked` rozhraní nekončí "Uživatelské rozhraní."

   Tato metoda se přidají do rozhraní, které se používá v kontejneru ovládacího prvku pro interakci s kontejner, aby rozhraní používají DHTML k interakci s ovládacím prvkem. Tuto metodu lze vyvolat pouze kontejneru.

1. V souboru CPP najít metodu prázdná a přidejte kód k zobrazení okna se zprávou, například:

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. Přidat další metodu s názvem `HelloHTML`, jenom tentokrát ho přidat do rozhraní, které končí na "Uživatelské rozhraní." Najít podložit out `HelloHTML` metoda ve .cpp soubor a přidejte kód k zobrazení okna se zprávou, například:

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. Přidat třetí metoda `GoToURL`, rozhraní nekončí "Uživatelské rozhraní." Tuto metodu implementovat voláním [IWebBrowser2::Navigate](/previous-versions//aa752133\(v=vs.85\)), následujícím způsobem:

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   Můžete použít `IWebBrowser2` metody vzhledem k tomu, že knihovna ATL poskytuje ukazatel na rozhraní za vás v souboru hlaviček.

V dalším kroku upravte prostředek ve formátu HTML volat metody, kterou jste vytvořili. Přidejte tři tlačítka pro volání těchto metod.

## <a name="to-modify-the-html-resource"></a>Úprava prostředku HTML

1. V **Průzkumníka řešení**, dvakrát klikněte pro zobrazení prostředku HTML soubor HTM.

   Prozkoumejte kód HTML, zejména volání externí metody odesílání Windows. Kód HTML volá projektu `OnClick` metoda a parametry označení textu ovládacího prvku (`theBody`) a barvu pro přiřazení ("`red`"). Textu po volání metody, které je popisek, který se zobrazí na tlačítku.

1. Přidejte další `OnClick` metodu, jenom změnit barvu. Příklad:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   Tato metoda vytvoří tlačítko s popiskem **aktualizovat**, že uživatel může klepnout a vrátit na původní, bílé pozadí ovládacího prvku.

1. Přidejte volání `HelloHTML` metody, které jste vytvořili. Příklad:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   Tato metoda vytvoří tlačítko s popiskem **HelloHTML**, který může uživatel kliknout na Zobrazit `HelloHTML` okno se zprávou.

Teď můžete vytvářet a [testování upravený ovládací prvek DHTML](../atl/testing-the-modified-atl-dhtml-control.md).

## <a name="see-also"></a>Viz také:

[Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)
