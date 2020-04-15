---
title: 'MFC – ovládací prvky ActiveX: Použití písem'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
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
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358262"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC – ovládací prvky ActiveX: Použití písem

Pokud ovládací prvek ActiveX zobrazuje text, můžete uživateli ovládacího prvku povolit změnu vzhledu textu změnou vlastnosti písma. Vlastnosti písma jsou implementovány jako objekty písma a mohou být jedním ze dvou typů: stock nebo custom. Vlastnosti písma stock jsou předem implementované vlastnosti písma, které můžete přidat pomocí Průvodce přidáním vlastností. Vlastní Font vlastnosti nejsou předem implementovány a vývojář ovládacího prvku určuje chování a použití vlastnosti.

Tento článek popisuje následující témata:

- [Použití vlastnosti Stock Font](#_core_using_the_stock_font_property)

- [Použití vlastních vlastností písma v ovládacím prvku](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Použití vlastnosti Skladové písmo

Vlastnosti stock font jsou předem implementovány třídou [COleControl](../mfc/reference/colecontrol-class.md). Kromě toho je k dispozici také standardní stránka vlastností Písmo, která uživateli umožňuje změnit různé atributy objektu písma, například jeho název, velikost a styl.

Přístup k objektu písma prostřednictvím [GetFont](../mfc/reference/colecontrol-class.md#getfont), `COleControl` [SetFont](../mfc/reference/colecontrol-class.md#setfont)a [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funkce . Uživatel ovládacího prvku bude přistupovat k objektu písma `GetFont` prostřednictvím `SetFont` a funguje stejným způsobem jako všechny ostatní Get/Set vlastnost. Pokud je vyžadován přístup k objektu písma `InternalGetFont` z ovládacího prvku, použijte funkci.

Jak je popsáno v [ovládacích prvcích activexu knihovny MFC: Vlastnosti](../mfc/mfc-activex-controls-properties.md), přidání vlastností zásob je snadné pomocí [Průvodce přidáním vlastností](../ide/names-add-property-wizard.md). Zvolíte vlastnost Font a Průvodce přidáním vlastností automaticky vloží položku základního písma do mapy odeslání ovládacího prvku.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Přidání vlastnosti Písmo stock pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Tím se otevře Průvodce přidáním vlastností.

1. V poli **Název vlastnosti** klepněte na **položku Písmo**.

1. Klikněte na **Finish** (Dokončit).

Průvodce přidáním vlastností přidá následující řádek do mapy odeslání ovládacího prvku, který se nachází v souboru implementace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Průvodce přidáním vlastností navíc přidá do ovládacího prvku následující řádek . IDL soubor:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Vlastnost Caption na skladě je příkladem vlastnosti text, kterou lze nakreslit pomocí informací o vlastnostech písma na skladě. Přidání vlastnosti Caption na skladě do ovládacího prvku používá kroky podobné těm, které se používají pro vlastnost Stock Font.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Přidání vlastnosti Titulek na skladě pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Tím se otevře Průvodce přidáním vlastností.

1. V poli **Název vlastnosti** klikněte na **Titulek**.

1. Klikněte na **Finish** (Dokončit).

Průvodce přidáním vlastností přidá následující řádek do mapy odeslání ovládacího prvku, který se nachází v souboru implementace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Úprava funkce OnDraw

Výchozí implementace `OnDraw` používá systémové písmo systému Windows pro veškerý text zobrazený v ovládacím prvku. To znamená, že `OnDraw` je nutné upravit kód výběrem objektu písma do kontextu zařízení. Chcete-li to provést, zavolejte [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) a předejte kontext zařízení ovládacího prvku, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Po `OnDraw` úpravě funkce pro použití objektu písma se zobrazí libovolný text v ovládacím prvku s vlastnostmi z vlastnosti Font ovládacího prvku.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Použití vlastních vlastností písma v ovládacím prvku

Kromě vlastnosti Stock Font může mít ovládací prvek ActiveX vlastní vlastnosti Písma. Chcete-li přidat vlastní vlastnost písma, musíte:

- Pomocí Průvodce přidáním vlastností implementujte vlastní vlastnost Font.

- [Zpracování oznámení písem](#_core_processing_font_notifications).

- [Implementace nového rozhraní pro oznámení písem](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementace vlastní vlastnosti písma

Chcete-li implementovat vlastní vlastnost Font, použijte Průvodce přidáním vlastnosti k přidání vlastnosti a potom proveďte některé změny kódu. Následující části popisují, jak `HeadingFont` přidat vlastní vlastnost do ukázkového ovládacího prvku.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Přidání vlastní vlastnosti Písmo pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Tím se otevře Průvodce přidáním vlastností.

1. Do pole **Název vlastnosti** zadejte název vlastnosti. V tomto příkladu použijte **HeadingFont**.

1. V **souboru Typ implementace**klepněte na tlačítko Získat nebo nastavit **metody**.

1. V poli **Typ vlastnosti** vyberte pro typ vlastnosti položku **IDispatch.** <strong>\*</strong>

1. Klikněte na **Finish** (Dokončit).

Průvodce přidáním vlastností vytvoří `HeadingFont` kód pro `CSampleCtrl` přidání vlastní vlastnosti do třídy a vzorku. IDL. Protože `HeadingFont` je typem vlastnosti Get/Set, Průvodce přidáním vlastností upraví mapu odeslání `CSampleCtrl` třídy tak, aby zahrnovala DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) položku makra:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Makro DISP_PROPERTY_EX `HeadingFont` přidruží název `CSampleCtrl` vlastnosti k odpovídající `GetHeadingFont` `SetHeadingFont`metodě Get and Set a . Je také zadán typ hodnoty vlastnosti; v tomto případě VT_FONT.

Průvodce přidáním vlastností také přidá deklaraci do souboru záhlaví ovládacího prvku (. H) pro `GetHeadingFont` `SetHeadingFont` a funkce a přidá jejich funkce šablony v souboru implementace ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Nakonec Průvodce přidáním vlastností upraví ovládací prvek . IDL přidáním položky `HeadingFont` pro vlastnost:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Změny kontrolního kódu

Nyní, když jste `HeadingFont` přidali vlastnost do ovládacího prvku, musíte provést některé změny záhlaví ovládacího prvku a implementační soubory plně podporovat novou vlastnost.

V souboru záhlaví ovládacího prvku (. H), přidejte následující deklaraci chráněné členské proměnné:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

V souboru implementace ovládacího prvku (. CPP), postupujte takto:

- Inicializovat *m_fontHeading* v konstruktoru ovládacího prvku.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Deklarujte statickou strukturu FONTDESC obsahující výchozí atributy písma.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- V funkci `DoPropExchange` ovládacího člena přidejte `PX_Font` volání funkce. To poskytuje inicializaci a trvalost pro vlastní Font vlastnost.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Dokončete `GetHeadingFont` implementaci funkce člena ovládacího prvku.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Dokončete `SetHeadingFont` implementaci funkce člena ovládacího prvku.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Upravte `OnDraw` členská funkci ovládacího prvku tak, aby definovala proměnnou pro uložení dříve vybraného písma.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Upravte `OnDraw` členská funkci ovládacího prvku tak, aby vyberte vlastní písmo do kontextu zařízení přidáním následujícího řádku všude tam, kde má být písmo použito.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Upravte `OnDraw` funkci člena ovládacího prvku a vyberte předchozí písmo zpět do kontextu zařízení přidáním následujícího řádku po použití písma.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Po implementaci vlastní vlastnosti Font by měla být implementována stránka vlastnosti standardní písmo, což uživatelům ovládacího prvku umožňuje změnit aktuální písmo ovládacího prvku. Chcete-li přidat ID stránky vlastností pro stránku vlastností standardní písmo, vložte za makro BEGIN_PROPPAGEIDS následující řádek:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Je také nutné povýšit parametr počtu BEGIN_PROPPAGEIDS makra o jednu. Následující řádek ilustruje toto:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Po provedené tyto změny, znovu sestavit celý projekt začlenit další funkce.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Zpracování oznámení písem

Ve většině případů ovládací prvek potřebuje vědět, kdy byly změněny vlastnosti objektu písma. Každý objekt písma je schopen poskytovat oznámení při změně `IFontNotification` voláním členské `COleControl`funkce rozhraní implementované ho .

Pokud ovládací prvek používá vlastnost stock Font, jeho `OnFontChanged` oznámení `COleControl`jsou zpracována členovou funkcí . Když přidáte vlastní vlastnosti písma, můžete je nechat používat stejnou implementaci. V příkladu v předchozí části to bylo provedeno předáním &*m_xFontNotification* při inicializaci m_fontHeading *členské* proměnné.

![Implementace více rozhraní objektů písma](../mfc/media/vc373q1.gif "Implementace více rozhraní objektů písma") <br/>
Implementace rozhraní s více objekty písem

Plné čáry na obrázku výše ukazují, že oba `IFontNotification`objekty písma používají stejnou implementaci aplikace . To by mohlo způsobit problémy, pokud chcete rozlišit, které písmo se změnilo.

Jedním ze způsobů, jak rozlišovat mezi oznámení mise objektu `IFontNotification` písma ovládacího prvku je vytvořit samostatnou implementaci rozhraní pro každý objekt písma v ovládacím prvku. Tato technika umožňuje optimalizovat kód výkresu aktualizací pouze řetězce nebo řetězce, které používají nedávno upravené písmo. Následující části ukazují kroky nezbytné k implementaci samostatné oznámení rozhraní pro druhou Font vlastnost. Druhá vlastnost písma je `HeadingFont` považována za vlastnost, která byla přidána v předchozí části.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementace nového rozhraní pro oznámení písem

Chcete-li rozlišovat mezi oznámení midvě nebo více písem, musí být implementována nové rozhraní oznámení pro každé písmo použité v ovládacím prvku. Následující části popisují, jak implementovat nové rozhraní oznámení písma úpravou záhlaví ovládacího prvku a soubory implementace.

### <a name="additions-to-the-header-file"></a>Dodatky k souboru záhlaví

V souboru záhlaví ovládacího prvku (. H), přidejte do deklarace třídy následující řádky:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Tím se vytvoří `IPropertyNotifySink` implementace `HeadingFontNotify`rozhraní s názvem . Toto nové rozhraní `OnChanged`obsahuje metodu nazvanou .

### <a name="additions-to-the-implementation-file"></a>Dodatky k prováděcímu souboru

V kódu, který inicializuje písmo nadpisu (v konstruktoru ovládacího prvku), změňte &*m_xFontNotification* na &*m_xHeadingFontNotify*. Pak přidejte následující kód:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Metody `AddRef` `Release` a v `IPropertyNotifySink` rozhraní sledují počet odkazů pro řídicí objekt ActiveX. Když ovládací prvek získá přístup k ukazatel `AddRef` rozhraní, ovládací prvek volá zvýšení počtu odkazů. Po dokončení ovládacího prvku s ukazatelem volání `Release`, v `GlobalFree` podstatě stejným způsobem, který může být volána k uvolnění bloku globální paměti. Při počet odkazů pro toto rozhraní přejde na nulu, implementace rozhraní může být uvolněna. V tomto příkladu `QueryInterface` funkce vrátí `IPropertyNotifySink` ukazatel na rozhraní na konkrétní objekt. Tato funkce umožňuje ovládacímu prvku ActiveX dotazovat objekt k určení rozhraní, která podporuje.

Po tyto změny byly provedeny v projektu, znovu sestavit projekt a pomocí testovacího kontejneru k testování rozhraní. Informace o tom, jak získat přístup k testovacímu kontejneru, najdete v tématu [Testování vlastností a událostí s testovacím kontejnerem.](../mfc/testing-properties-and-events-with-test-container.md)

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)
