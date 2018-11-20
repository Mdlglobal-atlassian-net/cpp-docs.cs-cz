---
title: Implementace stránky vlastností (ATL)
ms.date: 11/19/2018
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: a76a0f49e8b0ec7458b781785cd5030d2c523f0b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176468"
---
# <a name="example-implementing-a-property-page"></a>Příklad: Implementace stránky vlastností

Tento příklad ukazuje, jak vytvořit stránku vlastnost, která zobrazuje (a je možné změnit) vlastnosti [třídy dokumentů](../mfc/document-classes.md) rozhraní.

Tento příklad vychází [ATLPages ukázka](../visual-cpp-samples.md).

Abyste mohli absolvovat tento příklad, provedete následující:

- [Přidání třídy stránky vlastností knihovny ATL](#vcconusing_the_atl_object_wizard) pomocí dialogového okna Přidat třídu a Průvodce stránkou vlastností ATL.

- [Úprava prostředku dialogového okna](#vcconediting_the_dialog_resource) přidáním nových ovládacích prvků pro zajímavé vlastnosti `Document` rozhraní.

- [Přidání obslužné rutiny zpráv](#vcconadding_message_handlers) udržovat lokality stránky vlastností informováni o změny provedené uživatelem.

- Přidat některé `#import` příkazy a definice typu v [údržbu](#vcconhousekeeping) oddílu.

- [Přepsat IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) ověření objekty předávány na stránku vlastností.

- [Přepsat IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) inicializovat rozhraní na stránce vlastností.

- [Přepsat IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) aktualizovat nejnovější hodnoty vlastností objektu.

- [Zobrazit na stránce vlastností](#vccontesting_the_property_page) tak, že vytvoříte jednoduchou pomocný objekt.

- [Vytvoření makra](#vcconcreating_a_macro) , která otestuje na stránce vlastností.

##  <a name="vcconusing_the_atl_object_wizard"></a> Přidání třídy stránky vlastností knihovny ATL

Nejprve vytvořte nový projekt knihovny ATL DLL serveru s názvem `ATLPages7`. Teď použijte [Průvodce stránkou vlastností ATL](../atl/reference/atl-property-page-wizard.md) ke generování stránky vlastností. Zadejte na stránce vlastností **krátký název** z **DocProperties** pak přepnout do **řetězce** stránky lze nastavit vlastnosti stránky konkrétní položky, jak je znázorněno v následující tabulce.

|Položka|Hodnota|
|----------|-----------|
|Název|TextDocument|
|Řetězec doc|Vlastnosti TextDocument VCUE|
|Soubor nápovědy|*\<Prázdný >*|

Hodnoty, které jste nastavili na této stránce průvodce se vrátí do kontejneru stránky vlastností, pokud zavolá `IPropertyPage::GetPageInfo`. Co se stane řetězce po, který je závislý na kontejner, ale obvykle se používá k identifikaci vaší stránce uživateli. Nadpis se obvykle zobrazí na kartě nad vaší stránce a řetězec Doc, může se zobrazit ve stavovém řádku nebo popisek (i když rámec vlastnosti standardní nebude vůbec používat tento řetězec).

> [!NOTE]
>  Řetězce, které tady nastavíte, jsou uloženy jako řetězcové prostředky ve vašem projektu průvodce. Můžete snadno upravit tyto řetězce pomocí editoru prostředků, pokud potřebujete změnit tyto informace po vygenerování kódu pro stránku.

Klikněte na tlačítko **OK** má průvodce vytvořit stránky vlastností.

##  <a name="vcconediting_the_dialog_resource"></a> Úprava prostředku dialogového okna

Teď, když byl vytvořen stránky vlastností, budete muset přidat několik ovládacích prvků do dialogu prostředků představující vaše stránky. Přidejte do textového pole, ovládací prvek statický text a zaškrtávací políčko a nastavení jejich ID, jak je znázorněno níže:

![Úprava prostředku dialogového okna](../atl/media/ppgresourcelabeled.gif "úpravy prostředku dialogového okna")

Tyto ovládací prvky se použije k zobrazovaný název souboru dokumentu a jeho stav jen pro čtení.

> [!NOTE]
>  Prostředku dialogového okna rámce nebo příkazového tlačítka nezahrnuje ani nemá s kartami vzhled, který může očekávat. Tyto funkce jsou poskytovány rámec pro stránky vlastností, jako jsou vytvořeny pomocí volání [OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe).

##  <a name="vcconadding_message_handlers"></a> Přidání obslužných rutin zpráv

Pomocí ovládacích prvků na místě můžete přidat obslužné rutiny zpráv pro aktualizaci změny stavu stránky při změně hodnoty buď ovládacích prvků:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Tento kód reaguje na změny provedené na ovládací prvek pro úpravy nebo zaškrtněte políčko voláním [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), která informuje stránku webu, který se změnil na stránce. Obvykle bude stránka web reagovat povolením nebo zakázáním **použít** tlačítko v rámci stránky vlastností.

> [!NOTE]
>  Ve vlastní stránky vlastností můžete potřebovat k udržení přehledu o přesně vlastnosti, které změnily uživatel tak, aby se můžete vyhnout, aktualizují se vlastnosti, které nebyly změněny. V tomto příkladu implementuje tento kód tak, že neudržují přehled o původní hodnoty vlastností a jejich porovnání pomocí aktuálních hodnot z uživatelského rozhraní, až nastane čas, aby se změny projevily.

##  <a name="vcconhousekeeping"></a> Údržbu

Teď přidejte do ní několik `#import` příkazy DocProperties.h tak, aby kompilátor ví o `Document` rozhraní:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Budete také muset odkazovat `IPropertyPageImpl` základní třídy, přidejte následující **– typedef** k `CDocProperties` třídy:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Přepsání IPropertyPageImpl::SetObjects

První `IPropertyPageImpl` je metoda, která je potřeba přepsat [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Zde přidejte kód pro kontrolu, že pouze jeden objekt se předal dvoubajtový a že podporuje `Document` rozhraní, které očekáváte:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Je vhodné podporují pouze jeden objekt pro tuto stránku, protože vám umožní uživateli nastavit název souboru objektu – může existovat pouze jeden soubor v libovolném jednoho umístění.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Přepsání IPropertyPageImpl::Activate

Dalším krokem je inicializovat na stránce vlastností s hodnotami vlastností základního objektu při prvním vytvoření stránky.

Následující členy v tomto případě by měl přidejte do třídy, protože můžete také využít počáteční hodnoty vlastností pro porovnání použijete jejich změny stránky:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementace základní třídy [aktivovat](../atl/reference/ipropertypageimpl-class.md#activate) metoda je zodpovědný za vytváření dialogových oken a jejích ovládacích prvků, aby bylo možné tuto metodu přepsat a přidejte vlastní inicializaci po volání metody základní třídy:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Tento kód použije metody COM `Document` rozhraní pro získání vlastnosti, které vás zajímají. Poté použije obálek rozhraní Win32 API poskytované [CDialogImpl](../atl/reference/cdialogimpl-class.md) a její základní třídy k zobrazení hodnoty vlastností pro uživatele.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Přepsání IPropertyPageImpl::Apply

Pokud uživatelé chtějí své změny použít u objektů, bude volat web stránku vlastností [použít](../atl/reference/ipropertypageimpl-class.md#apply) metody. Toto je místo, kde opačný kód v `Activate` – že `Activate` trvalo hodnot z objektu a odesílají je do ovládacích prvků na stránce vlastností `Apply` vezme hodnoty ze ovládacích prvků na stránce vlastností a odesílá je do objekt.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  Kontrola proti [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na začátku této implementaci je počáteční kontrolu, aby se zabránilo zbytečným aktualizace objektů, pokud `Apply` je volána více než jednou. Také se kontroly oproti každému z hodnot vlastností k zajištění, že pouze změny výsledkem volání metody `Document`.

> [!NOTE]
> `Document` Zpřístupňuje `FullName` jako vlastnost jen pro čtení. Chcete-li aktualizovat název souboru dokumentu na základě změn provedených na stránku vlastností, je nutné použít `Save` metoda uložte soubor pod jiným názvem. Proto nebude muset kód na stránce Vlastnosti omezit k získání nebo nastavení vlastnosti.

##  <a name="vccontesting_the_property_page"></a> Zobrazení stránky vlastností

Chcete-li zobrazit tuto stránku, je potřeba vytvořit jednoduché pomocný objekt. Pomocný objekt se bude poskytovat metodu, která zjednodušuje `OleCreatePropertyFrame` připojení rozhraní API pro jednu stránku zobrazení do jednoho objektu. Tohoto pomocníka budou navržené tak, že je možné v prostředí Visual Basic.

Použít [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) a [Průvodce jednoduchý objekt knihovny ATL](../atl/reference/atl-simple-object-wizard.md) pro vygenerování nové třídy a použití `Helper` jako jeho krátký název. Po vytvoření, přidejte metodu, jak je znázorněno v následující tabulce.

|Položka|Hodnota|
|----------|-----------|
|Název metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*BstrCaption* parametr je titulek zobrazený v záhlaví dialogového okna. *BstrID* parametr je řetězec představující identifikátor CLSID nebo ProgID na stránce vlastností zobrazení. *PUnk* parametr bude `IUnknown` ukazatel na objekt, jehož vlastnosti se bude konfigurovat pomocí stránky vlastností.

Implementujte metodu, jak je znázorněno níže:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> Vytvoření makra

Jakmile jednou sestavíte projekt, můžete otestovat stránky vlastností a pomocný objekt pomocí jednoduchého makro, které můžete vytvořit a spustit ve vývojovém prostředí sady Visual Studio. Toto makro vytvoří pomocné rutiny a pak volat jeho `ShowPage` metodu pomocí identifikátor ProgID **DocProperties** stránku vlastností a `IUnknown` ukazatel aktuálně aktivním dokumentem v editoru sady Visual Studio. Kód, který potřebujete pro toto makro je zobrazena níže:

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

Když spustíte toto makro, na stránce vlastností zobrazí zobrazuje název souboru a stav jen pro čtení aktuálního textového dokumentu. Umožňuje zápis do dokumentu ve vývojovém prostředí; jsou pouze údaje stavu jen pro čtení dokumentu To nemá vliv na atribut jen pro čtení souboru na disku.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../atl/atl-com-property-pages.md)<br/>
[Ukázka ATLPages](../visual-cpp-samples.md)
