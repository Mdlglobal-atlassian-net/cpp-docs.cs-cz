---
title: 'MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX'
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 1f78823f39417ff6928a1b915d83507bc1ac9526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358294"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX

Tento článek popisuje běžný typ obrázku a jeho implementaci v ovládacím prvku ActiveX. Témata:

- [Přehled vlastních vlastností obrázku](#_core_overview_of_custom_picture_properties)

- [Implementace vlastní vlastnosti obrázku v ovládacím prvku ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Přírůstky do projektu řízení](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a>Přehled vlastních vlastností obrázku

Typ Obrázek je jedním ze skupiny typů, které jsou společné pro některé ovládací prvky ActiveX. Typ Obrázek zpracovává metasoubory, bitmapy nebo ikony a umožňuje uživateli zadat obrázek, který se má zobrazit v ovládacím prvku ActiveX. Vlastní picture vlastnosti jsou implementovány pomocí objektu obrázku a Get/Set funkce, které umožňují uživateli řízení přístup k Picture vlastnost. Pomocí stránky vlastností Obrázek můžete řídit uživatele přístup k vlastní vlastnosti Obrázek.

Kromě standardního typu Obrázek jsou k dispozici také typy písma a barev. Další informace o použití standardního typu písma v ovládacím prvku ActiveX naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Použití písem](../mfc/mfc-activex-controls-using-fonts.md).

Třídy ovládacího prvku ActiveX poskytují několik součástí, které můžete použít k implementaci vlastnosti Picture v rámci ovládacího prvku. Mezi tyto součásti patří:

- Třída [CPictureHolder.](../mfc/reference/cpictureholder-class.md)

   Tato třída poskytuje snadný přístup k objektu obrázku a funkce pro položku zobrazenou vlastní picture vlastnost.

- Podpora vlastností typu **LPPICTUREDISP**, implementována pomocí funkcí Get/Set.

   Pomocí zobrazení tříd můžete rychle přidat vlastní vlastnost nebo vlastnosti, které podporují typ Obrázek. Další informace o přidávání vlastností ovládacího prvku ActiveX pomocí zobrazení tříd naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Vlastnosti](../mfc/mfc-activex-controls-properties.md).

- Stránka vlastností, která manipuluje s vlastností nebo vlastnostmi picture ovládacího prvku.

   Tato stránka vlastností je součástí skupiny stránek vlastností akcií, které jsou k dispozici ovládacím prvkům ActiveX. Další informace o stránkách vlastností ovládacího prvku ActiveX naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Použití stránek vlastností skladových zásob](../mfc/mfc-activex-controls-using-stock-property-pages.md)

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementace vlastní vlastnosti obrázku v ovládacím prvku ActiveX

Po dokončení kroků popsaných v této části může ovládací prvek zobrazit obrázky vybrané jeho uživatelem. Uživatel může změnit zobrazený obrázek pomocí stránky vlastností, která zobrazuje aktuální obrázek a má tlačítko Procházet, které umožňuje uživateli vybrat různé obrázky.

Vlastní Picture vlastnost je implementována pomocí procesu podobného, který se používá pro implementaci jiných vlastností, hlavní rozdíl je, že vlastní vlastnost musí podporovat typ Obrázek. Vzhledem k tomu, že položka Picture vlastnost musí být vypracován ovládací prvek ActiveX, musí být provedeno několik dodatků a úprav vlastnosti před ji lze plně implementovat.

Chcete-li implementovat vlastní vlastnost Picture, musíte provést následující kroky:

- [Přidejte kód do řídicího projektu](#_core_additions_to_your_control_project).

   Musí být přidáno standardní ID stránky `CPictureHolder`vlastností Obrázek, datový člen typu a vlastní vlastnost typu **LPPICTUREDISP** s implementací Get/Set.

- [Upravte několik funkcí ve třídě ovládacího prvku](#_core_modifications_to_your_control_project).

   Tyto změny budou provedeny v několika funkcích, které jsou zodpovědné za kreslení ovládacího prvku ActiveX.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a>Přírůstky do projektu řízení

Chcete-li přidat ID stránky vlastností pro standardní stránku vlastností Obrázek, vložte následující řádek za BEGIN_PROPPAGEIDS makro do souboru implementace ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Je také nutné povýšit parametr počtu BEGIN_PROPPAGEIDS makra o jednu. Následující řádek ilustruje toto:

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Chcete-li `CPictureHolder` přidat datový člen do třídy ovládacího prvku, vložte následující řádek pod chráněnou část deklarace třídy ovládacího prvku do souboru záhlaví ovládacího prvku (. H):

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Není nutné pojmenovat váš datový člen *m_pic*; jakékoliv jméno bude stačit.

Dále přidejte vlastní vlastnost, která podporuje typ obrázek:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Přidání vlastní vlastnosti obrázku pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce zvolte **Přidat** a pak **Přidat vlastnost**.

1. Do pole **Název vlastnosti** zadejte název vlastnosti. Pro například `ControlPicture` účely, se používá v tomto postupu.

1. V poli **Typ vlastnosti** vyberte **iPictureDisp** <strong>\*</strong> pro typ vlastnosti.

1. V **souboru Typ implementace**klepněte na tlačítko Získat nebo nastavit **metody**.

1. Zadejte jedinečné názvy funkcí Get and Set nebo přijměte výchozí názvy. (V tomto příkladu `GetControlPicture` jsou `SetControlPicture` použity výchozí názvy a jsou používány.)

1. Klikněte na **Finish** (Dokončit).

Průvodce přidáním vlastností přidá následující kód mezi komentáře mapy odeslání v záhlaví ovládacího prvku (. H) soubor:

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Kromě toho byl do mapy odeslání implementace ovládacího prvku vložen následující kód (. CPP) soubor:

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Průvodce přidáním vlastností také přidá následující dvě funkce se zakázaným inzerováním do souboru implementace ovládacího prvku:

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Názvy tříd a funkcí ovládacího prvku se mohou lišit od výše uvedeného příkladu.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a>Úpravy řídicího projektu

Po provedení nezbytných dodatků k řídicímu projektu je třeba upravit několik funkcí, které ovlivňují vykreslování ovládacího prvku ActiveX. Tyto funkce `OnResetState` `OnDraw`, , a Get/Set funkce vlastní Picture vlastnost, jsou umístěny v souboru implementace ovládacího prvku. (Všimněte si, že v `CSampleCtrl`tomto `CPictureHolder` příkladu se nazývá třída ovládacího prvku `ControlPicture`, datový člen se nazývá *m_pic*a vlastní název vlastnosti obrázku je .)

Do funkce `OnResetState` řízení přidejte následující volitelnou `COleControl::OnResetState`čáru za volání do :

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Tím se obrázek ovládacího prvku nastaví na prázdný obrázek.

Chcete-li obrázek nakreslit správně, zavolejte [cPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) v ovládací `OnDraw` funkci. Upravte funkci tak, aby se podobala následujícímu příkladu:

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

Do funkce Get vlastní vlastnost iobrázku ovládacího prvku přidejte následující řádek:

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

Do funkce Set vlastní vlastnostI Obrázek ovládacího prvku přidejte následující řádky:

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Vlastnost obrázek musí být trvalá, aby se informace přidané v době návrhu zobrazovaly za běhu. Do `COleControl` `DoPropExchange` funkce odvozené třídy -derived přidejte následující řádek:

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Názvy tříd a funkcí se mohou lišit od výše uvedeného příkladu.

Po dokončení změn znovu sestavte projekt tak, aby zahrnoval nové funkce vlastní vlastnosti Picture, a pomocí testovacího kontejneru otestujte novou vlastnost. Informace o tom, jak získat přístup k testovacímu kontejneru, najdete v tématu [Testování vlastností a událostí s testovacím kontejnerem.](../mfc/testing-properties-and-events-with-test-container.md)

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Použití písem](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)
