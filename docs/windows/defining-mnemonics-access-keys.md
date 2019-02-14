---
title: Definování řízení přístupu a hodnoty
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 3a885ad57ba05304d51cb45d0b498d81ad37a148
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264852"
---
# <a name="defining-control-access-and-values"></a>Definování řízení přístupu a hodnoty

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="change-the-tab-order-of-controls"></a>Změna pořadí ovládacích prvků

Pořadí, ve kterém je pořadí **kartu** klíč přesune zaměření pro vstup z jednoho ovládacího prvku v rámci dialogového okna. Obvykle pokračuje pořadí zleva doprava a shora dolů v dialogovém okně. Každý ovládací prvek má **Tabstop** vlastnost, která určuje, zda ovládací prvek nastaven vstupní fokus.

### <a name="to-set-input-focus-for-a-control"></a>Chcete-li nastavit fokus vstupu pro ovládací prvek

V [okno vlastností](/visualstudio/ide/reference/properties-window)vyberte **True** nebo **False** v **Tabstop** vlastnost.

Dokonce i ovládací prvky, které nemají **Tabstop** nastavenou na **True** musí být součástí pořadí ovládacích prvků. Pořadí je důležité, například, když jste [definujte přístupové klíče (klávesových zkratek)](../windows/defining-mnemonics-access-keys.md) pro ovládací prvky, které nemají titulky. Statický text, který obsahuje přístupový klíč pro související ovládací prvek musí bezprostředně předcházet související ovládací prvek v pořadí.

> [!NOTE]
> Pokud vaše dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob, jakým se zobrazí ovládací prvky. Ovládací prvky, které jsou dále v pořadí karet se vždy zobrazují nad překrývající se ovládací prvky, které předcházet v pořadí.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li zobrazit aktuální pořadí pro všechny ovládací prvky v dialogovém okně

Na **formátu** nabídce vyberte možnost **pořadí**.

\- nebo –

- Stisknutím klávesy **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li změnit pořadí ovládacích prvků pro všechny ovládací prvky v dialogovém okně

1. Na **formátu** nabídce vyberte možnost **pořadí**.

   Řadu každý ovládací prvek v levém horním rohu se zobrazí místo něj v aktuální pořadí.

1. Nastavení pořadí karet klikněte na každý prvek v pořadí, které chcete **kartu** klíč použít.

1. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

   > [!TIP]
   > Jakmile zadáte **pořadí** režimu, můžete stisknout **Esc** nebo **Enter** zakázat možnost změnit pořadí ovládacích prvků.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Chcete-li změnit pořadí pro dva nebo více ovládacích prvků

1. Z **formátu** nabídce zvolte **pořadí**.

1. Zadejte, kde se začne změna v pořadí. Podržte stisknutou klávesu nejprve **Ctrl** klíče a vyberte ovládací prvek a pak vyberte ten, kde chcete začít změněné směr.

   Například, pokud chcete změnit pořadí ovládacích prvků `7` prostřednictvím `9`, podržte stisknutou klávesu **Ctrl**, vyberte ovládací prvek `6` první.

   > [!NOTE]
   > Chcete-li nastavit konkrétní ovládací prvek na číslo `1` (první v pořadí), poklepejte na ovládací prvek.

1. Verze **Ctrl** klíče a potom vyberte ovládací prvky v pořadí, které chcete **kartu** klíč dodržovat od tohoto okamžiku.

1. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

## <a name="define-mnemonics-access-keys"></a>Definice klávesových zkratek (přístupové klávesy)

Za normálních okolností uživatelé klávesnice Přesun zaměření pro vstup z jednoho ovládacího prvku do druhého v dialogovém okně s **kartu** a **šipku** klíče. Ale můžete definovat přístupovou klávesu (název mnemonická nebo snadno zapamatovat), který umožňuje uživatelům vybrat ovládací prvek stisknutím klávesy jeden klíč.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek titulkem viditelné (tlačítka, zaškrtávací políčka a přepínačů)

1. Vyberte ovládací prvek v dialogovém okně.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **titulek** vlastnost, zadejte nový název pro ovládací prvek psaní znak ampersand (`&`) před písmeno jako přístupový klíč pro tento ovládací prvek. Například, `&Radio1`.

3. Stisknutím klávesy **zadejte**.

   Podtržení se zobrazí v zobrazení titulku udávajících přístupový klíč, například **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek bez zobrazen titulek

1. Provádění dotazů pomocí popisek pro ovládací prvek **statický Text** v ovládacím prvku [nástrojů](/visualstudio/ide/reference/toolbox).

2. Statický text titulku, zadejte znak ampersand (`&`) před písmeno jako přístupový klíč.

3. Ujistěte se, že ovládací prvek statického textu bezprostředně předchází ovládací prvek, který ho popisky v pořadí.

Přístupové klíče v rámci dialogového okna musí být jedinečné.

### <a name="to-check-for-duplicate-access-keys"></a>Hledat duplicitní přístupové klávesy

1. Na **formátu** nabídky, klikněte na tlačítko **zkontrolujte klávesových zkratek**.

## <a name="add-values-to-a-combo-box-control"></a>Přidání hodnot do ovládacího prvku pole se seznamem

Můžete přidat hodnoty do ovládacího prvku pole se seznamem za předpokladu, že máte **dialogové okno** editoru otevřít.

> [!TIP]
> Je vhodné přidat všechny hodnoty do pole se seznamem *před* velikost pole **dialogové okno** editoru, nebo může zkrátit text, který by se měla zobrazit v ovládacím prvku pole se seznamem.

### <a name="to-enter-values-into-a-combo-box-control"></a>Zadejte hodnoty do ovládacího prvku pole se seznamem

1. Vyberte ovládací prvek pole se seznamem kliknutím na ni.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), přejděte dolů k položce **Data** vlastnost.

   > [!NOTE]
   > Chcete-li zobrazit vlastnosti seskupené podle typu, **Data** se zobrazí v **různé** vlastnosti.

1. Vyberte oblast hodnoty pro **Data** vlastnost a zadejte hodnoty dat, oddělené středníky.

   > [!NOTE]
   > Neumisťujte mezery mezi hodnotami, protože prostory narušit podle abecedy v rozevíracím seznamu.

1. Stisknutím klávesy **Enter** po dokončení přidávání hodnot.

Informace o zvětšení rozevírací část pole se seznamem, naleznete v tématu [nastavení velikosti pole se seznamem a jeho rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Nelze přidat hodnoty k použití tohoto postupu projekty Win32 ( **Data** vlastnost je zobrazena šedě pro projekty Win32). Projekty Win32 knihovny, které přidat tuto funkci nemají, je nutné přidat hodnoty pole se seznamem se projekt Win32 prostřednictvím kódu programu.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>K otestování výskytu hodnoty v poli se seznamem

Po zadání hodnoty v **Data** vlastnosti, vyberte **testovací** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Zkuste Posun směrem dolů seznamem celá hodnota. Hodnoty se zobrazí přesně tak, jak jsou zadány v **Data** vlastnost **vlastnosti** okna. Neexistuje žádné pravopisné nebo kontrola malá a velká písmena.

   Stisknutím klávesy **Esc** se vrátíte **dialogové okno** editoru.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)