---
title: Přidání, úprava nebo odstranění ovládacích prvků
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: b4edb5b7a51e4f6d368759ebc2e05a1cc585f19a
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742749"
---
# <a name="adding-editing-or-deleting-controls"></a>Přidání, úprava nebo odstranění ovládacích prvků

Použití **dialogové okno** editoru, můžete přidat, změnit velikost, upravit a odstranit ovládací prvky v dialogových oknech. Můžete také upravit vlastnosti ovládacího prvku, třeba jeho ID, nebo zda je zpočátku viditelné v době běhu.

**Editoru dialogového okna** kartě se zobrazí v [okno nástrojů](/visualstudio/ide/reference/toolbox) když pracujete v **dialogové okno** editoru. Můžete také upravit **nástrojů** okno pro snadnější použití. Další informace najdete v tématu [používání sady nástrojů](/visualstudio/ide/using-the-toolbox) a [zobrazit nebo skrýt okno nástrojů](showing-or-hiding-the-dialog-editor-toolbar.md).

Můžete použít nabídku **dialogové okno** editor rychle přidáte zaregistrované ovládacích prvků ActiveX do dialogového okna a můžete přidat ovládací prvky ActiveX **nástrojů** pro rychlý přístup.

K dispozici ve standardní ovládací prvky **nástrojů** s výchozí události jsou:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[Ovládací prvek tlačítko](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Ovládací prvek zaškrtávací políčko](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Ovládací prvek pole se seznamem](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Ovládací prvek textové pole](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Skupinový rámeček|(Není k dispozici)|
|[Ovládací prvek seznam](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Ovládací prvek přepínač](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Statický ovládací prvek textu](../mfc/reference/cstatic-class.md)|(Není k dispozici)|
|[Ovládací prvek obrázek](../mfc/reference/cpictureholder-class.md)|(Není k dispozici)|
|[Ovládací prvek RTF upravit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Ovládací prvek posuvníku.](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

Další informace o používání **RichEdit 1.0** ovládacím prvkem MFC naleznete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) a [příklady pro ovládací prvek upravit bohaté](../mfc/rich-edit-control-examples.md).

[Běžných ovládacích prvků Windows](../mfc/controls-mfc.md) k dispozici v **nástrojů** poskytovat vylepšené možnosti v aplikaci. Mezi ně patří:

|Název ovládacího prvku|Výchozí událost|
|---|---|
|[Ovládací prvek posuvníku](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Ovládací prvek typu číselník](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Ovládací prvek průběh](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Ovládací prvek výměně klíče](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Ovládací prvek seznamu](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Ovládací prvek stromu](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Ovládací prvek karty](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Animace ovládacího prvku](../mfc/using-an-animation-control.md)|ACN_START|
|[Ovládací prvek pro výběr času data](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Ovládací prvek měsíční kalendář](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Ovládací prvek adresy IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Ovládacího prvku rozšířené pole se seznamem](../mfc/creating-an-extended-combo-box-control.md)||
|[Vlastní ovládací prvek](custom-controls-in-the-dialog-editor.md)|TTN_GETDISPINFO|

Další informace najdete v tématu [třídy ovládacích prvků](../mfc/control-classes.md), [třídy dialogových oken](../mfc/dialog-box-classes.md), a [styly posuvníku](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control"></a>Přidání ovládacího prvku

Chcete-li přidat ovládací prvky do vaší nové dialogového okna, přetáhněte ovládací prvky z **nástrojů** do dialogového okna, kterou vytváříte. Potom můžete pohyb ovládací prvky nebo změňte jejich velikost a tvar.

Můžete přidat vlastní ovládací prvky do dialogového okna tak, že vyberete **vlastního ovládacího prvku** ikonu **nástrojů** a jeho přetažením na vašem dialogovém okně. Chcete-li přidat **Syslink** řídit, přidat vlastní ovládací prvek a potom změňte ovládacího prvku **třídy** vlastnost **Syslink**. Tato akce způsobí, že vlastnosti, které chcete aktualizovat a zobrazit **Syslink** vlastnosti ovládacího prvku. Informace o obálkové třídy knihovny MFC naleznete v tématu [clinkctrl –](../mfc/reference/clinkctrl-class.md).

### <a name="to-add-a-control-to-a-dialog-box"></a>Přidání ovládacího prvku do dialogového okna

1. Zajistěte, aby byl dialogového okna s kartami pole aktuálního dokumentu v rámci editoru. Pokud dialogové okno není aktuální dokument, nezobrazí **karta editoru dialogového okna** v **nástrojů**.

1. Na **editoru dialogového okna** karty **nástrojů** okna, vyberte ovládací prvek pak chcete:

   Vyberte dialogových oken v umístění, kam chcete umístit ovládací prvek. Ovládací prvek zobrazí, pokud jste vybrali.

   \- nebo –

   Přetáhnout myší ovládacího prvku z **nástrojů** do umístění ve vašem dialogovém okně.

   \- nebo –

   Dvakrát klikněte na panel ovládacího prvku **nástrojů** okno (se zobrazí na vašem dialogovém okně) a změna umístění ovládacího prvku do umístění, dáváte přednost.

### <a name="to-add-multiple-controls"></a>Chcete-li přidat více ovládacích prvků

1. Když podržíte **Ctrl** klíče, vyberte ovládací prvek v **nástrojů** okna.

1. Verze **Ctrl** klíče a dialogových oken vybrat tolikrát, kolikrát chcete přidat konkrétní ovládací prvek.

1. Stisknutím klávesy **Esc** zastavit umístit ovládací prvky.

### <a name="to-size-a-control-while-you-add-it"></a>Pro nastavení velikosti ovládacího prvku během jeho přidávání

1. Vyberte ovládací prvek v **nástrojů** okna.

1. Umístěte ukazatel myši (který se zobrazí jako různé vlasy), kde chcete levého horního rohu nový ovládací prvek bude ve vašem dialogovém okně.

1. Vyberte a podržte tlačítko myši pro ukotvení levého horního rohu ovládacího prvku v dialogovém okně pak přesuňte kurzor doprava a dolů, dokud je ovládací prvek požadovanou velikost.

   > [!NOTE]
   > Ve skutečnosti se dá ukotvit, všechny čtyři rohy požadovaný kresbě ovládací prvek. Tento postup použít jako příklad levém horním rohu.

1. Uvolněte tlačítko myši. Vyrovná ovládacího prvku do dialogového okna v zadanou velikost.

   > [!TIP]
   > Můžete změnit velikost ovládacího prvku po přetažení do dialogových oken přesunutím úchyty pro změnu velikosti ohraničení ovládacího prvku. Další informace najdete v tématu [velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md).

### <a name="to-add-an-activex-control"></a>Chcete-li přidat ovládací prvek ActiveX

Visual Studio umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně. Další informace najdete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md) a [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md).

**Vložit ovládací prvek ActiveX** dialogové okno umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně přitom [editoru dialogového okna](../windows/dialog-editor.md). Toto dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Ovládací prvek ActiveX**|Zobrazí seznam ovládacích prvků ActiveX. Vložení ovládacího prvku z tohoto dialogového okna nebude generovat obálkovou třídu. Pokud potřebujete obálkovou třídu, použijte [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) si ji vytvořit (Další informace najdete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md)). Ovládací prvek ActiveX v toto dialogové okno nezobrazí, zkuste nainstalovat ovládací prvek podle pokynů jeho dodavatele.|
|**Cesta**|Zobrazí soubor, ve kterém se nachází v ovládacím prvku ActiveX.|

#### <a name="to-see-the-activex-controls-available"></a>Pokud chcete zobrazit dostupné ovládací prvky ActiveX

1. Dialogové okno otevřete v editoru dialogového okna.

1. Klikněte pravým tlačítkem kamkoli do těla dialogového okna.

1. V místní nabídce vyberte **vložit ovládací prvek ActiveX**.

   **Vložit ovládací prvek ActiveX** dialogového okna zobrazuje všechny ovládací prvky ActiveX v systému. V dolní části dialogového okna se zobrazí cesta k souboru ovládacího prvku ActiveX.

#### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Chcete-li přidat ovládací prvek ActiveX do dialogového okna

1. V **vložit ovládací prvek ActiveX** dialogovém okně vyberte ovládací prvek, který chcete přidat do vaší dialogového okna a vyberte **OK**.

   Ovládací prvek se zobrazí v dialogovém okně, kde můžete upravit nebo vytvořit pro něj obslužné rutiny, stejně jako jakýkoli jiný ovládací prvek.

   > [!NOTE]
   > Můžete přidat ovládací prvky ActiveX **nástrojů** okno pro snadný přístup.

   > [!CAUTION]
   > Nemusí být možné distribuovat všechny ovládací prvky ActiveX v systému. Přečtěte si licenční smlouvy pro software, který je nainstalovaný ovládací prvky nebo se obraťte na softwarová společnost.

## <a name="to-edit-a-control"></a>Chcete-li upravit ovládací prvek

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Chcete-li upravit vlastnosti ovládacího prvku nebo ovládacích prvků

1. V dialogovém okně vyberte ovládací prvek, který chcete upravit.

   > [!NOTE]
   > Pokud vyberete více ovládacích prvků, lze upravit pouze vlastnosti společné pro vybrané ovládací prvky.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností ovládacího prvku.

   > [!NOTE]
   > Při nastavení **rastrový obrázek** vlastnost tlačítko, přepínač nebo rovna hodnotě ovládací prvek zaškrtávací políčko **True**, styl BS_BITMAP je implementována pro ovládací prvek. Další informace najdete v tématu [styly](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přidružení rastrový obrázek ovládacího prvku, naleznete v tématu [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky nezobrazí ovládacího prvku při práci v **dialogové okno** editor prostředků.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Chcete-li vrátit zpět změny vlastností ovládacího prvku

1. Ujistěte se, že ovládací prvek má fokus **dialogové okno** editoru.

1. Zvolte **zpět** z **upravit** nabídce (pokud fokus není v ovládacím prvku **zpět** příkaz nebude k dispozici).

### <a name="to-edit-properties-for-an-activex-control"></a>Postup úpravy vlastností pro ovládací prvek ActiveX

Poskytuje nezávislým výrobcům – ovládací prvky ActiveX mohou jsou vybavené své vlastní vlastnosti a vlastnosti. Vlastnosti pro ovládací prvky ActiveX jsou zobrazeny v **vlastnosti** okna. Navíc se zobrazují všechny vlastnosti stránky, které uživatelé vytvářející obsah ovládacího prvku ActiveX v **stránky vlastností** dialogové okno (Chcete-li zobrazit **stránku vlastností** pro konkrétní ovládací prvek ActiveX, klikněte na tlačítko **Stránku vlastností** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window)).

Různé karty se zobrazí na stránce vlastností pro ovládací prvek ActiveX, v závislosti na seznamy vlastností, které jsou součástí ovládacího prvku ActiveX.

> [!NOTE]
> Následující postup platí pro použitím stránky vlastnosti můžete upravit ovládací prvky ActiveX. Můžete také procházet a upravovat vlastnosti ActiveX na novém **vlastnosti** okna.

1. Vyberte **ActiveX** ovládacího prvku.

1. Na **zobrazení** nabídce vyberte možnost **stránku vlastností** a zobrazte vlastnosti.

1. Proveďte změny podle potřeby na stránce vlastností.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Chcete-li definovat členské proměnné pro ovládací prvek dialogového okna (jiné tlačítko)

Chcete-li definovat členské proměnné pro libovolný ovládací prvek pole dialogové okno s výjimkou tlačítka, můžete použít následující metody.

> [!NOTE]
> Tento postup platí jenom pro ovládací prvky dialogového okna v rámci projektu knihovny MFC. Projekty knihovny ATL používejte **nové zprávy Windows a obslužné rutiny událostí** dialogové okno. Další informace najdete v tématu [zpráva typy přidružených k objektům uživatelského rozhraní](../mfc/reference/message-types-associated-with-user-interface-objects.md), [úpravy obslužné rutiny zpráv](../mfc/reference/editing-a-message-handler.md), a [definování obslužné rutiny zpráv pro zprávy projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. V [editoru dialogového okna](../windows/dialog-editor.md), zvolte ovládací prvek.

1. Při stisknutí **Ctrl** klíče, poklepejte na ovládací prvek pole dialogového okna.

   [Přidat členskou proměnnou průvodce](../ide/add-member-variable-wizard.md) se zobrazí.

1. Zadejte příslušné informace **přidat členskou proměnnou** průvodce. Další informace najdete v tématu [výměna dat dialogových oken](../mfc/dialog-data-exchange.md).

1. Vyberte **OK** se vrátíte **dialogové okno** editoru.

   > [!TIP]
   > Pokud chcete přejít ze libovolný ovládací prvek dialogového okna na jeho existující obslužné rutiny, poklepejte na ovládací prvek.

Můžete také použít **členské proměnné** kartu [Průvodce třídami MFC](../mfc/reference/mfc-class-wizard.md) přidáte nové proměnné členů pro zadanou třídu a zobrazíte členské proměnné, které jsou již definovány.

## <a name="to-delete-a-control"></a>Chcete-li odstranit ovládací prvek

V dialogovém okně vyberte ovládací prvek a stiskněte klávesu **odstranit** klíč.

   \- nebo –

Na **upravit** nabídce vyberte možnost **odstranit**.

   > [!TIP]
   > Při použití **dialogové okno** editoru v mnoha případech můžete kliknutím na tlačítko pravým tlačítkem myši zobrazit místní nabídku s často používanými příkazy.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](controls-in-dialog-boxes.md)<br/>
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->
