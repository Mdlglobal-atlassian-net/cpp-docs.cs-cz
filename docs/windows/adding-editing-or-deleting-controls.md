---
title: 'Postupy: Přidání, úpravy nebo odstranění ovládacích prvků (C++)'
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: a42a64f93d334c0b5c63b0eca1567e6964d0a3ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447216"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Postupy: Přidání, úpravy nebo odstranění ovládacích prvků (C++)

Pomocí **editoru dialogového okna**můžete přidat, změnit velikost, upravit a odstranit ovládací prvky v dialogových oknech. Můžete také upravit vlastnosti ovládacího prvku, jako je jeho ID nebo zda je zpočátku viditelné v době běhu.

Karta **editoru dialogového okna** se zobrazí v [okně panelu nástrojů](/visualstudio/ide/reference/toolbox) při práci v **editoru dialogového okna**. Můžete také přizpůsobit okno **panelu nástrojů** pro snazší použití. Další informace naleznete v tématu [použití panelu nástrojů](/visualstudio/ide/using-the-toolbox) a [zobrazení nebo skrytí okna panelu nástrojů](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Při použití **editoru dialogových oken**můžete v mnoha případech vybrat pravé tlačítko myši a zobrazit místní nabídku často používaných příkazů.

## <a name="add-controls"></a>Přidání ovládacích prvků

### <a name="to-add-a-control"></a>Přidání ovládacího prvku

1. Zajistěte, aby se dialogové okno okna s kartami zobrazovalo jako aktuální dokument v rámci editoru. Pokud dialogové okno není aktuální dokument, v **sadě nástrojů**se nezobrazí **Karta Editor dialogového okna** .

1. Na kartě **Editor dialogového** okna v okně **panelu nástrojů** vyberte požadovaný ovládací prvek a pak jednu z těchto akcí:

   - Vyberte dialogové okno v umístění, kam chcete ovládací prvek umístit, a ovládací prvek se zobrazí tam, kde jste vybrali.

   - Přetáhněte ovládací prvek z okna **panelu nástrojů** do umístění v dialogovém okně. Pak můžete ovládací prvek přesunout kolem nebo změnit jeho velikost a tvar.

   - Dvakrát klikněte na ovládací prvek v okně **panelu nástrojů** a zobrazí se v dialogovém okně. Přesuňte ovládací prvek do umístění, které dáváte přednost.

### <a name="to-add-multiple-controls"></a>Přidání více ovládacích prvků

1. Podržte stisknutou klávesu **CTRL** a vyberte ovládací prvek v okně **panelu nástrojů** .

1. Uvolněte klávesu **CTRL** a vyberte dialogové okno tolikrát, kolikrát chcete přidat konkrétní ovládací prvek.

1. Stisknutím klávesy **ESC** zastavíte umístění ovládacích prvků.

### <a name="to-size-a-control-while-you-add-it"></a>Změna velikosti ovládacího prvku, když ho přidáte

1. Vyberte ovládací prvek v okně **panelu nástrojů** .

1. Umístěte kurzor, který se zobrazí jako zaměřovací kříž, kde chcete, aby byl v dialogovém okně levý horní roh nového ovládacího prvku.

1. Vyberte a podržte stisknuté tlačítko myši k ukotvení levého horního rohu ovládacího prvku v dialogovém okně. Pak přetáhněte kurzor doprava a dolů, dokud ovládací prvek nedosáhne požadované velikosti.

   > [!NOTE]
   > Můžete ukotvit kterýkoli ze čtyř rohů ovládacího prvku, který budete kreslit. Tento postup používal příklad v levém horním rohu.

1. Uvolněte tlačítko myši. Ovládací prvek se přirovná k dialogovému oknu v zadané velikosti.

> [!TIP]
> Můžete změnit velikost ovládacího prvku po jeho přesunutí do dialogového okna přesunutím úchytů pro změnu velikosti na okraji ovládacího prvku. Další informace najdete v tématu [Změna velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Přidání vlastního ovládacího prvku

Do dialogového okna můžete přidat vlastní ovládací prvky. Vyberte ikonu **vlastního ovládacího prvku** v **sadě nástrojů** a přetáhněte ji do dialogového okna. Chcete-li přidat ovládací prvek `Syslink`, přidejte vlastní ovládací prvek a poté změňte vlastnost **třídy** ovládacího prvku na hodnotu `Syslink`. Tato akce způsobí, že se vlastnosti aktualizují a zobrazí vlastnosti ovládacího prvku `Syslink`. Informace o třídě obálky knihovny MFC naleznete v tématu [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Upravit ovládací prvky

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Úprava vlastností ovládacího prvku nebo ovládacích prvků

1. V dialogovém okně vyberte ovládací prvek, který chcete upravit.

   > [!NOTE]
   > Pokud vyberete více ovládacích prvků, lze upravit pouze vlastnosti společné pro vybrané ovládací prvky.

1. V [okno Vlastnosti](/visualstudio/ide/reference/properties-window)změňte vlastnosti ovládacího prvku.

   > [!NOTE]
   > Když nastavíte vlastnost **rastr** pro tlačítko, přepínač nebo ovládací prvek zaškrtávací políčko je rovno hodnotě **True**, je BS_BITMAP stylu implementován pro váš ovládací prvek. Další informace naleznete v tématu [styly tlačítek](../mfc/reference/styles-used-by-mfc.md#button-styles). Příklad přidružení rastrového obrázku k ovládacímu prvku naleznete v tématu [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Rastrové obrázky se nezobrazí na ovládacím prvku, když jste v **editoru dialogového okna**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Zrušení změn vlastností ovládacího prvku

1. Ujistěte se, že ovládací prvek má fokus v **editoru dialogového okna**.

1. Přejděte do nabídky **upravit** > **vrátit zpět**. Pokud fokus není na ovládacím prvku, příkaz pro **vrácení zpět** nebude k dispozici.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Chcete-li definovat členskou proměnnou pro ovládací prvek dialogového okna (ne tlačítko)

> [!NOTE]
> Tento proces se vztahuje pouze na ovládací prvky dialogového okna v rámci projektu MFC. Projekty ATL by měly používat **nové dialogové okno zprávy a obslužné rutiny událostí systému Windows** . Další informace naleznete v tématu [typy zpráv přidružené k objektům uživatelského rozhraní](../mfc/reference/message-types-associated-with-user-interface-objects.md), [Úpravy obslužné rutiny zpráv](../mfc/reference/editing-a-message-handler.md)a [Definování obslužné rutiny zpráv pro zrcadlenou zprávu](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. V [editoru dialogového okna](../windows/dialog-editor.md)vyberte ovládací prvek.

1. Když stisknete klávesu **CTRL** , dvakrát klikněte na ovládací prvek dialog box.

   Zobrazí se [Průvodce Přidat členskou proměnnou](../ide/add-member-variable-wizard.md) .

1. Do průvodce **přidáním členské proměnné** zadejte příslušné informace. Další informace najdete v tématu [Výměna dat dialogových oken](../mfc/dialog-data-exchange.md).

1. Kliknutím na **tlačítko OK** se vraťte do **editoru dialogového okna**.

> [!TIP]
> Chcete-li přejít z jakéhokoli ovládacího prvku dialogu na jeho stávající obslužnou rutinu, dvakrát klikněte na ovládací prvek.

Můžete také použít kartu **členské proměnné** v [Průvodci třídou MFC](../mfc/reference/mfc-class-wizard.md) k přidání nových proměnných členů pro určenou třídu a zobrazení již definovaných proměnných členů.

## <a name="delete-controls"></a>Odstranit ovládací prvky

V dialogovém okně vyberte ovládací prvek a potom stiskněte klávesu **Delete** nebo přejděte do nabídky **Upravit** > **Odstranit**.

## <a name="other-issues"></a>Další problémy

### <a name="troubleshooting"></a>Řešení potíží

Po přidání společného ovládacího prvku nebo ovládacího prvku Rich Edit do dialogového okna se nezobrazí při testování dialogového okna. Nebo se dialogové okno nezobrazí. Příklad:

1. Vytvořte projekt Win32 a změňte nastavení aplikace tak, abyste vytvořili aplikaci pro Windows (ne konzolovou aplikaci).

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)dvakrát klikněte na soubor *. RC* .

1. V dialogovém okně klikněte dvakrát na pole **o produktu** .

1. Přidejte do dialogového okna **ovládací prvek IP adresa** .

1. Uložte a **znovu sestavte vše**.

1. Spusťte program.

1. V nabídce **pomocníka** v dialogovém okně zaškrtněte políčko **o** příkazu a sledujte, že se nezobrazí žádné dialogové okno.

V současné době **Editor dialogového okna** automaticky do projektu nepřidá kód, když přetáhnete následující běžné ovládací prvky nebo ovládací prvky s formátováním do dialogového okna. Ani aplikace Visual Studio při výskytu tohoto problému neposkytne chybu nebo upozornění. Chcete-li opravit, přidejte kód ovládacího prvku ručně.

||||
|-|-|-|
|Ovládací prvek posuvníku|Ovládací prvek strom|Výběr data a času|
|Otočný ovládací prvek|Ovládací prvek karta|Měsíční kalendář|
|Průběh – ovládací prvek|Ovládací prvek animace|Řízení IP adres|
|Klávesová zkratka|Ovládací prvek pro úpravy s formátováním|Rozšířené pole se seznamem|
|Ovládací prvek seznamu|Ovládací prvek s bohatou úpravou 2,0|Vlastní ovládací prvek|

Chcete-li použít běžné ovládací prvky v dialogovém okně, je nutné před vytvořením dialogového okna volat [vyžaduje InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) nebo `AFXInitCommonControls`.

Chcete-li použít ovládací prvky RichEdit, je nutné volat `LoadLibrary`. Další informace naleznete v tématu [informace o ovládacích prvcích pro úpravy s formátováním](/windows/win32/Controls/about-rich-edit-controls) v Windows SDK a [přehledu ovládacího prvku Rich Edit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Chcete-li použít ovládací prvek RichEdit s knihovnou MFC, je nutné nejprve volat [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) a načíst ovládací prvek RichEdit 2,0 (knihovny Riched20. DLL) nebo zavolejte [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) a načtěte starší ovládací prvek RichEdit 1,0 (Riched32. DLL).
>
> Aktuální třídu [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) můžete použít se starším ovládacím prvkem RichEdit 1,0, ale `CRichEditCtrl` je navržen pouze pro podporu ovládacího prvku RichEdit 2,0. Vzhledem k tomu, že RichEdit 1,0 a RichEdit 2,0 jsou podobné, většina metod bude fungovat. Existují však rozdíly mezi ovládacími prvky 1,0 a 2,0, takže některé metody mohou fungovat nesprávně nebo nefungují vůbec.

### <a name="activex-controls"></a>ActiveX – ovládací prvky

Visual Studio umožňuje vkládat ovládací prvky ActiveX do dialogového okna. Další informace naleznete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md) a [kontejnery ovládacích prvků ActiveX](../mfc/activex-control-containers.md).

Dialogové okno **Vložit ovládací prvek ActiveX** umožňuje vložit ovládací prvky ActiveX do dialogového okna při použití [editoru dialogového okna](../windows/dialog-editor.md). Toto dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Ovládací prvek ActiveX**|Zobrazí seznam ovládacích prvků ActiveX.<br/><br/>Vložení ovládacího prvku z tohoto dialogového okna negeneruje obálkovou třídu. Pokud potřebujete obálkovou třídu, použijte [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) k vytvoření jedné, viz [Přidání třídy](../ide/adding-a-class-visual-cpp.md).<br/><br/>Pokud se v tomto dialogovém okně nezobrazí ovládací prvek ActiveX, zkuste nainstalovat ovládací prvek podle pokynů dodavatele.|
|**Cesta**|Zobrazí soubor, ve kterém se nachází ovládací prvek ActiveX.|

> [!CAUTION]
> Je možné, že nebudete mít právo distribuovat všechny ovládací prvky ActiveX do systému. Přečtěte si licenční smlouvu k softwaru, který nainstaloval ovládací prvky, nebo se obraťte na softwarovou společnost.

#### <a name="to-add-an-activex-control"></a>Přidání ovládacího prvku ActiveX

1. Otevřete dialogové okno v **editoru dialogového okna**.

1. Klikněte pravým tlačítkem kamkoli do těla dialogového okna a vyberte **Vložit ovládací prvek ActiveX**.

   Zobrazí se dialogové okno **Vložit ovládací prvek ActiveX** , ve kterém se zobrazí všechny ovládací prvky ActiveX v systému. V dolní části dialogového okna se zobrazí cesta k souboru ovládacího prvku ActiveX.

1. Vyberte ovládací prvek, který chcete přidat do dialogového okna a zvolte **OK**.

   Ovládací prvek se zobrazí v dialogovém okně, kde ho můžete upravit nebo pro něj vytvořit obslužné rutiny stejně jako jakýkoli jiný ovládací prvek.

> [!TIP]
> Místní nabídku v **editoru dialogového okna** můžete použít k rychlému přidání registrovaných ovládacích prvků ActiveX do dialogového okna nebo k přidání ovládacích prvků ActiveX do okna **panelu nástrojů** pro snadný přístup.

#### <a name="to-edit-properties-for-an-activex-control"></a>Úprava vlastností pro ovládací prvek ActiveX

Ovládací prvky ActiveX dodávané nezávislými dodavateli mohou být vybaveny vlastními vlastnostmi a charakteristikami. Tyto vlastnosti jsou zobrazeny v okně **vlastnosti** . Všechny stránky vlastností vytvořené zapisovačem ovládacího prvku ActiveX se zobrazí v dialogovém okně **Vlastnosti stránky** . (Chcete-li zobrazit **stránku vlastností** pro konkrétní ovládací prvek ActiveX, vyberte tlačítko **stránky vlastností** v [okno Vlastnosti](/visualstudio/ide/reference/properties-window)).

- Chcete-li zobrazit vlastnosti, vyberte ovládací prvek **ActiveX** a přejděte na **zobrazení** nabídky > **stránce vlastností** . Podle potřeby proveďte změny na stránce vlastností.

   Na stránce vlastností ovládacího prvku ActiveX se zobrazí různé karty, v závislosti na seznamech vlastností, které jsou součástí ovládacího prvku ActiveX.

> [!NOTE]
> Tento postup se používá pro úpravu ovládacích prvků ActiveX pomocí stránky vlastností. V novém okně **vlastnosti** můžete také procházet a upravovat vlastnosti ActiveX.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Spravovat ovládací prvky dialogového okna](controls-in-dialog-boxes.md)<br/>
[Postupy: rozložení ovládacích prvků](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Postupy: definování přístupu a hodnot řízení](defining-mnemonics-access-keys.md)

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