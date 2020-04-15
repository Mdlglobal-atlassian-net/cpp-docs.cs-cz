---
title: 'Návod: Umístění ovládacích prvků na panely nástrojů'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 2a801e61c49301d9b8780bbf7eb77025990337ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360273"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Návod: Umístění ovládacích prvků na panely nástrojů

Tento článek popisuje, jak přidat tlačítko panelu nástrojů, který obsahuje ovládací prvek systému Windows na panelu nástrojů. V knihovně MFC musí být tlačítko panelu nástrojů [třídou třídy cmfcToolBarButton,](../mfc/reference/cmfctoolbarbutton-class.md)například [třídou CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [třídou CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md), [třídou CMFCDropDownToolbarButton](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)nebo [třídou CMFCToolBarMenuButton](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Přidávání ovládacích prvků na panely nástrojů

Chcete-li přidat ovládací prvek na panel nástrojů, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů. Další informace o vytváření tlačítek pomocí **Editoru panelů nástrojů** v sadě Visual Studio naleznete v článku [Editor panelů nástrojů.](../windows/toolbar-editor.md)

1. Zarezervujte obrázek panelu nástrojů (ikonu tlačítka) pro tlačítko ve všech rastrových obrázcích nadřazeného panelu nástrojů.

1. V obslužné `AFX_WM_RESETTOOLBAR` rutině zprávy, která zprávu zpracovává, proveďte následující kroky:

   1. Vytvořte ovládací prvek tlačítka pomocí odvozené třídy `CMFCToolbarButton`.

   1. Nahraďte tlačítko fiktivní ho za nový ovládací prvek pomocí [cmfctoolbar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Objekt tlačítka lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.

> [!NOTE]
> Pokud jste v aplikaci povolili přizpůsobení, bude pravděpodobně nutné obnovit panel nástrojů pomocí tlačítka **Obnovit** na kartě **Panely nástrojů** dialogového okna **Přizpůsobit,** abyste po opětovné kompilaci zoviděli aktualizovaný ovládací prvek v aplikaci. Stav panelu nástrojů je uložen v registru systému Windows, přičemž informace registru jsou načítány a použity po spuštění metody `ReplaceButton` při spouštění aplikace.

## <a name="toolbar-controls-and-customization"></a>Ovládací prvky a přizpůsobení panelu nástrojů

Karta **Příkazy** dialogového okna **Přizpůsobit** obsahuje seznam příkazů, které jsou k dispozici v aplikaci. Ve výchozím nastavení dialogové okno **Přizpůsobit** zpracovává nabídky aplikací a vytváří seznam standardních tlačítek panelu nástrojů v každé kategorii nabídek. Chcete-li zachovat rozšířené funkce, které ovládací prvky panelu nástrojů poskytují, je nutné nahradit standardní tlačítko panelu nástrojů vlastním ovládacím prvkem v dialogovém okně **Přizpůsobit.**

Když povolíte vlastní nastavení, vytvoříte dialogové `OnViewCustomize` okno **Přizpůsobit** v obslužné rutině přizpůsobení pomocí [třídy TŘÍDY CMFCToolBarsCustomizeDialog.](../mfc/reference/cmfctoolbarscustomizedialog-class.md) Před zobrazením dialogového okna **Přizpůsobit** voláním [cmfctoolbarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)volejte [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) a nahraďte standardní tlačítko novým ovládacím prvkem.

## <a name="example-creating-a-find-combo-box"></a>Příklad: Vytvoření pole se seznamem Find

Tato část popisuje, jak vytvořit ovládací prvek se seznamem **Najít,** který se zobrazí na panelu nástrojů a obsahuje naposledy použité vyhledávací řetězce. Uživatel může do ovládacího prvku zadat řetězec a stisknutím klávesy Enter prohledat dokument, nebo stisknout klávesu Escape a vrátit fokus na hlavní rámec. Tento příklad předpokládá, že dokument je zobrazen v zobrazení odvozené [cEditView třídy.](../mfc/reference/ceditview-class.md)

### <a name="creating-the-find-control"></a>Vytvoření ovládacího prvku Find

Nejprve vytvořte ovládací prvek pole se seznamem **Najít:**

1. Přidejte tlačítko a jeho příkazy do prostředků aplikace:

   1. V prostředcích aplikace přidejte na panel nástrojů v aplikaci a ke všem rastrovým obrázkům přidruženým k panelu nástrojů nové tlačítko s identifikátorem příkazu `ID_EDIT_FIND`.

   1. Vytvořte novou položku `ID_EDIT_FIND` nabídky s ID příkazu.

   1. Do tabulky řetězců přidejte nový řetězec „Najít text\nNajít“ a přiřaďte k němu identifikátor příkazu `ID_EDIT_FIND_COMBO`. Toto ID se použije jako ID příkazu tlačítka pole se seznamem **Najít.**

        > [!NOTE]
        > Jelikož příkaz `ID_EDIT_FIND` je standardní příkaz zpracovávaný třídou `CEditView`, není nutné implementovat pro něj zvláštní obslužnou rutinu.  Obslužnou rutinu je však zapotřebí implementovat pro nový příkaz `ID_EDIT_FIND_COMBO`.

1. Vytvořte novou `CFindComboBox`třídu , odvozenou z [třídy CComboBox](../mfc/reference/ccombobox-class.md).

1. Ve třídě `CFindComboBox` přepište virtuální metodu `PreTranslateMessage`. Tato metoda umožní pole se seznamem ke zpracování [zprávy WM_KEYDOWN.](/windows/win32/inputdev/wm-keydown) Stiskne-li uživatel klávesu Escape (`VK_ESCAPE`), vraťte fokus na okno hlavního rámce. Stiskne-li uživatel klávesu Enter (`VK_ENTER`), zašlete oknu hlavního rámce zprávu `WM_COMMAND` obsahující identifikátor příkazu `ID_EDIT_FIND_COMBO`.

1. Vytvořte třídu pro tlačítko pole se seznamem **Najít,** odvozené z [třídy CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). V tomto příkladu je `CFindComboButton`pojmenován .

1. Konstruktor třídy `CMFCToolbarComboBoxButton` přijímá tři parametry: identifikátor příkazu tlačítka, index obrázku tlačítka a styl pole se seznamem. Tyto parametry nastavte takto:

   1. Jako identifikátor příkazu předejte hodnotu `ID_EDIT_FIND_COMBO`.

   1. Použijte [CCommandManager::GetCmdImage](reference/internal-classes.md) s `ID_EDIT_FIND` získat index obrazu.

   1. Seznam dostupných stylů polí se seznamem naleznete v [tématu Styly se seznamem](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. Ve třídě `CFindComboButton` přepište metodu `CMFCToolbarComboBoxButton::CreateCombo`. Zde by měl být vytvořen objekt `CFindComboButton` a vrácen ukazatel na něj.

1. Pomocí [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) makru můžete vytvořit trvalé tlačítko combo. Správce pracovního prostoru automaticky načte a uloží stav tlačítka v registru systému Windows.

1. V aktuálním zobrazení dokumentu implementujte obslužnou rutinu příkazu `ID_EDIT_FIND_COMBO`. Pomocí [tlačítka CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) s `ID_EDIT_FIND_COMBO` načíst všechny **najít** pole se seznamem tlačítka. V důsledku přizpůsobení může existovat několik kopií tlačítka se stejným identifikátorem příkazu.

1. V `ID_EDIT_FIND` obslužné `OnFind`rutině zprávy použijte [příkaz CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) k určení, zda byl příkaz find odeslán z pole **Najít** pole se seznamem. Pokud ano, vyhledejte text a přidejte vyhledávací řetězec do pole se seznamem.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Přidání ovládacího prvku Find na hlavní panel nástrojů

Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:

1. V hlavním okně rámce implementujte popisovač zprávy `AFX_WM_RESETTOOLBAR``OnToolbarReset`.

    > [!NOTE]
    > Rozhraní pošle tuto zprávu hlavnímu oknu rámce ve chvíli, kdy je panel nástrojů inicializován během spuštění aplikace, nebo kdy je panel nástrojů obnoven během přizpůsobení. V obou případech je nutné nahradit standardní tlačítko panelu nástrojů vlastním tlačítkem pole se seznamem **Najít.**

1. V `AFX_WM_RESETTOOLBAR` obslužné rutině zkontrolujte ID panelu nástrojů, to znamená *WPARAM* zprávy AFX_WM_RESETTOOLBAR. Pokud je ID panelu nástrojů rovno ivi. **Find** [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) **Find** `ID_EDIT_FIND)` `CFindComboButton`

    > [!NOTE]
    > Objekt `CFindComboBox` lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Přidání ovládacího prvku Find do dialogového okna Přizpůsobit

V obslužné `OnViewCustomize`rutině přizpůsobení volejte [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) a nahradí tlačítko `ID_EDIT_FIND` **Najít** (tj. tlačítko id příkazu) objektem. `CFindComboButton`

## <a name="see-also"></a>Viz také

[Graf hierarchie](../mfc/hierarchy-chart.md)<br/>
[Třídy](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../mfc/reference/cmfctoolbar-class.md)<br/>
[Třída CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Třída CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog – třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
