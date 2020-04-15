---
title: Návrhář pásu karet (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372801"
---
# <a name="ribbon-designer-mfc"></a>Návrhář pásu karet (MFC)

Návrhář pásu karet umožňuje vytvářet a přizpůsobovat pásy karet v aplikacích knihovny MFC. Pás karet je prvek uživatelského rozhraní , který uspořádá příkazy do logických skupin. Tyto skupiny se zobrazují na samostatných kartách v pruhu v horní části okna. Pás karet nahradí panel nabídek a panely nástrojů. Pás karet může výrazně zlepšit použitelnost aplikace. Další informace naleznete v [tématu Ribbons](/windows/win32/uxguide/cmd-ribbons). Následující obrázek znázorňuje pás karet.

![Řízení prostředků pásu karet knihovny MFC](../mfc/media/ribbon_no_callouts.png "Řízení prostředků pásu karet knihovny MFC")

V dřívějších verzích sady Visual Studio musely být vytvořeny pásy pásky psaním kódu, který používá třídy pásu karet knihovny MFC, jako je [třída CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). V sadě Visual Studio 2010 a novější, návrhář pásu karet poskytuje alternativní metodu pro vytváření pásů karet. Nejprve vytvořte a přizpůsobte pás karet jako prostředek. Potom načtěte prostředek pásu karet z kódu v aplikaci knihovny MFC. Můžete dokonce použít prostředky pásu karet a třídy pásu karet knihovny MFC společně. Můžete například vytvořit prostředek pásu karet a pak programově přidat další prvky za běhu pomocí kódu.

## <a name="understanding-the-ribbon-designer"></a>Principy Návrháře pásu karet

Návrhář pásu karet vytvoří a uloží pás karet jako prostředek. Když vytvoříte zdroj pásu karet, návrhář pásu karet udělá tyto tři věci:

- Přidá položku do skriptu definice zdroje projektu (*.rc). V následujícím příkladu je IDR_RIBBON jedinečný název, který identifikuje zdroj pásu karet, RT_RIBBON_XML je typ prostředku a pás karet.mfcribbon-ms je název souboru prostředků.

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Přidá definice ID příkazu do resource.h.

```
#define IDR_RIBBON            307
```

- Vytvoří soubor prostředků pásu karet (*.mfcribbon-ms), který obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy pásu karet. Změny pásu karet v návrháři pásu karet jsou uloženy v souboru prostředků jako XML. Následující příklad kódu ukazuje část obsahu \*souboru .mfcribbon-ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Chcete-li použít prostředek pásu karet v aplikaci knihovny MFC, načtěte jej voláním [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Vytvoření pásu karet pomocí Návrháře pásu karet

Toto jsou dva způsoby přidání zdroje pásu karet do projektu knihovny MFC:

- Vytvořte aplikaci knihovny MFC a nakonfigurujte Průvodce projektem knihovny MFC pro vytvoření pásu karet. Další informace naleznete [v tématu Návod: Vytvoření aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- V existujícím projektu knihovny MFC vytvořte zdroj pásu karet a načtěte jej. Další informace naleznete [v tématu Návod: Aktualizace aplikace MFC Klikyháky (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Pokud projekt již obsahuje ručně kódovaný pás karet, knihovna MFC má funkce, které můžete použít k převodu existujícího pásu karet na zdroj pásu karet. Další informace naleznete v [tématu Postup: Převod existujícího pásu karet knihovny MFC na zdroj pásu karet](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
> Pásové pásy nelze vytvořit v aplikacích založených na dialogu. Další informace naleznete v [tématu Typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Přizpůsobení pásů karet

Pokud chcete otevřít pás karet v návrháři pásu karet, poklikejte na zdroj pásu karet v zobrazení zdrojů. V návrháři můžete přidávat, odebírat a přizpůsobovat prvky na pásu karet, tlačítku Aplikace nebo na panelu nástrojů pro rychlý přístup. Můžete také propojit události, například události kliknutí na tlačítko a události nabídky, s metodou ve vaší aplikaci.

Následující obrázek znázorňuje různé součásti v návrháři pásu karet.

![Návrhář pásu karet knihovny MFC](../mfc/media/ribbon_designer.png "Návrhář pásu karet knihovny MFC")

- **Sada nástrojů:** Obsahuje ovládací prvky, které lze přetáhnout na povrch návrháře.

- **Návrhářský povrch:** Obsahuje vizuální reprezentaci prostředku pásu karet.

- ** [Průvodce třídou](reference/mfc-class-wizard.md):** Zobrazí seznam atributů položky vybrané na povrchu návrháře.

- **Okno Zobrazení zdrojů:** Zobrazí zdroje, které obsahují zdroje pásu karet v projektu.

- **Panel nástrojů Editor pásu karet:** Obsahuje příkazy, které umožňují zobrazit náhled pásu karet a změnit jeho vizuální motiv.

Následující témata popisují, jak používat funkce v návrháři pásu karet:

- [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)

- [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Postupy: Načtení prostředku pásu karet z aplikace MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definice prvků pásu karet

![Pás karet knihovny MFC](../mfc/media/ribbon.png "Pás karet knihovny MFC")

- **Tlačítko aplikace:** Tlačítko, které se zobrazí v levém horním rohu pásu karet. Tlačítko Aplikace nahradí nabídku Soubor a je viditelné i v případě, že je pás karet minimalizován. Po klepnutí na tlačítko se zobrazí nabídka se seznamem příkazů.

- **Panel nástrojů Rychlý přístup:** Malý přizpůsobitelný panel nástrojů, který zobrazuje často používané příkazy.

- **Kategorie**: Logické seskupení, které představuje obsah karty pásu karet.

- **Výchozí tlačítko kategorie:** Tlačítko, které se zobrazí na pásu karet při minimalizaci pásu karet. Po klepnutí na tlačítko se kategorie znovu zobrazí jako nabídka.

- **Panel:** Oblast panelu pásu karet, která zobrazuje skupinu souvisejících ovládacích prvků. Každá kategorie pásu karet obsahuje jeden nebo více panelů pásu karet.

- **Prvky pásu karet:** Ovládací prvky v panelech, například tlačítka a pole se seznamem. Různé ovládací prvky, které lze hostovat na pásu karet, najdete v [tématu Ukázka minimonik pásu karet: Aplikace miniaplikací na pásu karet](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)
