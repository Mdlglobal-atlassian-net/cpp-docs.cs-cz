---
title: Návrhář pásu karet (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 5740b2f93f451a74407483c98ce5bf547b79bf35
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769482"
---
# <a name="ribbon-designer-mfc"></a>Návrhář pásu karet (MFC)

Návrhář pásu karet umožňuje vytvořit a upravit pásy karet v aplikacích MFC. Pás karet je prvek uživatelského rozhraní (UI), který umožňuje uspořádat příkazy do logických skupin. Tyto skupiny se zobrazí v samostatných kartách v pruhu v horní části okna. Pás karet nahrazuje nabídky a panely nástrojů. Pás karet může výrazně zlepšit použitelnost aplikace. Další informace najdete v tématu [pásů karet](/windows/desktop/uxguide/cmd-ribbons). Následující ilustrace znázorňuje pás karet.

![Ovládací prvek prostředku pásu karet MFC](../mfc/media/ribbon_no_callouts.png "ovládacího prvku prostředku pásu karet MFC")

V dřívějších verzích sady Visual Studio musel být karet vytvořen napsáním kódu, který používá třídy pásu karet MFC jako [CMFCRibbonBar – třída](../mfc/reference/cmfcribbonbar-class.md). V sadě Visual Studio 2010 a novější poskytuje Návrhář pásu karet alternativní metodu pro vytváření pásů karet. Nejprve vytvořte a přizpůsobte pás karet jako prostředek. Pak načtení prostředku pásu karet z kódu v aplikaci knihovny MFC. Dokonce můžete prostředky z pásu karet a třídy pásu karet MFC dohromady. Můžete například vytvořit prostředek pásu karet a potom programově přidat další prvky k němu za běhu pomocí kódu.

## <a name="understanding-the-ribbon-designer"></a>Principy Návrháře pásu karet

Návrhář pásu karet vytvoří a uloží pás karet jako prostředek. Při vytváření prostředku pásu karet nemá Návrhář pásu karet tyto tři věci:

- Přidá položku do skriptu definic prostředků projektu (* .rc). V následujícím příkladu IDR_RIBBON je jedinečný název, který identifikuje prostředek pásu karet, RT_RIBBON_XML je typ prostředku a ribbon.mfcribbon ms je název souboru prostředků.

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Přidá definice ID příkazů do souboru resource.h.

```
#define IDR_RIBBON            307
```

- Vytvoří soubor prostředků pásu karet (*.mfcribbon-ms), která obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy na pásu karet. Změny pásu karet v Návrháři pásu karet jsou uloženy v souboru prostředků ve formátu XML. Následující příklad kódu ukazuje část obsahu \*souboru .mfcribbon ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Chcete-li použít prostředky pásu karet v aplikaci knihovny MFC, načtěte prostředek voláním [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Vytvoření pásu karet pomocí Návrháře pásu karet

Toto jsou dva způsoby, jak přidat prostředek pásu karet do projektu knihovny MFC:

- Vytvoření aplikace knihovny MFC a konfigurace Průvodce projektu knihovny MFC vytvořte pás karet. Další informace najdete v tématu [názorný postup: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- V existujícím projektu knihovny MFC vytvořte prostředek pásu karet a načtěte jej. Další informace najdete v tématu [názorný postup: Aktualizace aplikace MFC Scribble (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Pokud váš projekt již má ručně kódovaný pás, knihovna MFC má funkce, které můžete použít pro převod existujícího pásu karet na prostředek pásu karet. Další informace najdete v tématu [jak: Převod existujícího pásu karet MFC na prostředek pásu karet](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
>  Pásy karet nelze v aplikacích založených na dialogové okno. Další informace najdete v tématu [typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Přizpůsobení pásů karet

Chcete-li otevřít pás karet v Návrháři pásu karet, dvakrát klikněte na prostředek pásu karet v okně zobrazení prostředků. V Návrháři můžete přidat, odebrat a přizpůsobit prvky na pásu karet, tlačítku aplikace nebo panelu nástrojů Rychlý přístup. Můžete také propojit události, například kliknutí na tlačítko události a události nabídky na metodu v aplikaci.

Následující obrázek znázorňuje různé součásti v Návrháři pásu karet.

![Návrhář pásu karet MFC](../mfc/media/ribbon_designer.png "Návrháře pásu karet MFC")

- **Panel nástrojů:** Obsahuje ovládací prvky, které lze přetáhnout do návrhové ploše.

- **Povrch návrháře:** Obsahuje vizuální reprezentaci prostředků pásu karet.

- **Okno Vlastnosti:** Seznam atributů položky vybrané na návrhové ploše.

- **Okno zobrazení zdrojů:** Zobrazí prostředky, které obsahují prostředky z pásu karet, ve vašem projektu.

- **Panel nástrojů editoru pásu karet:** Obsahuje příkazy, které umožňují zobrazit náhled pásu karet a změnit jeho vizuální motiv.

Následující témata popisují, jak používat funkce v Návrháři pásu karet:

- [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)

- [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Postupy: Načtení prostředku pásu karet z aplikace knihovny MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definice prvků pásu karet

![MFC Ribbon](../mfc/media/ribbon.png "MFC Ribbon")

- **Tlačítko aplikace:** Tlačítko, které se zobrazí v levém horním rohu pásu karet. Tlačítko aplikace nahrazuje nabídku Soubor a je viditelný i v případě, že je pás karet minimalizovaný. Po kliknutí na tlačítko se zobrazí nabídka, která obsahuje seznam příkazů.

- **Panel nástrojů Rychlý přístup:** Malý a přizpůsobitelný panel nástrojů, který zobrazuje často používané příkazy.

- **Kategorie**: Logické seskupení, který představuje obsah karty pásu karet.

- **Výchozí tlačítko kategorie:** Tlačítko, které se zobrazí na pásu karet, když je minimalizovaný. Po kliknutí na tlačítko kategorie se zobrazí znovu jako nabídka.

- **Panel:** Oblast na pásu karet, který se zobrazuje skupina souvisejících ovládacích prvků. Každá kategorie pásu karet obsahuje jeden nebo více panelů pásu karet.

- **Prvky pásu karet:** Ovládací prvky na panelech, například tlačítka a pole se seznamem. Různé ovládací prvky, které mohou být hostovány na pásu karet najdete v tématu [vzorek RibbonGadgets: Aplikace pro miniaplikace na pásu karet](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)
