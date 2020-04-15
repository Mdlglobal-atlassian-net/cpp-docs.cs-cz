---
title: Implementace stránky vlastností (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 0b2448e66e3b86e3295cd4b318a268a113f6058b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319580"
---
# <a name="example-implementing-a-property-page"></a>Příklad: Implementace stránky vlastností

::: moniker range="vs-2019"

Průvodce stránka vlastností atl není k dispozici v sadě Visual Studio 2019 a novější.

::: moniker-end

::: moniker range="<=vs-2017"

Tento příklad ukazuje, jak vytvořit stránku vlastností, která zobrazuje (a umožňuje změnit) vlastnosti rozhraní [Třídy dokumentu.](../mfc/document-classes.md)

Příklad je založen na [vzorku ATLPages](../overview/visual-cpp-samples.md).

Chcete-li dokončit tento příklad, budete:

- [Přidejte třídu stránky vlastností ATL](#vcconusing_the_atl_object_wizard) pomocí dialogového okna Přidat třídu a Průvodce stránkou vlastností atl.

- [Upravte prostředek dialogu](#vcconediting_the_dialog_resource) přidáním nových ovládacích `Document` prvků pro zajímavé vlastnosti rozhraní.

- [Přidejte obslužné rutiny zpráv,](#vcconadding_message_handlers) aby byl web stránky vlastností informován o změnách provedených uživatelem.

- Přidejte `#import` některé příkazy a typedef v části [Úklid.](#vcconhousekeeping)

- [Přepište iPropertyPageImpl::SetObjects,](#vcconoverriding_ipropertypageimpl_setobjects) abyste ověřili objekty předávané na stránku vlastností.

- [Přepište iPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) pro inicializaci rozhraní stránky vlastností.

- [Přepsat iPropertyPageImpl::Použít](#vcconoverride_ipropertypageimpl_apply) k aktualizaci objektu nejnovějšími hodnotami vlastností.

- [Zobrazte stránku vlastností](#vccontesting_the_property_page) vytvořením jednoduchého pomocného objektu.

- [Vytvořte makro,](#vcconcreating_a_macro) které otestuje stránku vlastností.

## <a name="adding-the-atl-property-page-class"></a><a name="vcconusing_the_atl_object_wizard"></a>Přidání třídy vlastností atl

Nejprve vytvořte nový projekt atl pro `ATLPages7`server DLL s názvem . Nyní použijte [Průvodce stránkou vlastností atl](../atl/reference/atl-property-page-wizard.md) ke generování stránky vlastností. Pojmenujte stránku vlastností **krátkým názvem** **DocProperties** a pak přepněte na stránku Řetězce a nastavte **položky** specifické pro stránku vlastností, jak je znázorněno v následující tabulce.

|Položka|Hodnota|
|----------|-----------|
|Nadpis|Textový dokument|
|Řetězec doc|Vlastnosti textového dokumentu VCUE|
|Helpfile|*\<prázdné>*|

Hodnoty nastavené na této stránce průvodce budou při volání `IPropertyPage::GetPageInfo`vráceny do kontejneru stránky vlastností . Co se stane s řetězci po které je závislá na kontejneru, ale obvykle budou použity k identifikaci stránky pro uživatele. Název se obvykle zobrazí na kartě nad stránkou a řetězec dokumentu může být zobrazen na stavovém řádku nebo v popisu (i když standardní rámec vlastností tento řetězec vůbec nepoužívá).

> [!NOTE]
> Řetězce, které zde nastavíte, jsou průvodcem uloženy jako prostředky řetězce v projektu. Tyto řetězce můžete snadno upravit pomocí editoru prostředků, pokud potřebujete tyto informace změnit po vygenerování kódu stránky.

Chcete-li, aby průvodce vygeneroval stránku vlastností, klepněte na tlačítko **OK.**

## <a name="editing-the-dialog-resource"></a><a name="vcconediting_the_dialog_resource"></a>Úprava prostředku dialogu

Teď, když byla vygenerována vaše stránka vlastností, budete muset přidat několik ovládacích prvků do prostředku dialogu představujícího stránku. Přidejte editační pole, statický textový ovládací prvek a zaškrtávací políčko a nastavte jejich ID, jak je znázorněno níže:

![Úprava prostředku dialogu](../atl/media/ppgresourcelabeled.gif "Úprava prostředku dialogu")

Tyto ovládací prvky budou použity k zobrazení názvu souboru dokumentu a jeho stavu jen pro čtení.

> [!NOTE]
> Prostředek dialogového okna neobsahuje rámeček nebo příkazová tlačítka, ani nemá vzhled s kartami, který jste očekávali. Tyto funkce jsou poskytovány rámcem stránky vlastností, například rámcem vytvořeného voláním [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe).

## <a name="adding-message-handlers"></a><a name="vcconadding_message_handlers"></a>Přidání obslužných rutin zpráv

S ovládacími prvky na místě, můžete přidat obslužné rutiny zpráv aktualizovat dirty stav stránky při změně hodnoty některého z ovládacích prvků:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Tento kód reaguje na změny provedené v ovládacím prvku nebo zaškrtávací políčko voláním [iPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), který informuje stránku, že stránka byla změněna. Web stránky obvykle odpoví povolením nebo zakázáním tlačítka **Použít** v rámci stránky vlastností.

> [!NOTE]
> Na vlastních stránkách vlastností může být nutné přesně sledovat, které vlastnosti byly uživatelem změněny, abyste se vyhnuli aktualizaci vlastností, které nebyly změněny. Tento příklad implementuje tento kód udržováním sledování původní hodnoty vlastností a jejich porovnání s aktuální hodnoty z uhlavního použití, když je čas použít změny.

## <a name="housekeeping"></a><a name="vcconhousekeeping"></a>Úklid

Nyní přidejte `#import` několik příkazů docProperties.h tak, aby `Document` kompilátor ví o rozhraní:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Budete také muset odkazovat `IPropertyPageImpl` na základní třídu; přidejte do třídy `CDocProperties` následující **typedef:**

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

## <a name="overriding-ipropertypageimplsetobjects"></a><a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Přepsání IPropertyPageImpl::SetObjects

První `IPropertyPageImpl` metodou, kterou je třeba přepsat, je [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Zde přidáte kód, který zkontroluje, zda byl předán pouze `Document` jeden objekt a zda podporuje rozhraní, které očekáváte:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
> Má smysl podporovat pouze jeden objekt pro tuto stránku, protože umožníte uživateli nastavit název souboru objektu – pouze jeden soubor může existovat v jednom umístění.

## <a name="overriding-ipropertypageimplactivate"></a><a name="vcconoverriding_ipropertypageimpl_activate"></a>Přepsání IPropertyPageImpl::Aktivovat

Dalším krokem je inicializovat stránku vlastností s hodnotami vlastností podkladového objektu při prvním vytvoření stránky.

V takovém případě byste měli do třídy přidat následující členy, protože budete také používat počáteční hodnoty vlastností pro porovnání, když uživatelé stránky použijí své změny:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementace základní třídy [Activate](../atl/reference/ipropertypageimpl-class.md#activate) metoda je zodpovědná za vytvoření dialogového okna a jeho ovládací prvky, takže můžete přepsat tuto metodu a přidat vlastní inicializaci po volání základní třídy:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Tento kód používá metody `Document` COM rozhraní získat vlastnosti, které vás zajímají. Potom používá obálky rozhraní API Win32 poskytované [CDialogImpl](../atl/reference/cdialogimpl-class.md) a jeho základní třídy k zobrazení hodnot vlastností pro uživatele.

## <a name="overriding-ipropertypageimplapply"></a><a name="vcconoverride_ipropertypageimpl_apply"></a>Přepsání IPropertyPageImpl::Použít

Pokud uživatelé chtějí použít své změny na objekty, web stránky vlastností zavolá metodu [Apply.](../atl/reference/ipropertypageimpl-class.md#apply) Toto je místo, kde provést `Activate` opak kódu `Activate` v – vzhledem k tomu, že hodnoty `Apply` z objektu a tlačil je do ovládacích prvků na stránce vlastností, bere hodnoty z ovládacích prvků na stránce vlastností a tlačí je do objektu.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
> Kontrola proti [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na začátku této implementace je počáteční kontrola, `Apply` aby se zabránilo zbytečné aktualizace objektů, pokud je volána více než jednou. Existují také kontroly proti každé z hodnot vlastností, aby bylo `Document`zajištěno, že pouze změny za následek volání metody .

> [!NOTE]
> `Document`zpřístupňuje `FullName` jako vlastnost jen pro čtení. Chcete-li aktualizovat název souboru dokumentu na základě změn provedených `Save` na stránce vlastností, musíte použít metodu k uložení souboru s jiným názvem. Kód na stránce vlastností se tedy nemusí omezovat na získání nebo nastavení vlastností.

## <a name="displaying-the-property-page"></a><a name="vccontesting_the_property_page"></a>Zobrazení stránky vlastností

Chcete-li zobrazit tuto stránku, musíte vytvořit jednoduchý pomocný objekt. Pomocný objekt poskytne metodu, která `OleCreatePropertyFrame` zjednodušuje rozhraní API pro zobrazení jedné stránky připojené k jednomu objektu. Tento pomocník bude navržen tak, aby jej lze použít z jazyka Visual Basic.

Dialogové [okno Přidat třídu](../ide/add-class-dialog-box.md) a [Průvodce jednoduchým objektem knihovny ATL](../atl/reference/atl-simple-object-wizard.md) slouží ke generování nové třídy a použití `Helper` jako krátký název. Po vytvoření přidejte metodu, jak je znázorněno v následující tabulce.

|Položka|Hodnota|
|----------|-----------|
|Název metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Parametr *bstrCaption* je titulek, který se zobrazí jako název dialogového okna. Parametr *bstrID* je řetězec představující buď CLSID nebo ProgID stránky vlastností, která se má zobrazit. Parametr *pUnk* bude `IUnknown` ukazatelem objektu, jehož vlastnosti budou konfigurovány stránkou vlastností.

Metodu implementujte, jak je znázorněno níže:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

## <a name="creating-a-macro"></a><a name="vcconcreating_a_macro"></a>Vytvoření makra

Po vytvoření projektu můžete otestovat stránku vlastností a pomocný objekt pomocí jednoduchého makra, které můžete vytvořit a spustit ve vývojovém prostředí sady Visual Studio. Toto makro vytvoří pomocný objekt `ShowPage` a poté zavolá jeho metodu pomocí progID stránky **vlastností DocProperties** a `IUnknown` ukazatele dokumentu aktuálně aktivního v editoru sady Visual Studio. Kód, který potřebujete pro toto makro, je uveden níže:

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

Při spuštění tohoto makra se zobrazí stránka vlastností zobrazující název souboru a stav aktuálně aktivního textového dokumentu jen pro čtení. Stav dokumentu jen pro čtení odráží pouze schopnost zápisu do dokumentu ve vývojovém prostředí; nemá vliv na atribut souboru jen pro čtení na disku.

::: moniker-end

## <a name="see-also"></a>Viz také

[Stránky vlastností](../atl/atl-com-property-pages.md)<br/>
[Ukázka stránek ATL](../overview/visual-cpp-samples.md)
