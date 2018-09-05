---
title: 'Návod: Umístění ovládacích prvků na panely nástrojů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 258d8f10238db58be26743694943ae3bd6abc20e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693572"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Návod: Umístění ovládacích prvků na panely nástrojů
Toto téma popisuje, jak na panel nástrojů přidat tlačítko panelu nástrojů obsahující ovládací prvek systému Windows. V knihovně MFC, musí být tlačítko panelu nástrojů [cmfctoolbarbutton – třída](../mfc/reference/cmfctoolbarbutton-class.md)-odvozené třídy, například [cmfctoolbarcomboboxbutton – třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [cmfctoolbareditboxbutton – třída](../mfc/reference/cmfctoolbareditboxbutton-class.md), [Cmfcdropdowntoolbarbutton – třída](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), nebo [cmfctoolbarmenubutton – třída](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## <a name="adding-controls-to-toolbars"></a>Přidávání ovládacích prvků na panely nástrojů  
 Chcete-li přidat ovládací prvek na panel nástrojů, postupujte takto:  
  
1.  Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů. Další informace o tom, jak vytváření tlačítek pomocí editoru panelu nástrojů v sadě Visual Studio, najdete v článku [panelu nástrojů editoru](../windows/toolbar-editor.md) tématu.  
  
2.  Zarezervujte obrázek panelu nástrojů (ikonu tlačítka) pro tlačítko ve všech rastrových obrázcích nadřazeného panelu nástrojů.  
  
3.  V popisovači zpráv, která zpracovává zprávu AFX_WM_RESETTOOLBAR postupujte takto:  
  
    1.  Vytvořte ovládací prvek tlačítka pomocí odvozené třídy `CMFCToolbarButton`.  
  
    2.  Nahraďte zástupné tlačítko novým ovládacím prvkem pomocí [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Objekt tlačítka lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.  
  
> [!NOTE]
>  Pokud ve vaší aplikaci povoleno přizpůsobování, bude pravděpodobně nutné resetovat pomocí panelu nástrojů **resetování** tlačítko **panely nástrojů** karty **vlastní** dialogové okno najdete v článku aktualizovaný ovládací prvek ve vaší aplikaci po opětovné kompilaci. Stav panelu nástrojů je uložen v registru systému Windows, přičemž informace registru jsou načítány a použity po spuštění metody `ReplaceButton` při spouštění aplikace.  
  
## <a name="toolbar-controls-and-customization"></a>Ovládací prvky a přizpůsobení panelu nástrojů  
 **Příkazy** karty **vlastní** dialogové okno obsahuje seznam příkazů, které jsou k dispozici v aplikaci. Ve výchozím nastavení **vlastní** dialogové okno zpracovává nabídky aplikace a sestavuje seznam standardních tlačítek panelu nástrojů v každé kategorii nabídky. Chcete-li zachovat rozšířené funkce, které poskytují ovládací prvky panelu nástrojů, je potřeba nahradit standardní tlačítko panelu nástrojů na vlastní ovládací prvky **vlastní** dialogové okno.  
  
 Po povolení přizpůsobení vytvoříte **vlastní** dialogové okno v obslužné rutině přizpůsobení `OnViewCustomize` pomocí [cmfctoolbarscustomizedialog – třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md) třídy. Před zobrazením **vlastní** dialogové okno voláním [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), volání [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) k nahrazení standardní tlačítko s nový ovládací prvek.  
  
## <a name="example-creating-a-find-combo-box"></a>Příklad: Vytvoření pole se seznamem Find  
 Tato část popisuje, jak vytvořit **najít** prvek pole se seznamem, který se zobrazí na panelu nástrojů a obsahuje naposled použité vyhledávací řetězce. Uživatel může do ovládacího prvku zadat řetězec a stisknutím klávesy Enter prohledat dokument, nebo stisknout klávesu Escape a vrátit fokus na hlavní rámec. Tento příklad předpokládá, že dokument je zobrazen v [třídy CEditView](../mfc/reference/ceditview-class.md)– zobrazení odvozeném z třídy.  
  
### <a name="creating-the-find-control"></a>Vytvoření ovládacího prvku Find  
 Nejprve vytvořte ovládací prvek pole se seznamem `Find`:  
  
1.  Přidejte tlačítko a jeho příkazy do prostředků aplikace:  
  
    1.  V prostředcích aplikace přidejte na panel nástrojů v aplikaci a ke všem rastrovým obrázkům přidruženým k panelu nástrojů nové tlačítko s identifikátorem příkazu `ID_EDIT_FIND`.  
  
    2.  Vytvořte novou položku nabídky s identifikátorem příkazu ID_EDIT_FIND.  
  
    3.  Do tabulky řetězců přidejte nový řetězec „Najít text\nNajít“ a přiřaďte k němu identifikátor příkazu `ID_EDIT_FIND_COMBO`. Tento identifikátor bude použit jako identifikátor příkazu tlačítka pole se seznamem `Find`.  
  
        > [!NOTE]
        >  Jelikož příkaz `ID_EDIT_FIND` je standardní příkaz zpracovávaný třídou `CEditView`, není nutné implementovat pro něj zvláštní obslužnou rutinu.  Obslužnou rutinu je však zapotřebí implementovat pro nový příkaz `ID_EDIT_FIND_COMBO`.  
  
2.  Vytvořte novou třídu, `CFindComboBox`odvozenou z [CComboBox – třída](../mfc/reference/ccombobox-class.md).  
  
3.  Ve třídě `CFindComboBox` přepište virtuální metodu `PreTranslateMessage`. Tato metoda umožní poli se seznamem zpracovávat [WM_KEYDOWN](/windows/desktop/inputdev/wm-keydown) zprávy. Stiskne-li uživatel klávesu Escape (`VK_ESCAPE`), vraťte fokus na okno hlavního rámce. Pokud uživatel stiskne klávesu Enter (`VK_ENTER`), publikuje do okna hlavního rámce wm_command – zpráva, která obsahuje `ID_EDIT_FIND_COMBO` Apple ID.  
  
4.  Vytvořte třídu pro **najít** tlačítko pole se seznamem, odvozený z [cmfctoolbarcomboboxbutton – třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). V tomto příkladu je pojmenována `CFindComboButton`.  
  
5.  Konstruktor třídy `CMFCToolbarComboBoxButton` přijímá tři parametry: identifikátor příkazu tlačítka, index obrázku tlačítka a styl pole se seznamem. Tyto parametry nastavte takto:  
  
    1.  Jako identifikátor příkazu předejte hodnotu `ID_EDIT_FIND_COMBO`.  
  
    2.  Použití [CCommandManager::GetCmdImage](reference/internal-classes.md) s `ID_EDIT_FIND` získat index bitové kopie.  
  
    3.  Seznam dostupných – pole se seznamem styly najdete v tématu [pole se seznamem stylů](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
6.  Ve třídě `CFindComboButton` přepište metodu `CMFCToolbarComboBoxButton::CreateCombo`. Zde by měl být vytvořen objekt `CFindComboButton` a vrácen ukazatel na něj.  
  
7.  Použití [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) – makro k zajištění trvalosti tlačítko pole se seznamem. Správce pracovního prostoru automaticky načte a uloží stav tlačítka v registru systému Windows.  
  
8.  V aktuálním zobrazení dokumentu implementujte obslužnou rutinu příkazu `ID_EDIT_FIND_COMBO`. Použití [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) s `ID_EDIT_FIND_COMBO` chcete načíst všechny **najít** tlačítka pole se seznamem. V důsledku přizpůsobení může existovat několik kopií tlačítka se stejným identifikátorem příkazu.  
  
9. V popisovači zprávy ID_EDIT_FIND `OnFind`, použijte [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) k určení, zda příkaz k vyhledávání byla odeslána z **najít** tlačítko pole se seznamem. Pokud ano, vyhledejte text a přidejte vyhledávací řetězec do pole se seznamem.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>Přidání ovládacího prvku Find na hlavní panel nástrojů  
 Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:  
  
1.  V hlavním okně rámce implementujte popisovač zprávy `AFX_WM_RESETTOOLBAR``OnToolbarReset`.  
  
    > [!NOTE]
    >  Rozhraní pošle tuto zprávu hlavnímu oknu rámce ve chvíli, kdy je panel nástrojů inicializován během spuštění aplikace, nebo kdy je panel nástrojů obnoven během přizpůsobení. V obou případech je zapotřebí nahradit standardní tlačítko Vlastní **najít** tlačítko pole se seznamem.  
  
2.  V `AFX_WM_RESETTOOLBAR` obslužnou rutinu, zkontrolujte Identifikátor panelu nástrojů, to znamená, *WPARAM* AFX_WM_RESETTOOLBAR zprávy. Je-li Identifikátor panelu nástrojů roven panelu nástrojů, který obsahuje **najít** tlačítko pole se seznamem, volání [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) nahradit **najít** tlačítko (to znamená tlačítko s Identifikátorem příkazu `ID_EDIT_FIND)` s `CFindComboButton` objektu.  
  
    > [!NOTE]
    >  Objekt `CFindComboBox` lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Přidání ovládacího prvku Find do dialogového okna Přizpůsobit  
 V obslužné rutině přizpůsobení `OnViewCustomize`, volání [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) nahradit **najít** tlačítko (tj. tlačítko s Identifikátorem příkazu `ID_EDIT_FIND)` s `CFindComboButton` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../mfc/hierarchy-chart.md)   
 [Třídy](../mfc/reference/mfc-classes.md)   
 [Cmfctoolbar – třída](../mfc/reference/cmfctoolbar-class.md)   
 [Cmfctoolbarbutton – třída](../mfc/reference/cmfctoolbarbutton-class.md)   
 [Cmfctoolbarcomboboxbutton – třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog – třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
