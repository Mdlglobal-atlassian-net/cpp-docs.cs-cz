---
title: Implementace stránky vlastností (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 68b4aaef06e40a8ec7b00f9ba744d83ce3388da2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492381"
---
# <a name="example-implementing-a-property-page"></a>Příklad: Implementace stránky vlastností

::: moniker range="vs-2019"

Průvodce stránkou vlastností ATL není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Tento příklad ukazuje, jak vytvořit stránku vlastností, která zobrazuje (a umožňuje změnit) vlastnosti rozhraní [třídy dokumentu](../mfc/document-classes.md) .

Příklad je založen na [ukázce ATLPages](../overview/visual-cpp-samples.md).

Pro dokončení tohoto příkladu budete:

- [Přidejte třídu stránky vlastností ATL](#vcconusing_the_atl_object_wizard) pomocí dialogového okna Přidat třídu a Průvodce stránkou vlastností ATL.

- Přidejte nové ovládací prvky pro zajímavé vlastnosti `Document` rozhraní a [upravte prostředek dialogu](#vcconediting_the_dialog_resource) .

- [Přidejte obslužné rutiny zpráv](#vcconadding_message_handlers) , aby se stránka vlastností informovala o změnách provedených uživatelem.

- Přidejte do `#import` části [údržbu](#vcconhousekeeping) nějaké příkazy a typedef.

- [Přepsat IPropertyPageImpl:: SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) pro ověření objektů předávaných na stránku vlastností.

- [Přepsat IPropertyPageImpl:: Activate](#vcconoverriding_ipropertypageimpl_activate) pro inicializaci rozhraní stránky vlastností.

- [Override IPropertyPageImpl:: Apply](#vcconoverride_ipropertypageimpl_apply) aktualizuje objekt o nejnovější hodnoty vlastností.

- [Zobrazení stránky vlastností](#vccontesting_the_property_page) vytvořením jednoduchého objektu pomocníka.

- [Vytvořte makro](#vcconcreating_a_macro) , které bude testovat stránku vlastností.

##  <a name="vcconusing_the_atl_object_wizard"></a>Přidání třídy stránky vlastností ATL

Nejprve vytvořte nový projekt ATL pro server knihovny DLL s názvem `ATLPages7`. Nyní použijte [Průvodce stránkou vlastností ATL](../atl/reference/atl-property-page-wizard.md) k vygenerování stránky vlastností. Dejte stránce vlastností **krátký název** **DocProperties** a potom přejděte na stránku **řetězce** , kde nastavíte položky pro jednotlivé vlastnosti, jak je znázorněno v následující tabulce.

|Položka|Value|
|----------|-----------|
|Název|TextDocument|
|Řetězec doc|VCUE TextDocument – vlastnosti|
|Soubor|*\<prázdné >*|

Hodnoty, které jste nastavili na této stránce průvodce, se vrátí do kontejneru stránky vlastností při volání `IPropertyPage::GetPageInfo`. Co se stane s řetězci po tom, co je závislé na kontejneru, ale obvykle budou použity k identifikaci vaší stránky uživateli. Název se obvykle zobrazí na kartě nad vaší stránkou a řetězec doc se může zobrazit ve stavovém řádku nebo popisu tlačítka (i když standardní rámec vlastností nepoužívá tento řetězec vůbec).

> [!NOTE]
>  Řetězce, které zde nastavíte, jsou v projektu uloženy jako řetězcové prostředky pomocí průvodce. Tyto řetězce lze snadno upravit pomocí editoru prostředků, pokud po vygenerování kódu stránky potřebujete tyto informace změnit.

Kliknutím na tlačítko **OK** vygeneruje průvodce stránku vlastností.

##  <a name="vcconediting_the_dialog_resource"></a>Úprava prostředku dialogového okna

Teď, když se vygenerovala vaše stránka vlastností, budete muset přidat několik ovládacích prvků do prostředku dialogu, který představuje vaši stránku. Přidejte textové pole, ovládací prvek statický text a zaškrtávací políčko a nastavte jeho ID, jak je znázorněno níže:

![Úprava prostředku dialogového okna](../atl/media/ppgresourcelabeled.gif "Úprava prostředku dialogového okna")

Tyto ovládací prvky budou použity k zobrazení názvu souboru dokumentu a jeho stavu jen pro čtení.

> [!NOTE]
>  Prostředek dialogového okna neobsahuje rámeček ani příkazová tlačítka, ani nemá na kartách vzhled, který jste očekávali. Tyto funkce jsou k dispozici v rámci rámce stránky vlastností, jako je například ta vytvořená voláním [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe).

##  <a name="vcconadding_message_handlers"></a>Přidávání obslužných rutin zpráv

Pomocí ovládacích prvků můžete přidat obslužné rutiny zpráv, které aktualizují stav nezměněné stránky, když se změní hodnota některého z ovládacích prvků:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Tento kód reaguje na změny provedené v ovládacím prvku pro úpravy nebo zaškrtávacím políčku voláním [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), který informuje lokalitu, kterou stránka změnila. Web stránky bude typicky reagovat povolením nebo zakázáním tlačítka **použít** na snímku stránky vlastností.

> [!NOTE]
>  Ve vlastních stránkách vlastností možná budete muset sledovat, které vlastnosti uživatel změnil, takže se můžete vyhnout aktualizaci vlastností, které se nezměnily. Tento příklad implementuje tento kód tak, že udržuje přehled o původních hodnotách vlastností a jejich porovnání s aktuálními hodnotami z uživatelského rozhraní, když je čas použít změny.

##  <a name="vcconhousekeeping"></a>Údržbu

Nyní přidejte několik `#import` příkazů do DocProperties. h, aby kompilátor věděl `Document` o rozhraní:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Budete také muset odkazovat na `IPropertyPageImpl` základní třídu; přidejte následující `CDocProperties` definice typedef do třídy:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Přepsání IPropertyPageImpl:: SetObjects

První `IPropertyPageImpl` metoda, kterou je třeba přepsat, je [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Zde přidáte kód pro kontrolu, zda byl předán pouze jeden objekt a zda podporuje `Document` rozhraní, které očekáváte:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Má smysl podporovat pouze jeden objekt pro tuto stránku, protože umožníte uživateli nastavit název souboru objektu – v jednom umístění může existovat pouze jeden soubor.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a>Přepsání IPropertyPageImpl:: Activate

Dalším krokem je inicializace stránky vlastností s hodnotami vlastností podkladového objektu při prvním vytvoření stránky.

V takovém případě byste měli do třídy přidat následující členy, protože použijete také počáteční hodnoty vlastností pro porovnání, když uživatelé stránky použijí změny:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementace základní třídy metody [Activate](../atl/reference/ipropertypageimpl-class.md#activate) zodpovídá za vytvoření dialogového okna a jeho ovládacích prvků, takže můžete tuto metodu přepsat a přidat vlastní inicializaci po volání základní třídy:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Tento kód používá metody `Document` rozhraní COM k získání vlastností, které vás zajímají. Potom používá Win32 API obálky poskytované [CDialogImpl –](../atl/reference/cdialogimpl-class.md) a jeho základními třídami k zobrazení hodnot vlastností uživateli.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a>Přepsání IPropertyPageImpl:: Apply

Když uživatelé chtějí použít změny objektů, na stránce vlastností bude volána metoda [Apply](../atl/reference/ipropertypageimpl-class.md#apply) . Toto je místo, kde se má vrátit kód v `Activate` rámci – zatímco `Activate` převzala hodnoty z objektu a vložili je do ovládacích prvků na stránce vlastností, `Apply` přebírá hodnoty z ovládacích prvků na stránce vlastností a předává je do předmětů.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  Kontrolu proti [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na začátku této implementace je počáteční kontrolou, aby nedocházelo k zbytečným aktualizacím objektů, pokud `Apply` je volána více než jednou. K dispozici jsou také kontroly proti každé z hodnot vlastností, aby bylo zajištěno, že pouze změny mají za `Document`následek volání metody do.

> [!NOTE]
> `Document`zpřístupňuje `FullName` jako vlastnost jen pro čtení. Chcete-li aktualizovat název souboru dokumentu na základě změn provedených na stránce vlastností, je nutné použít `Save` metodu k uložení souboru s jiným názvem. Proto se kód na stránce vlastností nemusí omezovat na získávání nebo nastavování vlastností.

##  <a name="vccontesting_the_property_page"></a>Zobrazení stránky vlastností

Chcete-li zobrazit tuto stránku, je nutné vytvořit jednoduchý objekt pomocníka. Pomocný objekt poskytne metodu, která zjednodušuje `OleCreatePropertyFrame` rozhraní API pro zobrazení jedné stránky připojené k jednomu objektu. Tato pomocná Nápověda bude navržena tak, aby se mohla používat z Visual Basic.

Pomocí [dialogového okna Přidat třídu](../ide/add-class-dialog-box.md) a [Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md) Vygenerujte novou třídu a použijte `Helper` ji jako její krátký název. Po vytvoření přidejte metodu, jak je znázorněno v následující tabulce.

|Položka|Value|
|----------|-----------|
|Název metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Parametr *bstrCaption* je popisek, který se má zobrazit jako název dialogového okna. Parametr *bstrID* je řetězec představující buď identifikátor CLSID, nebo identifikátor ProgID stránky vlastností, který se má zobrazit. Parametr *punk* bude `IUnknown` ukazatelem objektu, jehož vlastnosti budou nakonfigurovány na stránce vlastností.

Implementujte metodu, jak je znázorněno níže:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a>Vytvoření makra

Po sestavení projektu můžete otestovat stránku vlastností a objekt pomocníka pomocí jednoduchého makra, které lze vytvořit a spustit ve vývojovém prostředí sady Visual Studio. Toto makro vytvoří pomocný objekt a potom zavolejte jeho `ShowPage` metodu pomocí identifikátoru ProgID stránky `IUnknown` vlastností **DocProperties** a ukazatele dokumentu, který je aktuálně aktivní v editoru sady Visual Studio. Kód, který potřebujete pro toto makro, je uveden níže:

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

Po spuštění tohoto makra se zobrazí stránka vlastností, která zobrazuje název souboru a stav jen pro čtení aktuálně aktivního textového dokumentu. Stav jen pro čtení dokumentu odráží jenom možnost zapisovat do dokumentu ve vývojovém prostředí; nemá vliv na atribut jen pro čtení souboru na disku.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Stránky vlastností](../atl/atl-com-property-pages.md)<br/>
[Ukázka ATLPages](../overview/visual-cpp-samples.md)
