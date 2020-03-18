---
title: 'Postupy: definování přístupu a hodnot řízení (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 8ebd8d48b68581bf00215b4ca14f5ac0a543a3c0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443907"
---
# <a name="how-to-define-control-access-and-values-c"></a>Postupy: definování přístupu a hodnot řízení (C++)

## <a name="tab-order"></a>Pořadí prvků

Pořadí prvků je pořadí, ve kterém klávesa **TAB** přesune fokus vstupu z jednoho ovládacího prvku do dalšího v rámci dialogového okna. Obvykle pořadí prvků pokračuje od zleva doprava a shora dolů v dialogovém okně. Každý ovládací prvek má vlastnost **přístupového** ovládacího prvku, která určuje, zda ovládací prvek dostane fokus vstupu.

- Chcete-li nastavit fokus vstupu pro ovládací prvek, v [okně Vlastnosti](/visualstudio/ide/reference/properties-window)v poli vlastnost **přístupového** panelu vyberte **hodnotu true** nebo **false** .

Dokonce i ovládací prvky, které nemají vlastnost **přístupového** panelu nastavenou na **hodnotu true** , musí být součástí pořadí prvků, zejména pro ovládací prvky, které nemají popisky. Statický text obsahující přístupový klíč pro související ovládací prvek musí bezprostředně předcházet souvisejícímu ovládacímu prvku v pořadí prvků.

> [!NOTE]
> Pokud dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob zobrazení ovládacích prvků. Ovládací prvky, které jsou uvedeny později v pořadí prvků, jsou vždy zobrazeny nad všemi překrývajícími se ovládacími prvky, které jim předcházejí v pořadí prvků.

- Chcete-li zobrazit aktuální pořadí ovládacích prvků pro všechny ovládací prvky, přejděte do nabídky **formát** > **pořadí prvků**nebo stiskněte klávesovou **zkratku CTRL** + **D**.

   Číslo v levém horním rohu každého ovládacího prvku zobrazuje své místo v aktuálním pořadí ovládacích prvků.

- Chcete-li změnit pořadí prvků pro všechny ovládací prvky, přejděte na **Formát** nabídky > **pořadí prvků** a nastavte pořadí prvků výběrem jednotlivých ovládacích prvků v pořadí, v němž má klávesa **TAB** následovat.

- Chcete-li změnit pořadí karet pro dva nebo více ovládacích prvků, přejděte do nabídky **formát** > **pořadí prvků**. Podržte stisknutou **klávesu CTRL** a vyberte ovládací prvek, na kterém bude začínat změna, a pak uvolněte klávesu **CTRL** a vyberte ovládací prvky v pořadí, od kterého má klávesa **TAB** následovat.

   Například pokud chcete změnit pořadí ovládacích prvků `7` přes `9`, podržte stisknutou **klávesu CTRL**a potom vyberte ovládací prvek `6` nejdříve.

- Chcete-li nastavit konkrétní ovládací prvek na číslo `1`nebo první v pořadí prvků, dvakrát klikněte na ovládací prvek.

> [!TIP]
> Po zadání režimu **pořadí karet** stiskněte klávesu **ESC** nebo **ENTER** pro ukončení režimu **pořadí karet** a zakázání možnosti změnit pořadí prvků.

## <a name="mnemonics-access-keys"></a>Klávesové zkratky (přístupové klávesy)

Uživatelé klávesnice obvykle pohybují fokus z jednoho ovládacího prvku na jiný v dialogovém okně s klávesami **TAB** a **šipky** . Můžete ale definovat přístupový klíč (symbol nebo snadno zapamatovatelný název), který umožňuje uživatelům vybrat ovládací prvek stisknutím jediného klíče.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Definování přístupového klíče pro ovládací prvek se zobrazeným titulkem (tlačítka pro vložení, zaškrtávací políčka a přepínače)

1. Vyberte ovládací prvek v dialogovém okně.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)do vlastnosti **Titulek** zadejte nový název ovládacího prvku a zadáním ampersandu (`&`) před písmeno, které chcete pro tento ovládací prvek použít. například `&Radio1`.

1. Stiskněte **Enter**.

   Podtržení se zobrazí v zobrazeném titulku, aby označovalo přístupový klíč, například **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Definování přístupového klíče pro ovládací prvek bez viditelného titulku

1. Vytvořte titulek ovládacího prvku pomocí ovládacího prvku **statický text** v [sadě nástrojů](/visualstudio/ide/reference/toolbox).

1. Do titulku statického textu zadejte ampersand (`&`) před písmeno, které chcete použít jako přístupový klíč.

1. Ujistěte se, že ovládací prvek statický text hned předchází ovládacímu prvku, který je označen popiskem v pořadí ovládacích prvků.

> [!NOTE]
> Všechny přístupové klávesy v dialogovém okně by měly být jedinečné. Chcete-li vyhledat duplicitní přístupové klíče, přejděte do nabídky **formát** > **kontrolovat klávesové**zkratky.

## <a name="combo-box-values"></a>Hodnoty pole se seznamem

Můžete přidat hodnoty do ovládacího prvku pole se seznamem, pokud máte **Editor dialogového okna** otevřený.

> [!TIP]
> *Před* velikostí pole v **editoru dialogového okna**je vhodné přidat všechny hodnoty do pole se seznamem, nebo můžete zkrátit text, který se má zobrazit v ovládacím prvku se seznamem.

### <a name="to-enter-values-into-a-combo-box-control"></a>Zadání hodnot do ovládacího prvku pole se seznamem

1. Vyberte ovládací prvek pole se seznamem tím, že ho vyberete.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)se posuňte dolů k vlastnosti **data** .

   > [!NOTE]
   > Pokud zobrazujete vlastnosti seskupené podle typu, zobrazí se **data** v **různých** vlastnostech.

1. Vyberte oblast hodnota pro vlastnost **dat** a zadejte hodnoty dat, které jsou odděleny středníky.

   > [!NOTE]
   > Neumísťuje mezery mezi hodnoty, protože prostory, které jsou v rozevíracím seznamu v konfliktu s alphabetizing.

1. Po dokončení přidávání hodnot stiskněte klávesu **ENTER** .

Informace o zvětšení rozevírací části pole se seznamem naleznete v tématu [Nastavení velikosti pole se seznamem a jeho rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Pomocí tohoto postupu nemůžete přidávat hodnoty do projektů Win32 (vlastnost **data** je u projektů Win32 šedá). Vzhledem k tomu, že projekty Win32 nemají knihovny, které tuto funkci přidávají, je nutné přidat hodnoty do pole se seznamem s použitím projektu Win32 programově.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Testování vzhledu hodnot v poli se seznamem

1. Po zadání hodnot do vlastnosti **data** vyberte na [panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)tlačítko **test** .

1. Zkuste posun dolů o celý seznam hodnot. Hodnoty se zobrazí přesně tak, jak jsou zadány ve vlastnosti **data** v okně **vlastnosti** . Není k dispozici kontrola pravopisu nebo psaní velkých písmen.

1. Stisknutím klávesy **ESC** se vraťte do editoru **dialogových oken** .

## <a name="radio-button-values"></a>Hodnoty přepínačů

Když přidáte přepínače do dialogového okna, považovat je za skupinu nastavením vlastnosti **Group** v okně **vlastnosti** prvního tlačítka ve skupině. ID ovládacího prvku pro tento přepínač se pak zobrazí v [Průvodci přidáním členské proměnné](../ide/add-member-variable-wizard.md), což umožňuje přidat členskou proměnnou pro skupinu přepínačů.

Můžete mít více než jednu skupinu přepínačů v dialogovém okně. Jednotlivé skupiny přidejte pomocí následujícího postupu.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Přidání skupiny přepínacích tlačítek do dialogového okna

1. V [okně panelu nástrojů](/visualstudio/ide/reference/toolbox) vyberte ovládací prvek přepínač a zvolte umístění v dialogovém okně, kam chcete ovládací prvek umístit.

1. Opakujte výše uvedený krok a přidejte tolik přepínačů, kolik potřebujete. Ujistěte se, že přepínače ve skupině jsou po sobě po sobě v pořadí prvků.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)nastavte vlastnost **Skupina** *prvního* přepínače v pořadí prvků na **hodnotu true**.

   Změna vlastnosti **Group** na **hodnotu True** přidá styl WS_GROUP k položce tlačítka v objektu dialogového okna skriptu prostředků a zabrání uživateli v výběru více přepínačů najednou ve skupině tlačítek (Pokud uživatel vybere jeden přepínač, ostatní uživatelé ve skupině jsou vymazáni).

   > [!NOTE]
   > Vlastnost **Group** je nastavena na **hodnotu true**pouze prvním přepínačem ve skupině. Pokud máte další ovládací prvky, které nejsou součástí skupiny tlačítek, nastavte vlastnost **Group** prvního ovládacího prvku *, který je mimo skupinu* , na **hodnotu true** . Můžete rychle identifikovat první ovládací prvek mimo skupinu pomocí **kombinace kláves Ctrl**+**D** a zobrazit pořadí ovládacích prvků.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Přidání členské proměnné pro skupinu přepínačů

1. Pravým tlačítkem myši klikněte na první ovládací prvek přepínače v pořadí prvků (dominantní ovládací prvek a druhý s vlastností **Group** nastavenou na **true**) a vyberte **přidat proměnnou**.

1. V [Průvodci přidáním členské proměnné](../ide/add-member-variable-wizard.md)zaškrtněte políčko **řídicí proměnná** a pak vyberte přepínač **hodnota** .

   - Do pole **název proměnné** zadejte název pro novou členskou proměnnou.

   - V poli se seznamem **typ proměnné** vyberte **int** nebo zadejte *int*.

   Nyní můžete upravit kód a určit, který přepínač má být vybrán. `m_radioBox1 = 0;` například vybere první přepínač ve skupině.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Spravovat ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: Přidání, úprava nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)<br/>
[Postupy: rozložení ovládacích prvků](arrangement-of-controls-on-dialog-boxes.md)<br/>