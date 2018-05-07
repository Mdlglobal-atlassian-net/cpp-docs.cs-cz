---
title: Pásu karet Návrhář (MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.editors.ribbon.F1
dev_langs:
- C++
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbde67e61a38190a2e26884659d273b55a63f89e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ribbon-designer-mfc"></a>Návrhář pásu karet (MFC)
Návrhář pásu karet umožňuje vytvářet a přizpůsobovat pásů karet v aplikacích MFC. Pásu karet je element rozhraní (UI) uživatele, který slouží k uspořádání příkazy do logických skupin. Tyto skupiny se zobrazí v samostatných záložkách v pruhu v horní části okna. Na pásu karet nahrazuje řádku nabídek a panelů nástrojů. Pásu karet může výrazně zlepšit použitelnost aplikací. Další informace najdete v tématu [pásů karet](http://go.microsoft.com/fwlink/p/?linkid=129233). Následující obrázek znázorňuje pásu karet.  
  
 ![Ovládací prvek prostředku pásu karet MFC](../mfc/media/ribbon_no_callouts.png "ribbon_no_callouts")  
  
 V dřívějších verzích sady Visual Studio, musel být vytvořen pomocí psaní kódu, který používá třídy pásu karet MFC jako pásů karet [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md). V [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], Návrhář pásu karet poskytuje alternativní metoda pro vytváření pásů karet. Nejprve vytvořte a přizpůsobení pásu karet jako prostředek. Pak můžete načtete prostředek pásu karet z kódu v aplikaci MFC. Dokonce můžete prostředky pásu karet a pásu karet MFC – třídy společně. Můžete například vytvořit prostředek pásu karet a potom prostřednictvím kódu programu další prvky k němu přidejte za běhu pomocí kódu.  
  
## <a name="understanding-the-ribbon-designer"></a>Principy Návrháře pásu karet  
 Návrhář pásu karet vytvoří a uloží jako prostředek pásu karet. Když vytvoříte prostředek pásu karet, Návrhář pásu karet provede tyto tři věci:  
  
-   Přidá položku do projektu skript definice prostředků (* .rc). V následujícím příkladu `IDR_RIBBON` je jedinečný název, který identifikuje prostředek pásu karet `RT_RIBBON_XML` je typ prostředku a `ribbon.mfcribbon-ms` je název souboru prostředků.  
  
 ```  
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"  
 ```  
  
-   Přidá do resource.h definice identifikátory příkazů.  
  
 ```  
 #define IDR_RIBBON            307  
 ```  
  
-   Vytvoří soubor prostředek pásu karet (*.mfcribbon-ms), který obsahuje kód XML, který definuje tlačítek na pásu karet, ovládací prvky a atributy. Změny na pásu karet v Návrháři pásu karet jsou uložené v souboru prostředků jako XML. Následující příklad kódu ukazuje část obsahu \*souborů .mfcribbon ms:  
  
 ```  
 <RIBBON_BAR>  
 <ELEMENT_NAME>RibbonBar</ELEMENT_NAME>  
 <IMAGE>  
 <ID>  
 <NAME>IDB_BUTTONS</NAME>  
 <VALUE>113</VALUE>  
 </ID>   
 ```  
  
 V aplikaci MFC použít prostředek pásu karet, načíst zdroj voláním [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).  
  
## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Vytvoření pásu karet pomocí Návrháře pásu karet  
 Tyto jsou dva způsoby, chcete-li přidat prostředek pásu karet do projektu MFC:  
  
-   Vytvoření aplikace knihovny MFC a nakonfigurovat v Průvodci projektem MFC vytvořit na pásu karet. Další informace najdete v tématu [návod: vytváření pásu karet aplikace podle pomocí MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).  
  
-   V existujícím projektu knihovny MFC vytvořte prostředek pásu karet a načíst. Další informace najdete v tématu [návod: aktualizace aplikace MFC Klikyháky (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
 Pokud váš projekt již má ručně programové pásu karet, MFC obsahuje funkce, které můžete použít převod existujícího pásu karet na prostředek pásu karet. Další informace najdete v tématu [postupy: převod existujícího pásu karet MFC na prostředek pásu karet](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).  
  
> [!NOTE]
>  Nelze vytvořit pásů karet v aplikacích založených na dialogové okno. Další informace najdete v tématu [typu aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="customizing-ribbons"></a>Přizpůsobení pásů karet  
 Chcete-li otevřít pásu karet v Návrháři pásu karet, dvakrát klikněte na prostředek pásu karet v zobrazení zdrojů. V Návrháři můžete přidat, odebrat a přizpůsobit prvky na pásu karet, tlačítko aplikace nebo panelu nástrojů Rychlý přístup. Můžete také propojit události, například kliknutí na tlačítko události a události nabídky Metoda ve vaší aplikaci.  
  
 Následující obrázek ukazuje různé součásti v Návrháři pásu karet.  
  
 ![Návrhář pásu karet MFC](../mfc/media/ribbon_designer.png "ribbon_designer")  
  
- **Sada nástrojů:** obsahuje ovládací prvky, které můžete přetáhnout na plochu návrháře.  
  
- **Plochu návrháře:** obsahuje vizuální reprezentace prostředek pásu karet.  
  
- **Vlastnosti – okno:** obsahuje seznam atributy položce vybrané na plochu návrháře.  
  
- **Okno zobrazení zdrojů:** zobrazuje prostředky, které zahrnují pásu karet prostředky ve vašem projektu.  
  
- **Panel nástrojů editoru pásu karet:** obsahuje příkazy, které vám umožní zobrazit náhled na pásu karet a změňte jeho visual motivu.  
  
 Následující témata popisují, jak používat funkce v Návrháři pásu karet:  
  
- [Postupy: Přizpůsobení tlačítka aplikace](../mfc/how-to-customize-the-application-button.md)  
  
- [Postupy: Přizpůsobení panelu nástrojů Rychlý přístup](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
- [Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)  
  
- [Postupy: Načtení prostředku pásu karet z aplikace MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)  
  
## <a name="definitions-of-ribbon-elements"></a>Definice elementů pásu karet  
 ![Pásu karet MFC](../mfc/media/ribbon.png "pásu karet")  
  
- **Tlačítko aplikace:** tlačítko, které se nachází v levém horním rohu pásu karet. Tlačítko aplikace nahrazuje v nabídce Soubor a je viditelný i v případě, že je minimalizovaná na pásu karet. Po kliknutí na tlačítko se zobrazí nabídka, která má seznam příkazů.  
  
- **Panel nástrojů Rychlý přístup:** malé, přizpůsobitelné panel nástrojů, který zobrazí často používané příkazy.  
  
- **Kategorie**: logické seskupení, která představuje obsah karty pásu karet.  
  
- **Výchozí tlačítko kategorie:** tlačítko, které se zobrazí na pásu karet, když je minimalizovaná na pásu karet. Při kliknutí na tlačítko kategorie se znovu zobrazí jako nabídky.  
  
- **Panely:** oblast panelu pásu karet, který zobrazuje skupinu souvisejících ovládacích prvků. Každé kategorie pásu karet obsahuje jeden nebo více panelů pásu karet.  
  
- **Prvky pásu karet:** ovládacích prvků do panelů, například tlačítka a pole se seznamem. Různé ovládacích prvků, které může být hostovaný na pásu karet najdete v tématu [RibbonGadgets ukázka: jednoduché aplikace pásu karet miniaplikacemi](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Práce se zdrojovými soubory](../windows/working-with-resource-files.md)

