---
title: 'Ovládací prvky MFC ActiveX: Použití písem | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f5d1475412de736970d0ae36a39540121bfbc01
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930712"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC – ovládací prvky ActiveX: Použití písem
Pokud vaše ovládací prvek ActiveX zobrazí text, můžete povolit uživateli řízení Změna vzhledu textu změnou vlastnosti písma. Vlastnosti písma jsou implementovány jako objekty písma a může mít jednu ze dvou typů: uložených nebo vlastní. Uložené vlastnosti písma jsou vlastnosti preimplemented písma, které můžete přidat pomocí Průvodce přidáním vlastnosti. Vlastní vlastnosti písma nejsou preimplemented a vývojář ovládacího prvku určuje tato vlastnost chování a využití.  
  
 Tento článek obsahuje následující témata:  
  
-   [Pomocí Stock Font – vlastnost](#_core_using_the_stock_font_property)  
  
-   [Pomocí vlastností vlastní písma v vlastního ovládacího prvku](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> Pomocí vlastnosti uložených písma  
 Uložené vlastnosti písma jsou preimplemented v třídě [COleControl](../mfc/reference/colecontrol-class.md). Kromě toho je standardní stránky vlastností písma také k dispozici, které uživateli umožňují změnit různé atributy písma objektu, například jeho název, velikost a styl.  
  
 Přístup k objektu písma prostřednictvím [getfont –](../mfc/reference/colecontrol-class.md#getfont), [setfont –](../mfc/reference/colecontrol-class.md#setfont), a [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funkce `COleControl`. Uživatelské ovládací prvek bude přistupovat k tomuto objektu písma prostřednictvím `GetFont` a `SetFont` funkce stejným způsobem jako ostatní vlastnosti Get/Set. Pokud je nutný z v ovládacím prvku přístup k objektu písmo, použijte `InternalGetFont` funkce.  
  
 Jak je popsáno v [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md), přidání uložených vlastností je snadné se [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md). Vyberte vlastnost písma a Průvodce přidáním vlastnosti automaticky vloží uložených písma položku do ovládacího prvku expediční mapy.  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Chcete-li přidat uložených vlastností písma, pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Otevře se Průvodce přidáním vlastnosti.  
  
5.  V **název vlastnosti** pole, klikněte na tlačítko **písma**.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
 Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku odesílání mapy, umístěný v řídicím souboru implementace třídy:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 Kromě toho Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 Uložené vlastnosti titulku je příklad vlastnosti textu, která lze rozlišovat pomocí uložené informace o vlastnosti písma. Přidání zásob Vlastnosti titulku do ovládacího prvku používá kroky, které jsou podobné těm, které používá pro stock Font – vlastnost.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastnost uložených titulek pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Otevře se Průvodce přidáním vlastnosti.  
  
5.  V **název vlastnosti** pole, klikněte na tlačítko **popisek**.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
 Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku odesílání mapy, umístěný v řídicím souboru implementace třídy:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> Úprava OnDraw – funkce  
 Výchozí implementaci `OnDraw` používá písmo systému Windows pro všechny text zobrazený v ovládacím prvku. To znamená, že je nutné upravit `OnDraw` kód tak, že vyberete objekt písma do kontextu zařízení. Chcete-li to provést, volejte [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) a předejte kontextu zařízení ovládacího prvku, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 Po `OnDraw` funkce změnila použití objektu písma, text v rámci prvku zobrazil s vlastnostmi z ovládacího prvku uložených vlastností písma.  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> Pomocí vlastností vlastní písma v vlastního ovládacího prvku  
 Kromě uložených vlastností písma ovládacího prvku ActiveX může mít vlastní vlastnosti písma. Chcete-li přidat vlastní písma vlastnost postupujte takto:  
  
-   Použijte Průvodce přidáním vlastnosti implementovat vlastní vlastnost písma.  
  
-   [Zpracování oznámení písma](#_core_processing_font_notifications).  
  
-   [Implementace nové rozhraní oznámení písma](#_core_implementing_a_new_font_notification_interface).  
  
###  <a name="_core_implementing_a_custom_font_property"></a> Implementace vlastní Font – vlastnost  
 Pokud chcete implementovat vlastní vlastnost písma, použijete Průvodce přidáním vlastnosti k přidat vlastnost a potom proveďte úpravy kódu. Následující části popisují, jak přidat vlastní `HeadingFont` vlastnosti do ovládacího prvku ukázka.  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní vlastnost písma pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Otevře se Průvodce přidáním vlastnosti.  
  
5.  V **název vlastnosti** zadejte název vlastnosti. V tomto příkladu použijte **headingfont –**.  
  
6.  Pro **typem implementace**, klikněte na tlačítko **metody Get/Set**.  
  
7.  V **typ vlastnosti** vyberte **IDispatch\***  pro typ vlastnosti.  
  
8.  Klikněte na tlačítko **Dokončit**.  
  
 Průvodce přidáním vlastnosti vytvoří kódu k přidání `HeadingFont` vlastní vlastnost `CSampleCtrl` třídy a UKÁZKY. IDL soubor. Protože `HeadingFont` je vlastnost typu Get/Set upraví Průvodce přidáním vlastnosti `CSampleCtrl` mapy odeslání třídy a zahrnout DISP_PROPERTY_EX_ID[disp_property_ex –](../mfc/reference/dispatch-maps.md#disp_property_ex) makro položky:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 Disp_property_ex – makro přidruží `HeadingFont` název vlastnosti k jeho odpovídajícím zprostředkovatelům `CSampleCtrl` třída získání a nastavení metody, `GetHeadingFont` a `SetHeadingFont`. Rovněž je zadán typ hodnoty vlastnosti; v tomto případě VT_FONT.  
  
 Průvodce přidáním vlastnosti také přidá deklaraci v souboru ovládacího prvku záhlaví (. H) pro `GetHeadingFont` a `SetHeadingFont` funkce a přidá jejich funkce šablon v řídicím souboru implementace (. CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 Nakonec Průvodce přidáním vlastnosti upravuje ovládacího prvku. IDL souboru tak, že přidáte položku pro `HeadingFont` vlastnost:  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>Změny kódu ovládacího prvku  
 Teď, když jste přidali `HeadingFont` vlastnosti do ovládacího prvku, je nutné provést některé změny na soubory, které plně podporují nové vlastnosti záhlaví a implementaci ovládacího prvku.  
  
 V souboru ovládacího prvku záhlaví (. H), přidejte následující deklarace proměnné chráněného člena:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 V řídicím souboru implementace (. CPP), postupujte takto:  
  
-   Inicializace *m_fontHeading* v konstruktoru ovládacího prvku.  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   Definice statických FONTDESC struktury obsahující výchozí atributy písma.  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   V ovládacím prvku `DoPropExchange` člen fungovat, že přidáte volání `PX_Font` funkce. To poskytuje inicializace a trvalosti pro vaše vlastní vlastnost písma.  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   Dokončit implementaci ovládacího prvku `GetHeadingFont` – členská funkce.  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   Dokončit implementaci ovládacího prvku `SetHeadingFont` – členská funkce.  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   Ovládací prvek upravit `OnDraw` – členská funkce k definování proměnné pro uložení dříve vybrané písmo.  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   Ovládací prvek upravit `OnDraw` – členská funkce a vyberte vlastní písmo do kontextu zařízení přidáním následující řádek bez ohledu na písmo má být použita.  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   Ovládací prvek upravit `OnDraw` – členská funkce vyberte předchozí písmo zpět do kontextu zařízení po použila písmo, a to přidáním následujícího řádku.  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 Po implementovala vlastní vlastnost písma standardní vlastnost stránka písmo by měla být implementována, umožnit uživatelům ovládací prvek, chcete-li změnit písmo aktuální ovládacího prvku. Přidat ID stránky vlastností pro standardní vlastnost stránka písmo, vložte následující řádek po begin_proppageids – makro:  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 Musíte také zvýšit počet parametru begin_proppageids – makro o jednu. To ukazuje následující řádek:  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 Poté, co byly provedeny změny, znovu sestavte celý projekt, který má obsahovat další funkce.  
  
###  <a name="_core_processing_font_notifications"></a> Zpracování oznámení písma  
 Ve většině případů je potřeba vědět, kdy byly upraveny vlastnosti objektu písma ovládacího prvku. Každý objekt písma je schopný poskytnout oznámení při změně voláním funkce člena `IFontNotification` rozhraní implementované `COleControl`.  
  
 Pokud ovládací prvek používá uložených vlastností písma, jsou zpracovávány jeho oznámení `OnFontChanged` členské funkce `COleControl`. Když přidáte vlastní písma vlastnosti, si můžete je použít stejnou implementaci. V příkladu v předchozí části se toho dosáhlo tím předávání &*m_xFontNotification* při inicializaci *m_fontHeading* členské proměnné.  
  
 ![Implementace více rozhraní objektů písma](../mfc/media/vc373q1.gif "vc373q1")  
Implementace více rozhraní objektů písma  
  
 Plné čáry na výše uvedeném obrázku zobrazit, že oba objekty písma používají stejné implementace `IFontNotification`. Pokud jste chtěli rozlišení, které písmo změnit to může způsobit problémy.  
  
 Jeden způsob k rozlišení mezi ovládacího prvku písma objekt oznámení je vytvoření samostatné provádění `IFontNotification` rozhraní pro každý objekt písma v ovládacím prvku. Tento postup umožňuje optimalizovat kreslení kód aktualizací pouze řetězec, nebo řetězce, které ho používají naposledy upravené. Následující části ukazují kroky nezbytné k implementaci rozhraní samostatné oznámení pro druhou vlastností písma. Druhou vlastností písma předpokládá se, že `HeadingFont` vlastnost, která byla přidána v předchozí části.  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> Implementace nové rozhraní oznámení písma  
 K rozlišení mezi oznámení o dvě nebo více písem, je nutné implementovat nové rozhraní oznámení pro každou písmo použité v ovládacím prvku. Následující části popisují, jak implementovat nové rozhraní oznámení písma změnou ovládacího prvku záhlaví a implementace soubory.  
  
### <a name="additions-to-the-header-file"></a>Doplňky soubor hlaviček  
 V souboru ovládacího prvku záhlaví (. H), přidejte následující řádky do deklaraci třídy:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 Tím se vytvoří implementace `IPropertyNotifySink` rozhraní s názvem `HeadingFontNotify`. Toto nové rozhraní obsahuje metodu s názvem `OnChanged`.  
  
### <a name="additions-to-the-implementation-file"></a>Přidání do souboru implementace  
 Kód, který inicializuje písmo nadpisu (v konstruktoru ovládací prvek), změňte &*m_xFontNotification* k &*m_xHeadingFontNotify*. Přidejte následující kód:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 `AddRef` a `Release` metody v `IPropertyNotifySink` rozhraní udržování přehledu o počet odkazů pro objekt ovládacího prvku ActiveX. Pokud ovládací prvek získá přístup k rozhraní ukazatele, ovládací prvek volá `AddRef` se zvýší počet odkazů. Po dokončení ovládacího prvku s ukazatele volá `Release`, mnohem stejným způsobem `GlobalFree` může být například k bezplatným blok globální paměť. Pokud počet odkazů pro toto rozhraní přejde na hodnotu nula, může být uvolněno implementaci rozhraní. V tomto příkladu `QueryInterface` funkce vrátí ukazatel na `IPropertyNotifySink` rozhraní pro daný objekt. Tato funkce umožňuje ovládacího prvku ActiveX k dotazování objekt pro určení, co ji rozhraní podporuje.  
  
 Až tyto změny byly provedeny do projektu, projekt znovu sestavte a použít k testování rozhraní Test kontejneru. V tématu [testování vlastností a událostí pomocí Test kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup kontejner testů.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Ovládací prvky MFC ActiveX: Použití obrázků v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

