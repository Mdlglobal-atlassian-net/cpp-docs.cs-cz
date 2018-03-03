---
title: "Implementace stránky vlastností (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96314b4b8ba7696f784354c2353070ca3873c11c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="example-implementing-a-property-page"></a>Příklad: Implementace stránky vlastností
Tento příklad ukazuje, jak vytvořit stránku vlastností, která zobrazuje (a umožňuje změnit) vlastnosti [třídy dokumentů](../mfc/document-classes.md) rozhraní.  
  
 Tento příklad vychází z [ATLPages ukázka](../visual-cpp-samples.md).  
  
 Abyste mohli dokončit tento příklad, které budete:  
  
- [Přidání třídy knihovny ATL vlastnost stránky](#vcconusing_the_atl_object_wizard) pomocí průvodce ATL vlastnost stránky a dialogové okno Přidat třídu.  
  
- [Úprava prostředku dialogového okna](#vcconediting_the_dialog_resource) přidáním nové ovládací prvky pro zajímavé vlastnosti **dokumentu** rozhraní.  
  
- [Přidání obslužné rutiny zpráv](#vcconadding_message_handlers) zachovat webu stránky vlastnost informováni o změny provedené uživatelem.  
  
-   Přidejte nějaké `#import` příkazů a typedef v [Housekeeping](#vcconhousekeeping) části.  
  
- [Přepsání IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) k ověření objektů předávány na stránku vlastností.  
  
- [Přepsání IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) inicializovat rozhraní její stránku vlastností.  
  
- [Přepsání IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) aktualizace s nejnovější hodnoty vlastností objektu.  
  
- [Zobrazení vlastností stránky](#vccontesting_the_property_page) vytvořením jednoduchého pomocný objekt.  
  
- [Vytvoření makra](#vcconcreating_a_macro) , testovat stránku vlastností.  
  
##  <a name="vcconusing_the_atl_object_wizard"></a>Přidání třídy ATL – stránky vlastností  
 Nejprve vytvořte nový projekt ATL pro knihovny DLL na serveru s názvem `ATLPages7`. Teď použít [ATL vlastnost stránky průvodce](../atl/reference/atl-property-page-wizard.md) ke generování stránky vlastností. Poskytnout stránku vlastností **krátký název** z **DocProperties** potom přepnout **řetězce** stránky lze nastavit položky podle vlastností stránky, jak je znázorněno v následující tabulce.  
  
|Položka|Hodnota|  
|----------|-----------|  
|Název|TextDocument|  
|Popisný řetězec|Vlastnosti TextDocument VCUE|  
|Soubor nápovědy|*\<prázdné >*|  
  
 Hodnoty, které nastavíte na této stránce průvodce se vrátí do kontejneru vlastnost stránky, pokud zavolá **IPropertyPage::GetPageInfo**. Co se stane řetězce, po které je závislá na kontejner, ale obvykle se používá k identifikaci stránku pro uživatele. Název se obvykle objeví na kartě výše stránku a řetězec Doc, může se zobrazit ve stavovém řádku nebo popisek (i když standardní rámec vlastností vůbec nepoužívá tento řetězec).  
  
> [!NOTE]
>  Řetězce, které tady nastavíte, jsou uloženy jako řetězcové prostředky ve vašem projektu průvodcem. Můžete snadno upravit tyto řetězce pomocí editoru prostředků, pokud potřebujete změnit tyto informace po vygenerování kódu pro stránku.  
  
 Klikněte na tlačítko **OK** Průvodce generování stránky vlastností.  
  
##  <a name="vcconediting_the_dialog_resource"></a>Úprava prostředku dialogového okna  
 Teď, když byla vygenerována stránky vlastností, budete muset přidat několik ovládacích prvků do prostředku dialogového okna představující stránku. Přidání textové pole, ovládacího prvku statický text a zaškrtněte políčko a nastavte jejich ID, jak je uvedeno níže:  
  
 ![Úprava prostředku dialogového okna](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")  
  
 Tyto ovládací prvky se použije k zobrazení názvu souboru dokumentu a jeho stav jen pro čtení.  
  
> [!NOTE]
>  Prostředek dialogu nezahrnuje rámce nebo příkazového tlačítka a nemusí záložkách vzhled, které se mají očekávat. Tyto funkce jsou poskytovány rámce stránky vlastnost jako je třeba vytvořit voláním [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437).  
  
##  <a name="vcconadding_message_handlers"></a>Přidání obslužných rutin zpráv  
 Ovládací prvky na místě můžete přidat obslužné rutiny zpráv se bude aktualizovat stav dirty stránky, při změně hodnoty buď ovládacích prvků:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]  
  
 Tento kód reaguje na změny provedené ovládacích prvcích pro úpravy nebo zaškrtněte políčko voláním [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), která informuje o stránku lokality, která se změnila na stránku. Obvykle bude odpovídat webu stránky povolením nebo zakázáním **použít** na stránku rámečku vlastnost tlačítko.  
  
> [!NOTE]
>  V vlastní stránky vlastností může být nutné ke sledování přesněji vlastnosti, které bylo změněno uživatelem tak, aby se můžete vyhnout, aktualizace vlastností, které nebyly změněny. Tento příklad implementuje tento kód nesleduje původní hodnoty vlastností a porovnávání pomocí aktuálních hodnot z uživatelského rozhraní, když je čas, aby se změny projevily.  
  
##  <a name="vcconhousekeeping"></a>Housekeeping  
 Nyní přidat pár `#import` příkazy, čímž DocProperties.h tak, aby kompilátor zná **dokumentu** rozhraní:  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]  
  
 Budete také potřebovat k odkazování na `IPropertyPageImpl` základní třída; přidejte následující `typedef` k **CDocProperties** třídy:  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Přepsání IPropertyPageImpl::SetObjects  
 První `IPropertyPageImpl` metoda, která je nutné přepsat [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Zde přidáte kód pro zkontrolujte, že byl předán pouze jeden objekt, a že podporuje **dokumentu** rozhraní, které očekáváte:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  Má smysl pro podporu pouze jednoho objektu pro tuto stránku, protože vám umožní uživateli nastavit název souboru objektu – v libovolném jeden umístění může existovat pouze jeden soubor.  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a>Přepsání IPropertyPageImpl::Activate  
 Dalším krokem je k chybě při inicializaci stránku vlastností s hodnoty vlastností podkladového objektu při prvním vytvoření stránky.  
  
 V takovém případě by měl přidejte následující členy do třídy, vzhledem k tomu, že budete taky používat počáteční hodnoty vlastnosti pro porovnání když uživatelé stránky své změny:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]  
  
 Základní třída implementace [aktivovat](../atl/reference/ipropertypageimpl-class.md#activate) metoda zodpovídá za vytvoření dialogového okna a jeho ovládacích prvků, aby bylo možné tuto metodu přepsat a přidejte vlastní inicializaci po volání metody základní třídy:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]  
  
 Tento kód používá metody COM **dokumentu** rozhraní získat vlastnosti, které vás zajímají. Poté použije obálky Win32 API poskytované [CDialogImpl](../atl/reference/cdialogimpl-class.md) a jeho základních tříd k zobrazení hodnot vlastností pro uživatele.  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a>Přepsání IPropertyPageImpl::Apply  
 Když uživatelé chtějí jejich změny pro objekty, bude volat webu stránky vlastností [použít](../atl/reference/ipropertypageimpl-class.md#apply) metoda. Toto je místo, kde opačný kód **aktivovat** – zatímco **aktivovat** trvalo hodnot z objektu a jejich instaluje do ovládacích prvků na stránce vlastností **použít** vezme hodnoty z ovládacích prvků na stránce vlastností a jejich nabízených oznámení do objektu.  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  Kontrola u [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na začátku Tato implementace je počáteční kontrolu, aby se zabránilo zbytečným aktualizace objektů, pokud **použít** nazývá více než jednou. Existují také kontroly proti jednotlivým hodnot vlastností zajistit, že pouze změny provedené výsledkem volání metody **dokumentu**.  
  
> [!NOTE]
> **Dokument** zpřístupní **FullName** jako vlastnost jen pro čtení. Pokud chcete aktualizovat název souboru dokumentu, na základě změn provedených na stránku vlastností, budete muset použít **Uložit** metoda uložte soubor pod jiným názvem. Proto kód na stránce vlastností nemá omezit sám sebe pro získání nebo nastavení vlastností.  
  
##  <a name="vccontesting_the_property_page"></a>Zobrazení stránky vlastností  
 K zobrazení této stránky, musíte vytvořit jednoduché pomocný objekt. Pomocný objekt poskytne metodu, která zjednodušuje **OleCreatePropertyFrame** rozhraní API pro zobrazení jednotlivých stránek připojení pro jediný objekt. Tohoto pomocníka budou navrženy tak, aby ho bylo možné použít z jazyka Visual Basic.  
  
 Použít [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) a [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md) vygenerovat novou třídu a použijte `Helper` jako jeho krátký název. Po vytvoření, přidejte metodu, jak je znázorněno v následující tabulce.  
  
|Položka|Hodnota|  
|----------|-----------|  
|Název metody|`ShowPage`|  
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption` Parametr je titulek zobrazený v záhlaví dialogového okna. `bstrID` Parametr je řetězec představující identifikátor CLSID nebo ProgID vlastnost stránky zobrazení. `pUnk` Parametr bude `IUnknown` ukazatele objektu, jehož vlastnosti se bude konfigurovat pomocí jeho stránku vlastností.  
  
 Implementujte metodu, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a>Vytváření maker  
 Jakmile jste sestavili projekt, můžete otestovat stránku vlastností a objekt pomocníka použití jednoduchého makra, která umožňuje vytvářet a spouštět ve vývojovém prostředí sady Visual Studio. Toto makro vytvoří pomocné rutiny objektu a pak volat jeho **ShowPage** metodu pomocí atribut ProgID v **DocProperties** stránku vlastností a **IUnknown** ukazatel dokumentu v editoru Visual Studio aktuálně aktivní. Kód, který je nutné pro tuto makro je zobrazena níže:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
 
Public Module AtlPages  
 
    Public Sub Test()  
    Dim Helper  
    Helper = CreateObject("ATLPages7.Helper.1")  
 
    On Error Resume Next  
    Helper.ShowPage(_ 
    ActiveDocument.Name,
    _ 
 "ATLPages7Lib.DocumentProperties.1",
    _ 
    DTE.ActiveDocument _)  
    End Sub  
 
End Module  
```  
  
 Při spuštění této makra vlastnosti se zobrazí stránka zobrazuje název souboru a jen pro čtení stav aktuálně aktivní textového dokumentu. Stav jen pro čtení dokumentu odráží pouze možnost zapisovat do dokumentu ve vývojovém prostředí; neovlivní atribut jen pro čtení souboru na disku.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../atl/atl-com-property-pages.md)   
 [Ukázka ATLPages](../visual-cpp-samples.md)

