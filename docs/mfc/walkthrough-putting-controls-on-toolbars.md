---
title: 'Návod: Vložení ovládacích prvků na panely nástrojů'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 0c62a8b484cb666427f873244221afec5d4719da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510736"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Návod: Vložení ovládacích prvků na panely nástrojů

Tento článek popisuje, jak přidat tlačítko panelu nástrojů, které obsahuje ovládací prvek Windows, na panel nástrojů. V knihovně MFC musí být tlačítko panelu nástrojů CMFCToolBarButton třídou odvozenou od [třídy](../mfc/reference/cmfctoolbarbutton-class.md), například třída [CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [Třída CMFCToolBarEditBoxButton](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)nebo [ Třída CMFCToolBarMenuButton](../mfc/reference/cmfctoolbarmenubutton-class.md)

## <a name="adding-controls-to-toolbars"></a>Přidávání ovládacích prvků na panely nástrojů

Chcete-li přidat ovládací prvek na panel nástrojů, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů. Další informace o tom, jak vytvořit tlačítka pomocí **editoru panelu nástrojů** v aplikaci Visual Studio, naleznete v článku [Editor panelu nástrojů](../windows/toolbar-editor.md) .

1. Zarezervujte obrázek panelu nástrojů (ikonu tlačítka) pro tlačítko ve všech rastrových obrázcích nadřazeného panelu nástrojů.

1. V obslužné rutině zprávy, která `AFX_WM_RESETTOOLBAR` zpracovává zprávu, proveďte následující kroky:

   1. Vytvořte ovládací prvek tlačítka pomocí odvozené třídy `CMFCToolbarButton`.

   1. Nahraďte zástupný tlačítko novým ovládacím prvkem pomocí [CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Objekt tlačítka lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.

> [!NOTE]
>  Pokud jste v aplikaci povolili vlastní nastavení, může být nutné resetovat panel nástrojů pomocí tlačítka **obnovit** na kartě **panely nástrojů** v dialogovém okně **přizpůsobit** , aby se po opětovné kompilaci zobrazil aktualizovaný ovládací prvek v aplikaci. Stav panelu nástrojů je uložen v registru systému Windows, přičemž informace registru jsou načítány a použity po spuštění metody `ReplaceButton` při spouštění aplikace.

## <a name="toolbar-controls-and-customization"></a>Ovládací prvky a přizpůsobení panelu nástrojů

Karta **příkazy** v dialogovém okně **přizpůsobit** obsahuje seznam příkazů, které jsou k dispozici v aplikaci. Ve výchozím nastavení dialogové okno **přizpůsobit** zpracuje nabídky aplikace a sestaví seznam standardních tlačítek panelu nástrojů v každé kategorii nabídky. Chcete-li mít rozšířené funkce, které ovládací prvek Toolbar poskytuje, je nutné nahradit standardní tlačítko panelu nástrojů vlastním ovládacím prvkem v dialogovém okně **přizpůsobit** .

Pokud povolíte přizpůsobení, vytvoříte dialogové okno **přizpůsobit** v obslužné rutině `OnViewCustomize` vlastního nastavení pomocí třídy [třídy CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md) . Než zobrazíte dialogové okno **přizpůsobit** voláním [CMFCToolBarsCustomizeDialog:: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), zavolejte [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) a nahraďte standardní tlačítko novým ovládacím prvkem.

## <a name="example-creating-a-find-combo-box"></a>Příklad: Vytvoření pole se seznamem najít

Tato část popisuje, jak vytvořit ovládací prvek pole se seznamem **Najít** , který se zobrazí na panelu nástrojů a obsahuje naposledy použité vyhledávací řetězce. Uživatel může do ovládacího prvku zadat řetězec a stisknutím klávesy Enter prohledat dokument, nebo stisknout klávesu Escape a vrátit fokus na hlavní rámec. V tomto příkladu se předpokládá, že se dokument zobrazuje v zobrazení odvozeném od [třídy CEditView](../mfc/reference/ceditview-class.md).

### <a name="creating-the-find-control"></a>Vytvoření ovládacího prvku Find

Nejprve vytvořte ovládací prvek pole se seznamem **Najít** :

1. Přidejte tlačítko a jeho příkazy do prostředků aplikace:

   1. V prostředcích aplikace přidejte na panel nástrojů v aplikaci a ke všem rastrovým obrázkům přidruženým k panelu nástrojů nové tlačítko s identifikátorem příkazu `ID_EDIT_FIND`.

   1. Vytvořte novou položku nabídky s `ID_EDIT_FIND` ID příkazu.

   1. Do tabulky řetězců přidejte nový řetězec „Najít text\nNajít“ a přiřaďte k němu identifikátor příkazu `ID_EDIT_FIND_COMBO`. Toto ID se použije jako ID příkazu pro tlačítko **Najít** pole se seznamem.

        > [!NOTE]
        > Jelikož příkaz `ID_EDIT_FIND` je standardní příkaz zpracovávaný třídou `CEditView`, není nutné implementovat pro něj zvláštní obslužnou rutinu.  Obslužnou rutinu je však zapotřebí implementovat pro nový příkaz `ID_EDIT_FIND_COMBO`.

1. Vytvořte novou třídu `CFindComboBox`odvozenou z [třídy CComboBox –](../mfc/reference/ccombobox-class.md).

1. Ve třídě `CFindComboBox` přepište virtuální metodu `PreTranslateMessage`. Tato metoda umožní, aby pole se seznamem zpracovával zprávu [WM_KEYDOWN](/windows/win32/inputdev/wm-keydown) . Stiskne-li uživatel klávesu Escape (`VK_ESCAPE`), vraťte fokus na okno hlavního rámce. Stiskne-li uživatel klávesu Enter (`VK_ENTER`), zašlete oknu hlavního rámce zprávu `WM_COMMAND` obsahující identifikátor příkazu `ID_EDIT_FIND_COMBO`.

1. Vytvořte třídu tlačítka **Najít** pole se seznamem odvozenou od [třídy CMFCToolbarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). V tomto příkladu je pojmenován `CFindComboButton`.

1. Konstruktor třídy `CMFCToolbarComboBoxButton` přijímá tři parametry: identifikátor příkazu tlačítka, index obrázku tlačítka a styl pole se seznamem. Tyto parametry nastavte takto:

   1. Jako identifikátor příkazu předejte hodnotu `ID_EDIT_FIND_COMBO`.

   1. K získání indexu obrázku použijte [CCommandManager:: GetCmdImage.](reference/internal-classes.md) `ID_EDIT_FIND`

   1. Seznam dostupných stylů pole se seznamem naleznete v tématu [styly polí se seznamem](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. Ve třídě `CFindComboButton` přepište metodu `CMFCToolbarComboBoxButton::CreateCombo`. Zde by měl být vytvořen objekt `CFindComboButton` a vrácen ukazatel na něj.

1. Použijte makro [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) , aby bylo tlačítko se seznamem trvalé. Správce pracovního prostoru automaticky načte a uloží stav tlačítka v registru systému Windows.

1. V aktuálním zobrazení dokumentu implementujte obslužnou rutinu příkazu `ID_EDIT_FIND_COMBO`. Pomocí [CMFCToolBar:: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) with `ID_EDIT_FIND_COMBO` načtěte všechna tlačítka **Najít** pole se seznamem. V důsledku přizpůsobení může existovat několik kopií tlačítka se stejným identifikátorem příkazu.

1. V obslužné rutině `OnFind` [](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) zprávy pomocí CMFCToolBar:: IsLastCommandFromButton určete, zda byl příkaz find odeslán z tlačítka Najít pole se seznamem. `ID_EDIT_FIND` Pokud ano, vyhledejte text a přidejte vyhledávací řetězec do pole se seznamem.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Přidání ovládacího prvku Find na hlavní panel nástrojů

Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:

1. V hlavním okně rámce implementujte popisovač zprávy `AFX_WM_RESETTOOLBAR``OnToolbarReset`.

    > [!NOTE]
    > Rozhraní pošle tuto zprávu hlavnímu oknu rámce ve chvíli, kdy je panel nástrojů inicializován během spuštění aplikace, nebo kdy je panel nástrojů obnoven během přizpůsobení. V obou případech je nutné nahradit standardní tlačítko panelu nástrojů vlastním tlačítkem **Najít** pole se seznamem.

1. V obslužné rutině prověřte ID panelu nástrojů, to znamená wParam zprávy AFX_WM_RESETTOOLBAR. `AFX_WM_RESETTOOLBAR` Pokud je ID panelu nástrojů rovno prvku panelu nástrojů, který obsahuje tlačítko **Najít** pole se seznamem, zavolejte [CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) a nahraďte tlačítko **find** (to znamená tlačítko s identifikátorem `ID_EDIT_FIND)` příkazu s `CFindComboButton` objektem.

    > [!NOTE]
    > Objekt `CFindComboBox` lze vytvořit v zásobníku, protože funkce `ReplaceButton` zkopíruje objekt tlačítka a tuto kopii udržuje.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Přidání ovládacího prvku Find do dialogového okna Přizpůsobit

V obslužné rutině `OnViewCustomize`přizpůsobení zavolejte [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) a nahraďte tlačítko **find** (to znamená tlačítko s identifikátorem `ID_EDIT_FIND`příkazu) s `CFindComboButton` objektem.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../mfc/hierarchy-chart.md)<br/>
[Třídy](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton – třída](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton – třída](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog – třída](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
