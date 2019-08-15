---
title: Návrhář pásu karet (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 1634eee30063a48041d60fc1b7116ca9543c9de2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511469"
---
# <a name="ribbon-designer-mfc"></a>Návrhář pásu karet (MFC)

Návrhář pásu karet umožňuje vytvořit a přizpůsobit pás karet v aplikacích knihovny MFC. Pás karet je prvek uživatelského rozhraní (UI), který slouží k uspořádání příkazů do logických skupin. Tyto skupiny se zobrazí na oddělených kartách v horní části okna. Pás karet nahrazuje panel nabídek a panely nástrojů. Pás karet může významně zlepšit použitelnost aplikace. Další informace najdete v tématu [pásy karet](/windows/win32/uxguide/cmd-ribbons). Na následujícím obrázku vidíte pás karet.

![Ovládací prvek prostředků pásu karet MFC](../mfc/media/ribbon_no_callouts.png "Ovládací prvek prostředků pásu karet MFC")

V dřívějších verzích sady Visual Studio bylo nutné vytvořit pásu karet psaním kódu, který používá třídy pásu karet MFC, jako je například [Třída CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). V aplikaci Visual Studio 2010 a novějších nabízí Návrhář pásu karet alternativní způsob vytváření pásu karet. Nejprve vytvořte a přizpůsobte pás karet jako prostředek. Pak načtěte prostředek pásu karet z kódu v aplikaci knihovny MFC. Můžete dokonce použít prostředky pásu karet a třídy pásu karet MFC dohromady. Můžete například vytvořit prostředek pásu karet a potom programově přidat více prvků za běhu pomocí kódu.

## <a name="understanding-the-ribbon-designer"></a>Princip Návrháře pásu karet

Návrhář pásu karet vytvoří a uloží pás karet jako prostředek. Při vytváření prostředku pásu karet provede Návrhář pásu karet tyto tři věci:

- Přidá položku do skriptu definice prostředků projektu (*. RC). V následujícím příkladu je IDR_RIBBON jedinečný název, který identifikuje prostředek pásu karet, RT_RIBBON_XML je typ prostředku a pás karet. mfcribbon-ms je název souboru prostředků.

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Přidá definice ID příkazů do Resource. h.

```
#define IDR_RIBBON            307
```

- Vytvoří soubor prostředků pásu karet (*. mfcribbon-ms), který obsahuje kód XML definující tlačítka, ovládací prvky a atributy pásu karet. Změny pásu karet v Návrháři pásu karet jsou uloženy v souboru prostředků jako XML. Následující příklad kódu ukazuje část obsahu \*souboru. mfcribbon-ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Chcete-li použít prostředek pásu karet v aplikaci knihovny MFC, načtěte prostředek voláním [CMFCRibbonBar:: LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Vytvoření pásu karet pomocí Návrháře pásu karet

Existují dva způsoby, jak přidat prostředek pásu karet do projektu knihovny MFC:

- Vytvořte aplikaci knihovny MFC a nakonfigurujte Průvodce projektem knihovny MFC pro vytvoření pásu karet. Další informace najdete v tématu [Návod: Vytvoření aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- V existujícím projektu knihovny MFC vytvořte prostředek pásu karet a načtěte jej. Další informace najdete v tématu [Návod: Aktualizuje se aplikace MFC Klikyháky (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Pokud má váš projekt již ručně kódovaný pás karet, knihovna MFC obsahuje funkce, které lze použít k převedení existujícího pásu karet na prostředek pásu karet. Další informace najdete v tématu [jak: Převede existující pás karet MFC na prostředek](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)pásu karet.

> [!NOTE]
>  Pásy karet nelze vytvořit v aplikacích založených na dialogových oknech. Další informace naleznete v tématu [Typ aplikace, Průvodce aplikací MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Přizpůsobení pásu karet

Pokud chcete v Návrháři pásu karet otevřít pás karet, poklikejte na prostředek pásu karet v Prostředky. V Návrháři můžete přidat, odebrat a přizpůsobit prvky na pásu karet, na tlačítku aplikace nebo na panelu nástrojů Rychlý přístup. Můžete také propojit události, například kliknout na události a události nabídky, na metodu ve vaší aplikaci.

Následující ilustrace znázorňuje různé komponenty v Návrháři pásu karet.

![Návrhář pásu karet MFC](../mfc/media/ribbon_designer.png "Návrhář pásu karet MFC")

- **Nástroj** Obsahuje ovládací prvky, které lze přetáhnout na plochu návrháře.

- **Plocha návrháře:** Obsahuje vizuální znázornění prostředku pásu karet.

- **Okno Vlastnosti:** Zobrazí seznam atributů položky, která je vybrána na návrhové ploše.

- **Prostředky okno:** Zobrazuje prostředky, které zahrnují prostředky pásu karet, v projektu.

- **Panel nástrojů editoru pásu karet:** Obsahuje příkazy, které umožňují zobrazit náhled pásu karet a měnit jeho vizuální motiv.

Následující témata popisují, jak používat funkce v Návrháři pásu karet:

- [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)

- [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Postupy: Načtení prostředku pásu karet z aplikace knihovny MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definice elementů pásu karet

![MFC Ribbon](../mfc/media/ribbon.png "MFC Ribbon")

- **Tlačítko aplikace:** Tlačítko, které se zobrazí v levém horním rohu pásu karet. Tlačítko aplikace nahradí nabídku soubor a je viditelné i v případě, že je pás karet minimalizován. Po kliknutí na tlačítko se zobrazí nabídka, která obsahuje seznam příkazů.

- **Panel nástrojů Rychlý přístup:** Malý přizpůsobitelný panel nástrojů, který zobrazuje často používané příkazy.

- **Kategorie**: Logické seskupení, které představuje obsah karty pásu karet.

- **Výchozí tlačítko Kategorie:** Tlačítko, které se zobrazí na pásu karet, když je minimalizován pás karet. Po kliknutí na tlačítko se kategorie znovu zobrazí jako nabídka.

- **Cestář** Oblast panelu pásu karet, která zobrazuje skupinu souvisejících ovládacích prvků. Každá kategorie pásu karet obsahuje jeden nebo více panelů pásu karet.

- **Prvky pásu karet:** Ovládací prvky v panelech, například tlačítka a pole se seznamem. Chcete-li zobrazit různé ovládací prvky, které lze hostovat na pásu karet [, přečtěte si část RibbonGadgets Sample: Aplikace](../overview/visual-cpp-samples.md)miniaplikace na pásu karet

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)
