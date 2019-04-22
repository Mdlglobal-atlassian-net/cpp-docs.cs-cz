---
title: 'Postupy: Přidání, úpravy, nebo odstranění ovládacích prvků (C++)'
ms.date: 02/15/2019
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
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 2e3e671cd92313ad120d2cd6aae3f7e815e09e65
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025361"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Postupy: Přidání, úpravy, nebo odstranění ovládacích prvků (C++)

Použití **editoru dialogového okna**, můžete přidat, změnit velikost, upravit a odstranit ovládací prvky v dialogových oknech. Můžete také upravit vlastnosti ovládacího prvku, třeba jeho ID, nebo zda je zpočátku viditelné v době běhu.

**Editoru dialogového okna** kartě se zobrazí v [okno nástrojů](/visualstudio/ide/reference/toolbox) když pracujete v **editoru dialogového okna**. Můžete také upravit **nástrojů** okno pro snadnější použití. Další informace najdete v tématu [používání sady nástrojů](/visualstudio/ide/using-the-toolbox) a [zobrazit nebo skrýt okno nástrojů](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Při použití **editoru dialogového okna**, v mnoha případech můžete vybrat pravé tlačítko myši zobrazit místní nabídku s často používanými příkazy.

## <a name="add-controls"></a>Přidání ovládacích prvků

### <a name="to-add-a-control"></a>Přidání ovládacího prvku

1. Zajistěte, aby byl dialogového okna s kartami pole aktuálního dokumentu v rámci editoru. Pokud dialogové okno není aktuální dokument, nezobrazí **karta editoru dialogového okna** v **nástrojů**.

1. Na **editoru dialogového okna** karty **nástrojů** okna, vyberte ovládací prvek má, pak buď:

   - Vyberte dialogových oken v umístění, kam chcete umístit ovládací prvek a ovládací prvek se zobrazí, pokud jste vybrali.

   - Přetáhnout myší ovládacího prvku z **nástrojů** okno do umístění ve vašem dialogovém okně a můžete pak pohyb ovládací prvky nebo změňte jejich velikost a tvar.

   - Dvakrát klikněte na panel ovládacího prvku **nástrojů** okně a zobrazí se ve vašem dialogovém okně, přesuňte ovládací prvek na místo, dáváte přednost.

### <a name="to-add-multiple-controls"></a>Chcete-li přidat více ovládacích prvků

1. Když podržíte **Ctrl** klíče, vyberte ovládací prvek v **nástrojů** okna.

1. Verze **Ctrl** klíče a dialogových oken vybrat tolikrát, kolikrát chcete přidat konkrétní ovládací prvek.

1. Stisknutím klávesy **Esc** zastavit umístit ovládací prvky.

### <a name="to-size-a-control-while-you-add-it"></a>Pro nastavení velikosti ovládacího prvku během jeho přidávání

1. Vyberte ovládací prvek v **nástrojů** okna.

1. Umístěte kurzor, který se zobrazí jako různé vlasy, kam chcete levého horního rohu nový ovládací prvek bude ve vašem dialogovém okně.

1. Vyberte a podržte tlačítko myši pro ukotvení levého horního rohu ovládacího prvku v dialogovém okně pak přesuňte kurzor doprava a dolů, dokud je ovládací prvek požadovanou velikost.

   > [!NOTE]
   > Můžete ukotvit všechny čtyři rohy požadovaný kresbě ovládací prvek. Tento postup použít jako příklad levém horním rohu.

1. Uvolněte tlačítko myši. Vyrovná ovládacího prvku do dialogového okna v zadanou velikost.

> [!TIP]
> Můžete změnit velikost ovládacího prvku po přetažení do dialogových oken přesunutím úchyty pro změnu velikosti ohraničení ovládacího prvku. Další informace najdete v tématu [velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Chcete-li přidat vlastní ovládací prvek

Můžete přidat vlastní ovládací prvky do dialogového okna tak, že vyberete **vlastního ovládacího prvku** ikonu **nástrojů** a jeho přetažením na vašem dialogovém okně. Chcete-li přidat **Syslink** řídit, přidat vlastní ovládací prvek a potom změňte ovládacího prvku **třídy** vlastnost **Syslink**. Tato akce způsobí, že vlastnosti, které chcete aktualizovat a zobrazit **Syslink** vlastnosti ovládacího prvku. Informace o obálkové třídy knihovny MFC naleznete v tématu [clinkctrl –](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Ovládací prvky úprav

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Chcete-li upravit vlastnosti ovládacího prvku nebo ovládacích prvků

1. V dialogovém okně vyberte ovládací prvek, který chcete upravit.

   > [!NOTE]
   > Pokud vyberete více ovládacích prvků, lze upravit pouze vlastnosti společné pro vybrané ovládací prvky.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností ovládacího prvku.

   > [!NOTE]
   > Při nastavení **rastrový obrázek** vlastnost tlačítko, přepínač nebo rovna hodnotě ovládací prvek zaškrtávací políčko **True**, styl BS_BITMAP je implementována pro ovládací prvek. Další informace najdete v tématu [styly](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přidružení rastrový obrázek ovládacího prvku, naleznete v tématu [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky nezobrazí ovládacího prvku při práci v **editoru dialogového okna**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Chcete-li vrátit zpět změny vlastností ovládacího prvku

1. Ujistěte se, že ovládací prvek má fokus **editoru dialogového okna**.

1. Přejděte do nabídky **upravit** > **zpět**. Pokud fokus není v ovládacím prvku **zpět** příkaz nebude k dispozici.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Chcete-li definovat členské proměnné pro ovládací prvek dialogového okna (jiné tlačítko)

> [!NOTE]
> Tento postup platí jenom pro ovládací prvky dialogového okna v rámci projektu knihovny MFC. Projekty knihovny ATL používejte **nové zprávy Windows a obslužné rutiny událostí** dialogové okno. Další informace najdete v tématu [zpráva typy přidružených k objektům uživatelského rozhraní](../mfc/reference/message-types-associated-with-user-interface-objects.md), [úpravy obslužné rutiny zpráv](../mfc/reference/editing-a-message-handler.md), a [definování obslužné rutiny zpráv pro zprávy projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. V [editoru dialogového okna](../windows/dialog-editor.md), zvolte ovládací prvek.

1. Při stisknutí **Ctrl** klíče, poklepejte na ovládací prvek pole dialogového okna.

   [Přidat členskou proměnnou průvodce](../ide/add-member-variable-wizard.md) se zobrazí.

1. Zadejte příslušné informace **přidat členskou proměnnou** průvodce. Další informace najdete v tématu [výměna dat dialogových oken](../mfc/dialog-data-exchange.md).

1. Vyberte **OK** se vrátíte **editoru dialogového okna**.

> [!TIP]
> Pokud chcete přejít ze libovolný ovládací prvek dialogového okna na jeho existující obslužné rutiny, poklepejte na ovládací prvek.

Můžete také použít **členské proměnné** kartu [Průvodce třídami MFC](../mfc/reference/mfc-class-wizard.md) přidáte nové proměnné členů pro zadanou třídu a zobrazíte členské proměnné, které jsou již definovány.

## <a name="delete-controls"></a>Odstranění ovládacích prvků

V dialogovém okně vyberte ovládací prvek, stiskněte **odstranit** klíče, nebo přejděte do nabídky **upravit** > **odstranit**.

## <a name="other-issues"></a>Další problémy

### <a name="troubleshooting"></a>Poradce při potížích

Po přidání běžného ovládacího prvku nebo ovládací prvek RTF do dialogového okna, nebude se zobrazovat při testování dialogových oken nebo dialogového okna, samotné se nezobrazí, například:

1. Vytvořte projekt Win32, změna nastavení aplikace, proto vytvořit aplikace Windows (ne konzolovou aplikaci).

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), dvakrát klikněte na *.rc* souboru.

1. V části Možnosti dialogového okna, dvakrát klikněte **o** pole.

1. Přidat **ovládací prvek adresy IP** do dialogového okna.

1. Uložit a **sestavit vše znovu**.

1. Spuštění programu.

1. V dialogových oken **pomáhají** nabídku, vyberte **o** příkaz a sledujte, zobrazí se dialogové okno bez.

V současné době **editoru dialogového okna** nepřidává automaticky kódu do projektu při přetažení následující běžné ovládací prvky nebo ovládací prvky na dialogové okno pro úpravy s formátováním. Ani sada Visual Studio poskytuje chybu nebo upozornění při výskytu tohoto problému. Pokud chcete vyřešit, přidejte kód pro ovládací prvek ručně.

||||
|-|-|-|
|Ovládací prvek posuvníku|Ovládací prvek stromu|Výběr data a času|
|Ovládací prvek typu číselník|Ovládací prvek karty|Měsíční kalendář|
|Ovládací prvek průběh|Animace ovládacího prvku|Ovládací prvek adresy IP|
|Klávesová zkratka|Ovládací prvek pro úpravy s formátováním|Rozšířené pole se seznamem|
|Ovládací prvek seznamu|Ovládací prvek pro úpravy s formátováním 2.0|Vlastní ovládací prvek|

Použití běžných ovládacích prvků v dialogovém okně, je třeba volat [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) nebo `AFXInitCommonControls` předtím, než vytvoříte dialogové okno.

Chcete-li používat řízení RichEdit, musíte volat `LoadLibrary`. Další informace najdete v tématu [o bohaté upravit ovládací prvky](/windows/desktop/Controls/about-rich-edit-controls) v sadě Windows SDK a [– Přehled ovládacího prvku Rich upravit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Použití ovládacího prvku RichEdit s knihovnou MFC, musíte nejprve volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo se telefonicky [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší ovládacího prvku RichEdit 1.0 (RICHED32. KNIHOVNY DLL).
>
> Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třída s atributem starší ovládacího prvku RichEdit 1.0, ale `CRichEditCtrl` je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Protože jsou podobné RichEdit 1.0 a RichEdit 2.0, většina metod bude fungovat. Existují však určité rozdíly mezi 1.0 nebo 2.0 ovládací prvky, takže mohou některé metody nebudou správně fungovat nebo nepracuje vůbec.

### <a name="activex-controls"></a>ActiveX – ovládací prvky

Visual Studio umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně. Další informace najdete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md) a [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md).

**Vložit ovládací prvek ActiveX** dialogové okno umožňuje vložit ovládací prvky ActiveX na vašem dialogovém okně přitom [editoru dialogového okna](../windows/dialog-editor.md). Toto dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Ovládací prvek ActiveX**|Zobrazí seznam ovládacích prvků ActiveX.<br/><br/>Vložení ovládacího prvku z tohoto dialogového okna nebude generovat obálkovou třídu. Pokud potřebujete obálkovou třídu, použijte [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) Pokud chcete jeden vytvořit, přečtěte si téma [přidání třídy](../ide/adding-a-class-visual-cpp.md).<br/><br/>Ovládací prvek ActiveX v toto dialogové okno nezobrazí, zkuste nainstalovat ovládací prvek podle pokynů jeho dodavatele.|
|**Cesta**|Zobrazí soubor, ve kterém se nachází v ovládacím prvku ActiveX.|

> [!CAUTION]
> Nemusí být možné distribuovat všechny ovládací prvky ActiveX v systému. Přečtěte si licenční smlouvy pro software, který je nainstalovaný ovládací prvky nebo se obraťte na softwarová společnost.

#### <a name="to-add-an-activex-control"></a>Chcete-li přidat ovládací prvek ActiveX

1. Otevřete dialogové okno pole **editoru dialogového okna**.

1. Klikněte pravým tlačítkem kamkoli do těla dialogových oken a vyberte **vložit ovládací prvek ActiveX**.

   **Vložit ovládací prvek ActiveX** dialogového okna zobrazuje všechny ovládací prvky ActiveX v systému. V dolní části dialogového okna se zobrazí cesta k souboru ovládacího prvku ActiveX.

1. Vyberte ovládací prvek, který chcete přidat do vaší dialogové okno a zvolte **OK**.

   Ovládací prvek se zobrazí v dialogovém okně, kde můžete upravit nebo vytvořit pro něj obslužné rutiny, stejně jako jakýkoli jiný ovládací prvek.

> [!TIP]
> Můžete použít nabídku **editoru dialogového okna** rychle přidávání registrované ovládacích prvků ActiveX do dialogového okna, nebo zkuste přidat ovládací prvky ActiveX **nástrojů** okno pro snadný přístup.

#### <a name="to-edit-properties-for-an-activex-control"></a>Postup úpravy vlastností pro ovládací prvek ActiveX

Poskytuje nezávislým výrobcům – ovládací prvky ActiveX mohou jsou vybavené své vlastní vlastnosti a vlastnosti. Tyto vlastnosti jsou zobrazeny v **vlastnosti** okna, včetně jakékoli vlastnosti stránky, které uživatelé vytvářející obsah ovládacího prvku ActiveX jsou zobrazeny v **stránky vlastností** dialogové okno (Chcete-li zobrazit  **Stránka vlastností** pro konkrétní ovládací prvek ActiveX, vyberte **stránku vlastností** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window)).

- Vyberte **ActiveX** řídit a přejděte do nabídky **zobrazení** > **stránku vlastností** a zobrazte vlastnosti. Proveďte změny podle potřeby na stránce vlastností.

   Různé karty se zobrazí na stránce vlastností pro ovládací prvek ActiveX, v závislosti na seznamy vlastností, které jsou součástí ovládacího prvku ActiveX.

> [!NOTE]
> Tento postup platí pro použitím stránky vlastnosti můžete upravit ovládací prvky ActiveX. Můžete také procházet a upravovat vlastnosti ActiveX na novém **vlastnosti** okna.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Správa ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: Ovládací prvky rozložení](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Postupy: Definování řízení přístupu a hodnot](defining-mnemonics-access-keys.md)<br/>

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