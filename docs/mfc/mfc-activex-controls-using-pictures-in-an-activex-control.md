---
title: 'MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LPPICTUREDISP
dev_langs:
- C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a734e51f298f7f092dde341479293bad3a2d9434
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072678"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX

Tento článek popisuje běžné typ obrázku a jak implementovat v ovládacím prvku ActiveX. Mezi témata patří:

- [Přehled vlastnosti vlastního obrázku](#_core_overview_of_custom_picture_properties)

- [Implementace vlastnosti vlastní obrázek v ovládacím prvku ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Přidání do projektu ovládacího prvku](#_core_additions_to_your_control_project)

##  <a name="_core_overview_of_custom_picture_properties"></a> Přehled vlastnosti vlastního obrázku

Typ obrázku je součástí skupiny typů, které jsou společné pro některé ovládací prvky ActiveX. Typ obrázku zpracovává metasoubory, rastrové obrázky a ikony a umožňuje uživateli zadat obrázek, který se má zobrazit v ovládacím prvku ActiveX. Vlastní vlastnosti obrázku jsou implementovány pomocí objektu obrázek a funkce Get/Set, které umožňují řízení přístupu uživatelů k vlastnosti obrázku. Ovládací prvek uživatelé přístup k vlastní vlastnost obrázek pomocí akcie stránka vlastností obrázku.

Kromě standardní typ obrázku, písma a barvy typy jsou také k dispozici. Další informace o použití standardní typ písma v ovládacím prvku ActiveX, najdete v článku [knihovny MFC – ovládací prvky ActiveX: použití písem](../mfc/mfc-activex-controls-using-fonts.md).

Třídy ovládacích prvků ActiveX poskytují několik komponent, které můžete použít k implementaci vlastnost obrázek v ovládacím prvku. Mezi tyto komponenty patří:

- [Cpictureholder –](../mfc/reference/cpictureholder-class.md) třídy.

   Tato třída poskytuje snadný přístup k objektu obrázek a funkce pro položky zobrazí ve vlastní vlastnosti obrázku.

- Podpora pro vlastnosti typu **LPPICTUREDISP**, implementovaný pomocí funkce Get/Set.

   Pomocí zobrazení tříd můžete rychle přidat vlastní vlastnost nebo vlastnosti, která podporuje typ obrázku. Další informace o přidání vlastnosti ovládacích prvků ActiveX pomocí zobrazení tříd, najdete v článku [knihovny MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md).

- Stránky vlastností, která zpracovává ovládacího prvku obrázek vlastnost nebo vlastnosti.

   Tuto stránku vlastností je součástí skupiny stránky uložených vlastností, které jsou k dispozici pro ovládací prvky ActiveX. Další informace na stránkách vlastností ovládacího prvku ActiveX, najdete v článku [knihovny MFC – ovládací prvky ActiveX: pomocí stránky vlastností akcií](../mfc/mfc-activex-controls-using-stock-property-pages.md)

##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> Implementace vlastnosti vlastní obrázek v ovládacím prvku ActiveX

Po dokončení kroků uvedených v této části ovládací prvek mohl zobrazit obrázky, kterou uživatel zvolí. Uživatel může změnit zobrazeného obrázku pomocí stránky vlastností, která zobrazuje aktuální obrázek a obsahuje tlačítko Procházet, který umožňuje uživateli vybrat různé obrázky.

Vlastní vlastnost obrázek se implementuje pomocí procesu podobný použít k implementaci dalších vlastností, hlavním rozdílem, že se vlastnost vlastní musí podporovat typ obrázku. Protože je nutné vykreslit položku vlastnost obrázek v ovládacím prvku ActiveX, počet dodatků a změn třeba vlastnosti předtím, než může být plně implementovány.

K implementaci vlastní vlastnosti obrázku, postupujte takto:

- [Přidejte kód do ovládacího prvku projektu](#_core_additions_to_your_control_project).

   Standardní obrázek vlastnost ID stránky, datový člen typu `CPictureHolder`a vlastní vlastnost typu **LPPICTUREDISP** s Get/Set musí být přidán implementace.

- [Upravit několik funkcí ve třídě ovládacího prvku](#_core_modifications_to_your_control_project).

   Tyto změny bude proveden několik funkcí, které jsou zodpovědné za vykreslování ovládacího prvku ActiveX.

##  <a name="_core_additions_to_your_control_project"></a> Přidání do projektu ovládacího prvku

Chcete-li přidat ID stránky vlastností pro standardní stránku vlastností obrázek, vložíte následující řádek po BEGIN_PROPPAGEIDS – makro v souboru implementace ovládacího prvku (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Jednou, musíte zvýšit počet parametr vaše BEGIN_PROPPAGEIDS – makro. To ukazuje následující řádek:

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Chcete-li přidat `CPictureHolder` datový člen třídy ovládací prvek vložíte následující řádek chráněné části deklarace třídy ovládacího prvku v souboru záhlaví ovládacího prvku (. H):

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Není nutné pojmenovat datový člen *m_pic*; bude stačit libovolný název.

V dalším kroku přidejte vlastní vlastnost, která podporuje typ obrázku:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní obrázek vlastnosti pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce zvolte **přidat** a potom **přidat vlastnost**.

1. V **název vlastnosti** zadejte název vlastnosti. Například účely `ControlPicture` se používá v tomto postupu.

1. V **typ vlastnosti** vyberte **IPictureDisp** <strong>\*</strong> pro tento typ vlastnosti.

1. Pro **typ implementace**, klikněte na tlačítko **metody Get/Set**.

1. Zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy. (V tomto příkladu výchozí názvy `GetControlPicture` a `SetControlPicture` se používají.)

9. Klikněte na tlačítko **Dokončit**.

Průvodce přidáním vlastnosti přidá následující kód mezi komentáře mapy odbavení v záhlaví ovládacího prvku (. H) file:

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Kromě toho mapy odbavení implementace ovládacího prvku vložila následující kód (. Soubor CPP):

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Průvodce přidáním vlastnosti také přidá následující dva zástupné procedury funkcí v souboru implementace ovládacího prvku:

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
>  Názvy třídy a funkce ovládacího prvku mohou lišit od výše uvedený příklad.

###  <a name="_core_modifications_to_your_control_project"></a> Úpravy do projektu ovládacího prvku

Po provedení potřebné dodatky k řízení projektu, budete muset upravit několik funkcí, které mají vliv vykreslování ovládacího prvku ActiveX. Tyto funkce `OnResetState`, `OnDraw`, a funkce Get/Set vlastní vlastnosti obrázku, jsou umístěny v souboru implementace ovládacího prvku. (Všimněte si, že v tomto příkladu třída ovládacího prvku se nazývá `CSampleCtrl`, `CPictureHolder` se nazývá datový člen *m_pic*, a název vlastnosti vlastního obrázku je `ControlPicture`.)

V ovládacím prvku `OnResetState` funkci, přidejte následující volitelné řádek po volání `COleControl::OnResetState`:

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Tím se nastaví obrázek ovládacího prvku obrázku prázdná.

Chcete-li nakreslit obrázek správně, ujistěte se, volání [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) v ovládacím prvku `OnDraw` funkce. Upravte funkce vypadat podobně jako v následujícím příkladu:

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

Ve funkci Get vlastnosti vlastní obrázek ovládacího prvku přidejte následující řádek:

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

Ve funkci Set vlastnosti vlastní obrázek ovládacího prvku přidejte následující řádky:

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Vlastnost obrázek se musí provádět trvalé tak, aby se zobrazí informace o přidaných v době návrhu v době běhu. Přidejte následující řádek, který `COleControl`-odvozené třídy `DoPropExchange` funkce:

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
>  Názvy třídy a funkce se mohou lišit od výše uvedený příklad.

Po dokončení změny znovu sestavte projekt nové funkce vlastnost vlastní obrázek začlenění a používání kontejner testu otestovat novou vlastnost. Zobrazit [testování vlastností a událostí pomocí testování kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Použití písem](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

