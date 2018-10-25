---
title: 'MFC – ovládací prvky ActiveX: Použití písem | Dokumentace Microsoftu'
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
ms.openlocfilehash: 8c34b4a842655ebce6fccaa89a1dfc6d4ef49add
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063481"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC – ovládací prvky ActiveX: Použití písem

Pokud ovládací prvek ActiveX zobrazí text, můžete povolit uživateli změnit vzhled textu změnou vlastnosti font. Vlastnosti písma jsou implementovány jako objekty písma a může být jeden ze dvou typů: výchozí nebo vlastní. Uložené vlastnosti písma jsou vlastnosti preimplemented písma, které můžete přidat pomocí Průvodce přidáním vlastnosti. Vlastní vlastnosti písma nejsou preimplemented a developer ovládací prvek určuje chování vlastnosti a využití.

Tento článek obsahuje následující témata:

- [Použití Stock Font – vlastnost](#_core_using_the_stock_font_property)

- [Pomocí vlastností vlastní písma v ovládacím prvku](#_core_implementing_a_custom_font_property)

##  <a name="_core_using_the_stock_font_property"></a> Pomocí vlastností uložených písma

Uložené vlastnosti písma jsou preimplemented třídou [COleControl](../mfc/reference/colecontrol-class.md). Kromě toho je standardní stránek vlastností písma také k dispozici, které uživateli umožňují měnit různé atributy písma objektu, například jeho název, velikost a stylu.

Přístup k objektu písma prostřednictvím [getfont –](../mfc/reference/colecontrol-class.md#getfont), [setfont –](../mfc/reference/colecontrol-class.md#setfont), a [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funkce `COleControl`. Ovládací prvek uživatele bude přístup k objektu písma prostřednictvím `GetFont` a `SetFont` funkce stejně jako jakoukoli jinou vlastnosti Get/Set. Při přístupu k objektu písma je zapotřebí ve směru z v rámci ovládacího prvku, použijte `InternalGetFont` funkce.

Jak je popsáno v [knihovny MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md), přidání uložených vlastností je snadné se [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md). Zvolte vlastnost písma a Průvodce přidáním vlastnosti automaticky vloží uložených písma položku do mapy odbavení ovládacího prvku.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastnost běžného písma pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Otevře se Průvodce přidáním vlastnosti.

1. V **název vlastnosti** klikněte **písmo**.

1. Klikněte na tlačítko **Dokončit**.

Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku mapy odeslání, umístěný v souboru implementace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Kromě toho Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku. Soubor IDL:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Uložené vlastnosti titulku je příkladem text vlastnost, která může vykreslit pomocí informací uložených vlastností písma. Přidání zásob titulek vlastnosti do ovládacího prvku pomocí kroků, které jsou podobné těm, jež používají pro stock Font – vlastnost.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Přidání uložených vlastností titulek, pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Otevře se Průvodce přidáním vlastnosti.

1. V **název vlastnosti** klikněte **titulek**.

1. Klikněte na tlačítko **Dokončit**.

Průvodce přidáním vlastnosti přidá následující řádek do ovládacího prvku mapy odeslání, umístěný v souboru implementace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

##  <a name="_core_modifying_the_ondraw_function"></a> Úprava OnDraw – funkce

Výchozí implementace `OnDraw` používá písmo systému Windows pro všechny text zobrazený v ovládacím prvku. To znamená, že je třeba upravit `OnDraw` kód tak, že vyberete objekt písmo do kontextu zařízení. Chcete-li to provést, zavolejte [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) a předat kontext zařízení ovládacího prvku, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Po `OnDraw` byla změněna funkce použití objektu písma, zobrazí se text v ovládacím prvku pomocí vlastnosti z ovládacího prvku vlastnost běžného písma.

##  <a name="_core_using_custom_font_properties_in_your_control"></a> Pomocí vlastností vlastní písma v ovládacím prvku

Kromě vlastnost běžného písma může mít ovládací prvek ActiveX vlastních vlastností písma. Přidání vlastního písma vlastnosti musíte mít:

- Pomocí Průvodce přidáním vlastnosti k implementaci vlastních vlastností písma.

- [Zpracování oznámení písmo](#_core_processing_font_notifications).

- [Implementace nové rozhraní oznámení písmo](#_core_implementing_a_new_font_notification_interface).

###  <a name="_core_implementing_a_custom_font_property"></a> Implementace vlastnosti vlastní písma

K implementaci vlastních vlastností písma, použijte Průvodce přidáním vlastnosti přidat vlastnosti a pak proveďte určité změny pro kód. Následující části popisují, jak přidat vlastní `HeadingFont` vlastnost Ukázka ovládacího prvku.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní vlastnost písma pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Otevře se Průvodce přidáním vlastnosti.

1. V **název vlastnosti** zadejte název pro vlastnost. V tomto příkladu použijte **HeadingFont**.

1. Pro **typ implementace**, klikněte na tlačítko **metody Get/Set**.

1. V **typ vlastnosti** vyberte **IDispatch** <strong>\*</strong> pro vlastnosti typu.

1. Klikněte na tlačítko **Dokončit**.

Průvodce přidáním vlastnosti vytvoří kód pro přidání `HeadingFont` vlastní vlastnost `CSampleCtrl` třídy a UKÁZKY. Soubor IDL. Protože `HeadingFont` je typ vlastnosti Get/Set, Průvodce přidáním vlastnosti změní `CSampleCtrl` mapa odeslání třídy mají zahrnout DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) – makro položky:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX – makro přidruží `HeadingFont` název vlastnosti k odpovídajícímu `CSampleCtrl` třídy Get a Set metod, `GetHeadingFont` a `SetHeadingFont`. Rovněž je zadán typ vlastnosti; v tomto případě VT_FONT.

Průvodce přidáním vlastnosti také přidá deklaraci v souboru záhlaví ovládacího prvku (. H) pro `GetHeadingFont` a `SetHeadingFont` funkcí a přidává své šablony funkce v souboru implementace ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

A konečně Průvodce přidáním vlastnosti upraví ovládacího prvku. Soubor IDL to přidáním položky pro `HeadingFont` vlastnost:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Změny kódu ovládacího prvku

Teď, když jste přidali `HeadingFont` vlastnosti do ovládacího prvku, je třeba provést některé změny na soubory, které plně podporují novou vlastnost záhlaví a implementace ovládacího prvku.

V souboru záhlaví ovládacího prvku (. H), přidejte následující deklarace proměnné chráněný člen:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

V souboru implementace ovládacího prvku (. CPP), postupujte takto:

- Inicializovat *m_fontHeading* v konstruktoru ovládacího prvku.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Deklarujte statickou FONTDESC strukturu obsahující výchozí atributy písma.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- V ovládacím prvku `DoPropExchange` členské funkci, přidejte volání `PX_Font` funkce. Tímto způsobem, inicializace a trvalosti pro vaši vlastní vlastnost písma.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Dokončení implementace ovládacího prvku `GetHeadingFont` členskou funkci.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Dokončení implementace ovládacího prvku `SetHeadingFont` členskou funkci.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Upravit ovládací prvek `OnDraw` členské funkce definovat proměnnou pro uchování dříve vybraného písma.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Upravit ovládací prvek `OnDraw` členskou funkci k výběru vlastního písma do kontextu zařízení tak, že přidáte následující řádek bez ohledu na to je písmo, který se má použít.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Upravit ovládací prvek `OnDraw` členské funkce vyberte předchozí písmo zpět do kontextu zařízení tak, že přidáte následující řádek po písma se používá.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Poté, co byl implementován vlastních vlastností písma, standardní stránek vlastností písma by měla být implementována, umožnit uživatelům ovládacího prvku, chcete-li změnit písmo ovládacího prvku. Chcete-li přidat ID stránky vlastností pro standardní stránek vlastností písma, vložte následující řádek po BEGIN_PROPPAGEIDS – makro:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Jednou, musíte zvýšit počet parametr vaše BEGIN_PROPPAGEIDS – makro. To ukazuje následující řádek:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Po provedení těchto změn znovu sestavte celý projekt začlenit další funkce.

###  <a name="_core_processing_font_notifications"></a> Zpracování oznámení písma

Ve většině případů je potřeba vědět, kdy byly upraveny vlastnosti objektu písma ovládacího prvku. Každý objekt písma je schopný poskytnout oznámení při změně voláním členské funkce typu `IFontNotification` rozhraní implementované `COleControl`.

Pokud ovládací prvek používá vlastnost běžného písma, jsou zpracovávány jeho oznámení `OnFontChanged` členskou funkci `COleControl`. Při přidání vlastního písma vlastnosti budete moci používat stejné implementaci. V příkladu v předchozí části se toho dosáhlo tím, že předáte &*m_xFontNotification* při inicializaci *m_fontHeading* členské proměnné.

![Implementace rozhraní více objektů písma](../mfc/media/vc373q1.gif "vc373q1") implementovat více rozhraní objektu písma

Zobrazit čáry na obrázku výše, že oba objekty písmo budou používat stejné provádění `IFontNotification`. To může způsobit problémy, kdybyste chtěli změnit písmo rozlišení.

Jedním ze způsobů k rozlišení mezi oznámení objektu font ovládacího prvku je vytvořit samostatné implementace `IFontNotification` rozhraní pro každý objekt písma v ovládacím prvku. Tato technika vám umožní optimalizovat kód výkresu aktualizací pouze řetězec, nebo řetězce, které používají naposledy upravené písma. Následující části ukazují postup potřebný k implementaci rozhraní samostatné oznámení pro druhý vlastnosti Font. Druhou vlastností písma se předpokládá se, že `HeadingFont` vlastnost, která byla přidána v předchozí části.

###  <a name="_core_implementing_a_new_font_notification_interface"></a> Implementace nové rozhraní oznámení písma

K rozlišení mezi oznámení dvě nebo více písem, je nutné implementovat nové rozhraní oznámení pro každou písmo použité v ovládacím prvku. Následující části popisují, jak implementovat nové rozhraní oznámení písma úpravou souborů záhlaví a implementaci ovládacího prvku.

### <a name="additions-to-the-header-file"></a>Přidání do souboru hlaviček

V souboru záhlaví ovládacího prvku (. H), přidejte následující řádky do deklarace třídy:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Tím se vytvoří implementace `IPropertyNotifySink` rozhraní s názvem `HeadingFontNotify`. Toto nové rozhraní obsahuje metodu nazvanou `OnChanged`.

### <a name="additions-to-the-implementation-file"></a>Dodatky k implementační soubor

V kódu, který inicializuje písmo záhlaví (v konstruktoru ovládací prvek), změňte &*m_xFontNotification* k &*m_xHeadingFontNotify*. Přidejte následující kód:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef` a `Release` metody v `IPropertyNotifySink` rozhraní udržovat přehled o počet odkazů pro objekt ovládacího prvku ActiveX. Když ovládací prvek získá přístup k ukazatel rozhraní, ovládací prvek volá `AddRef` se zvýší počet odkazů. Po dokončení se ovládací prvek s ukazatelem, volá `Release`, v skoro stejné způsobu, jakým `GlobalFree` může volat pro uvolnění bloku globální paměti. Když pro toto rozhraní počet odkazů dosáhne nuly, lze jej uvolnit implementace rozhraní. V tomto příkladu `QueryInterface` funkce vrátí ukazatel `IPropertyNotifySink` rozhraní pro daný objekt. Tato funkce umožňuje ovládacího prvku ActiveX k dotazování objektu určit, co je rozhraní podporuje.

Po provedení těchto změn do vašeho projektu, sestavte projekt znovu a použít kontejner testování pro testování rozhraní. Zobrazit [testování vlastností a událostí pomocí testování kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

