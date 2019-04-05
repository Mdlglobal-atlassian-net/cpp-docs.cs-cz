---
title: 'Postupy: Definování řízení přístupu a hodnoty (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: c49913597f51ef231073b89d60ad9718b1113f44
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041481"
---
# <a name="how-to-define-control-access-and-values-c"></a>Postupy: Definování řízení přístupu a hodnoty (C++)

## <a name="tab-order"></a>Pořadí karet

Pořadí, ve kterém je pořadí **kartu** klíč přesune zaměření pro vstup z jednoho ovládacího prvku v rámci dialogového okna. Obvykle pokračuje pořadí zleva doprava a shora dolů v dialogovém okně. Každý ovládací prvek má **Tabstop** vlastnost, která určuje, zda ovládací prvek nastaven vstupní fokus.

- V nastavení vstupní fokus pro ovládací prvek, [okno vlastností](/visualstudio/ide/reference/properties-window)vyberte **True** nebo **False** v **Tabstop** vlastnost.

Dokonce i ovládací prvky, které nemají **Tabstop** vlastnost nastavena na hodnotu **True** musí být součástí pořadí ovládacích prvků, zejména pro ovládací prvky, které nemají titulky. Statický text, který obsahuje přístupový klíč pro související ovládací prvek musí bezprostředně předcházet související ovládací prvek v pořadí.

> [!NOTE]
> Pokud vaše dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob, jakým se zobrazí ovládací prvky. Ovládací prvky, které jsou dále v pořadí karet se vždy zobrazují nad překrývající se ovládací prvky, které předcházet v pořadí.

- Chcete-li zobrazit aktuální pořadí pro všechny ovládací prvky, přejděte do nabídky **formátu** > **pořadí**, nebo stiskněte klávesu **Ctrl** + **D**.

   Řadu každý ovládací prvek v levém horním rohu se zobrazí místo něj v aktuální pořadí.

- Chcete-li změnit pořadí pro všechny ovládací prvky, přejděte do nabídky **formátu** > **pořadí** a nastavit pořadí prvků tak, že vyberete každý ovládací prvek v pořadí, které chcete **kartu** klíč sledovat.

- Chcete-li změnit pořadí pro dva nebo více ovládacích prvků, přejděte do nabídky **formátu** > **pořadí**. Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvek, ve kterém se změny v pořadí začít a pak uvolněte **Ctrl** klíče a vyberte ovládací prvky v pořadí, které chcete **kartu** klíč postupujte podle od tohoto okamžiku.

   Například, pokud chcete změnit pořadí ovládacích prvků `7` prostřednictvím `9`, podržte stisknutou klávesu **Ctrl**, vyberte ovládací prvek `6` první.

- Chcete-li nastavit konkrétní ovládací prvek na číslo `1`, nebo první v pořadí, poklepejte na ovládací prvek.

> [!TIP]
> Jakmile zadáte **pořadí** režimu, stiskněte klávesu **Esc** nebo **Enter** ukončíte **pořadí** režimu a zakažte možnost změnit pořadí ovládacích prvků.

## <a name="mnemonics-access-keys"></a>Klávesových zkratek (přístupové klávesy)

Za normálních okolností uživatelé klávesnice Přesun zaměření pro vstup z jednoho ovládacího prvku do druhého v dialogovém okně s **kartu** a **šipku** klíče. Ale můžete definovat přístupovou klávesu (název mnemonická nebo snadno zapamatovat), který umožňuje uživatelům vybrat ovládací prvek stisknutím klávesy jeden klíč.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek titulkem viditelné (tlačítka, zaškrtávací políčka a přepínačů)

1. Vyberte ovládací prvek v dialogovém okně.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **titulek** vlastnost, zadejte nový název pro ovládací prvek psaní znak ampersand (`&`) před písmeno jako přístupový klíč pro tento ovládací prvek. Například, `&Radio1`.

1. Stisknutím klávesy **zadejte**.

   Podtržení se zobrazí v zobrazení titulku udávajících přístupový klíč, například **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Chcete-li definovat přístupovou klávesu pro ovládací prvek bez zobrazen titulek

1. Provádění dotazů pomocí popisek pro ovládací prvek **statický Text** v ovládacím prvku [nástrojů](/visualstudio/ide/reference/toolbox).

1. Statický text titulku, zadejte znak ampersand (`&`) před písmeno jako přístupový klíč.

1. Ujistěte se, že ovládací prvek statického textu bezprostředně předchází ovládací prvek, který ho popisky v pořadí.

> [!NOTE]
> Všechny přístupové klíče v rámci dialogového okna musí být jedinečné. Zkontrolovat duplicitní přístupové klávesy, přejděte do nabídky **formátu** > **zkontrolujte klávesových zkratek**.

## <a name="combo-box-values"></a>Hodnoty pole se seznamem

Můžete přidat hodnoty do ovládacího prvku pole se seznamem za předpokladu, že máte **editoru dialogového okna** otevřete.

> [!TIP]
> Je vhodné přidat všechny hodnoty do pole se seznamem *před* velikost pole v **editoru dialogového okna**, nebo může zkrátit text, který by se měla zobrazit v ovládacím prvku pole se seznamem.

### <a name="to-enter-values-into-a-combo-box-control"></a>Zadejte hodnoty do ovládacího prvku pole se seznamem

1. Zvolte ovládací prvek pole se seznamem tak, že ho vyberete.

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

1. Po zadání hodnoty v **Data** vlastnosti, vyberte **testovací** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

1. Zkuste Posun směrem dolů seznamem celá hodnota. Hodnoty se zobrazí přesně tak, jak jsou zadány v **Data** vlastnost **vlastnosti** okna. Neexistuje žádné pravopisné nebo kontrola malá a velká písmena.

1. Stisknutím klávesy **Esc** se vrátíte **dialogové okno** editoru.

## <a name="radio-button-values"></a>Přepínač hodnoty

Při přidání přepínacích tlačítek do dialogového okna s nimi zacházet jako se skupinou tak, že nastavíte **skupiny** vlastnost **vlastnosti** okno pro první tlačítka ve skupině. ID ovládacího prvku pro tento přepínač se pak objeví v [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), abyste mohli přidat členskou proměnnou pro skupinu přepínačů.

V dialogovém okně můžete mít více než jedné skupině přepínačů. Přidejte každou skupinu pomocí následujícího postupu.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Do dialogového okna Přidat skupinu přepínačů

1. Vyberte ovládací prvek přepínač tlačítko v [okno nástrojů](/visualstudio/ide/reference/toolbox) a zvolit umístění v dialogovém okně umístění ovládacího prvku.

1. Opakujte předchozí krok pro přidání tolika přepínačů, podle potřeby. Zkontrolujte, zda že jsou v pořadí po sobě jdoucích přepínací tlačítka ve skupině.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **skupiny** vlastnost *první* přepínač v pořadí karet na **True**.

   Změna **skupiny** vlastnost **True** přidá WS_GROUP styl tlačítka položky v objektu dialogového okna skriptu prostředků a zabrání může uživatel výběrem více než jeden přepínací tlačítka v daný okamžik v Skupina tlačítek (Pokud uživatel vybere jeden přepínací tlačítko, ostatní ve skupině jsou vymazány).

   > [!NOTE]
   > Pouze první přepínací tlačítko ve skupině by měly mít **skupiny** vlastnost nastavena na hodnotu **True**. Pokud máte další ovládací prvky, které nejsou součástí skupiny tlačítko, nastavte **skupiny** vlastnost první ovládací prvek *, která je mimo skupinu* k **True** také. První ovládací prvek mimo skupinu můžete rychle identifikovat pomocí **Ctrl**+**D** Chcete-li zobrazit pořadí ovládacích prvků.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Přidání členské proměnné pro skupina přepínacích tlačítek

1. Klikněte pravým tlačítkem na první tlačítko ovládacím prvku přepínač v pořadí (dominantního ovládacího prvku a ten se **skupiny** vlastnost nastavena na hodnotu **True**) a zvolte **přidat proměnnou**.

1. V [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), vyberte **řídicí proměnná** zaškrtněte políčko a potom vyberte **hodnotu** přepínač.

   - V **název proměnné** zadejte název pro novou proměnnou člena.

   - V **typ proměnné** pole se seznamem, vyberte **int** nebo typ *int*.

   Nyní můžete upravit kódu k určení, jaké tlačítko přepínače by se měla zobrazit vybraný. Například `m_radioBox1 = 0;` vybere první přepínací tlačítko ve skupině.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Správa ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: Přidání, úpravě nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)<br/>
[Postupy: Rozložení ovládacích prvků](arrangement-of-controls-on-dialog-boxes.md)<br/>