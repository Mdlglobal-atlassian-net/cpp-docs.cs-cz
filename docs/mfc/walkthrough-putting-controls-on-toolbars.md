---
title: 'Návod: Umístění ovládacích prvků na panely nástrojů | Microsoft Docs'
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
ms.openlocfilehash: 45a04f81ee7419bdf45052f0f1f2746dd7866af8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957169"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Návod: Umístění ovládacích prvků na panely nástrojů
Toto téma popisuje, jak na panel nástrojů přidat tlačítko panelu nástrojů obsahující ovládací prvek systému Windows. V prostředí MFC, musí být tlačítka panelu nástrojů [CMFCToolBarButton – třída](../mfc/reference/cmfctoolbarbutton-class.md)-odvozené třídy, například [CMFCToolBarComboBoxButton třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton třída](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton třída](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), nebo [CMFCToolBarMenuButton třída](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## <a name="adding-controls-to-toolbars"></a>Přidávání ovládacích prvků na panely nástrojů  
 Chcete-li přidat ovládací prvek na panel nástrojů, postupujte takto:  
  
1.  Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů. Další informace o tom, jak vytvořit tlačítka pomocí editoru panelu nástrojů v sadě Visual Studio najdete v tématu [Editor panelu nástrojů](../windows/toolbar-editor.md) tématu.  
  
2.  Zarezervujte obrázek panelu nástrojů (ikonu tlačítka) pro tlačítko ve všech rastrových obrázcích nadřazeného panelu nástrojů.  
  
3.  V popisovač zpráv, který zpracovává zprávy AFX_WM_RESETTOOLBAR postupujte takto:  
  
    1.  Vytvořte ovládací prvek tlačítka pomocí odvozené třídy `CMFCToolbarButton`.  
  
    2.  Nahraďte zástupný tlačítko Nový ovládací prvek pomocí [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Objekt tlačítka lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.  
  
> [!NOTE]
>  Pokud jste povolili přizpůsobení v aplikaci, bude pravděpodobně nutné resetovat pomocí panelu nástrojů **resetovat** tlačítko **panely nástrojů** kartě **přizpůsobit** dialogovém okně najdete v článku aktualizovaný ovládací prvek v aplikaci po nutnosti rekompilace. Stav panelu nástrojů je uložen v registru systému Windows, přičemž informace registru jsou načítány a použity po spuštění metody `ReplaceButton` při spouštění aplikace.  
  
## <a name="toolbar-controls-and-customization"></a>Ovládací prvky a přizpůsobení panelu nástrojů  
 **Příkazy** kartě **přizpůsobit** dialogové okno obsahuje seznam příkazů, které jsou k dispozici v aplikaci. Ve výchozím nastavení **přizpůsobit** dialogové okno zpracovává nabídky aplikace a vytvoří seznam tlačítka na standardním panelu nástrojů v každé kategorii nabídky. Pokud chcete zachovat rozšířené funkce, které poskytují ovládací prvky panelu nástrojů, je potřeba nahradit na standardním panelu nástrojů tlačítko vlastního ovládacího prvku v **přizpůsobit** dialogové okno.  
  
 Když povolíte vlastní nastavení, můžete vytvořit **přizpůsobit** dialogovém okně obslužná rutina přizpůsobení `OnViewCustomize` pomocí [CMFCToolBarsCustomizeDialog třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md) – třída. Před zobrazením **přizpůsobit** dialogové okno voláním [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), volání [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) nahradit Standardní tlačítka s nový ovládací prvek.  
  
## <a name="example-creating-a-find-combo-box"></a>Příklad: Vytvoření pole se seznamem Find  
 Tato část popisuje postup vytvoření **najít** prvek pole se seznamem, který se zobrazí na panelu nástrojů a obsahuje nedávno použité hledání řetězců. Uživatel může do ovládacího prvku zadat řetězec a stisknutím klávesy Enter prohledat dokument, nebo stisknout klávesu Escape a vrátit fokus na hlavní rámec. Tento příklad předpokládá, že dokument je zobrazen v [CEditView třída](../mfc/reference/ceditview-class.md)-odvozené zobrazení.  
  
### <a name="creating-the-find-control"></a>Vytvoření ovládacího prvku Find  
 Nejprve vytvořte ovládací prvek pole se seznamem `Find`:  
  
1.  Přidejte tlačítko a jeho příkazy do prostředků aplikace:  
  
    1.  V prostředcích aplikace přidejte na panel nástrojů v aplikaci a ke všem rastrovým obrázkům přidruženým k panelu nástrojů nové tlačítko s identifikátorem příkazu `ID_EDIT_FIND`.  
  
    2.  Vytvořte novou položku nabídky s identifikátorem příkazu ID_EDIT_FIND.  
  
    3.  Do tabulky řetězců přidejte nový řetězec „Najít text\nNajít“ a přiřaďte k němu identifikátor příkazu `ID_EDIT_FIND_COMBO`. Tento identifikátor bude použit jako identifikátor příkazu tlačítka pole se seznamem `Find`.  
  
        > [!NOTE]
        >  Jelikož příkaz `ID_EDIT_FIND` je standardní příkaz zpracovávaný třídou `CEditView`, není nutné implementovat pro něj zvláštní obslužnou rutinu.  Obslužnou rutinu je však zapotřebí implementovat pro nový příkaz `ID_EDIT_FIND_COMBO`.  
  
2.  Vytvořte novou třídu, `CFindComboBox`, odvozené z [CComboBox – třída](../mfc/reference/ccombobox-class.md).  
  
3.  Ve třídě `CFindComboBox` přepište virtuální metodu `PreTranslateMessage`. Tato metoda vám umožní pole se seznamem ke zpracování [WM_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) zprávy. Stiskne-li uživatel klávesu Escape (`VK_ESCAPE`), vraťte fokus na okno hlavního rámce. Pokud uživatel dotkne klávesy Enter (`VK_ENTER`), post do hlavního rámce okna wm_command – zprávy, který obsahuje `ID_EDIT_FIND_COMBO` příkaz ID.  
  
4.  Vytvořte třídu **najít** tlačítko pole se seznamem, odvozené od [CMFCToolBarComboBoxButton třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). V tomto příkladu je pojmenována `CFindComboButton`.  
  
5.  Konstruktor třídy `CMFCToolbarComboBoxButton` přijímá tři parametry: identifikátor příkazu tlačítka, index obrázku tlačítka a styl pole se seznamem. Tyto parametry nastavte takto:  
  
    1.  Jako identifikátor příkazu předejte hodnotu `ID_EDIT_FIND_COMBO`.  
  
    2.  Použití [CCommandManager::GetCmdImage](http://msdn.microsoft.com/en-us/4094d08e-de74-4398-a483-76d27a742dca) s `ID_EDIT_FIND` získat index bitové kopie.  
  
    3.  Seznam dostupných pole se seznamem styly najdete v tématu [pole se seznamem styly](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
6.  Ve třídě `CFindComboButton` přepište metodu `CMFCToolbarComboBoxButton::CreateCombo`. Zde by měl být vytvořen objekt `CFindComboButton` a vrácen ukazatel na něj.  
  
7.  Použití [implement_serial –](../mfc/reference/run-time-object-model-services.md#implement_serial) makro aby tlačítko pole se seznamem trvalé. Správce pracovního prostoru automaticky načte a uloží stav tlačítka v registru systému Windows.  
  
8.  V aktuálním zobrazení dokumentu implementujte obslužnou rutinu příkazu `ID_EDIT_FIND_COMBO`. Použití [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) s `ID_EDIT_FIND_COMBO` načíst všechny **najít** tlačítka pole se seznamem. V důsledku přizpůsobení může existovat několik kopií tlačítka se stejným identifikátorem příkazu.  
  
9. V obslužné rutiny zpráv id_edit_find – `OnFind`, použijte [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) k určení, zda příkaz find byl odeslán z **najít** tlačítko pole se seznamem. Pokud ano, vyhledejte text a přidejte vyhledávací řetězec do pole se seznamem.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>Přidání ovládacího prvku Find na hlavní panel nástrojů  
 Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:  
  
1.  V hlavním okně rámce implementujte popisovač zprávy `AFX_WM_RESETTOOLBAR``OnToolbarReset`.  
  
    > [!NOTE]
    >  Rozhraní pošle tuto zprávu hlavnímu oknu rámce ve chvíli, kdy je panel nástrojů inicializován během spuštění aplikace, nebo kdy je panel nástrojů obnoven během přizpůsobení. V obou případech je potřeba nahradit na standardním panelu nástrojů tlačítko Vlastní **najít** tlačítko pole se seznamem.  
  
2.  V `AFX_WM_RESETTOOLBAR` obslužnou rutinu, zkontrolujte ID nástrojů, který je, *WPARAM* AFX_WM_RESETTOOLBAR zprávy. Pokud se rovná tohoto panelu nástrojů, který obsahuje ID panelu nástrojů **najít** tlačítko pole se seznamem, volání [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) nahradit **najít** tlačítko (to znamená, tlačítko s ID příkazu, který `ID_EDIT_FIND)` s `CFindComboButton` objektu.  
  
    > [!NOTE]
    >  Objekt `CFindComboBox` lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Přidání ovládacího prvku Find do dialogového okna Přizpůsobit  
 V obslužné rutině přizpůsobení `OnViewCustomize`, volání [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) nahradit **najít** tlačítko (to znamená, tlačítko s ID příkazu `ID_EDIT_FIND)` s `CFindComboButton` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../mfc/hierarchy-chart.md)   
 [Třídy](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton – třída](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton – třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog – třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
