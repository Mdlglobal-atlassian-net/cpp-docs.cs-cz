---
title: "Ovládací prvky MFC ActiveX: Použití obrázků v ovládacím prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LPPICTUREDISP
dev_langs: C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a27e5ebb58056dfd14417adea211daf2c6ac2ddf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX
Tento článek popisuje běžné typ obrázku a jak implementovat vaše ovládacího prvku ActiveX. Témata zahrnují:  
  
-   [Přehled vlastností vlastní obrázek](#_core_overview_of_custom_picture_properties)  
  
-   [Implementace vlastnosti vlastní obrázek ve vašem ovládacím prvku ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)  
  
-   [Přidání do projektu ovládací prvek](#_core_additions_to_your_control_project)  
  
##  <a name="_core_overview_of_custom_picture_properties"></a>Přehled vlastností vlastní obrázek  
 Typ obrázku je jedním ze skupiny typů, které jsou společné pro některé ovládací prvky ActiveX. Typ obrázku zpracovává metasoubory, rastrové obrázky nebo ikon a umožní uživateli zadat obrázek, který se má zobrazit v ovládacím prvku ActiveX. Vlastní vlastnosti obrázku jsou implementovány pomocí objektu obrázku a Get/Set funkce, které umožňují přístup uživatelů řízení vlastnosti obrázek. Ovládací prvek uživatelé přístup k vlastní vlastnosti obrázek pomocí stock stránka vlastností obrázku.  
  
 Kromě standardní typ obrázku jsou také písma a barev typy k dispozici. Další informace o použití standardní typ písma v vaše ovládací prvek ActiveX, najdete v článku [MFC – ovládací prvky ActiveX: použití písem](../mfc/mfc-activex-controls-using-fonts.md).  
  
 Třídy ovládacích prvků ActiveX poskytují několik komponent, které můžete použít k implementaci vlastnost obrázků v ovládacím prvku. Tyto součásti zahrnují:  
  
-   [CPictureHolder](../mfc/reference/cpictureholder-class.md) třídy.  
  
     Tato třída poskytuje snadný přístup k objektu obrázku a funkce pro položku, zobrazí vlastnost vlastní obrázek.  
  
-   Podpora pro vlastnosti typu **LPPICTUREDISP**, implementovaná pomocí funkce Get/Set.  
  
     Pomocí zobrazení tříd rychle přidáte vlastní vlastnosti a vlastnosti, která podporuje typ obrázku. Další informace o přidání vlastností ovládacího prvku ActiveX s zobrazení tříd, najdete v článku [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md).  
  
-   Stránky vlastností, které pracují se vlastnosti nebo vlastnosti Obrázek ovládacího prvku.  
  
     Tato stránka vlastností je součástí skupiny stránek uložených vlastností, které jsou k dispozici pro ovládací prvky ActiveX. Další informace o stránky vlastností ovládacího prvku ActiveX, najdete v článku [MFC – ovládací prvky ActiveX: použití Stock stránky vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementace vlastnosti vlastní obrázek ve vašem ovládacím prvku ActiveX  
 Po dokončení kroků uvedených v této části můžete ovládací prvek zobrazit obrázky vybrali jeho uživatelem. Uživatel může změnit zobrazeného obrázku pomocí stránku vlastností, která ukazuje na aktuální obrázku a má tlačítko Procházet, která umožňuje uživatelům vyberte jiný obrázky.  
  
 Vlastní vlastnost obrázek se implementuje pomocí procesu podobná použít k implementaci ostatní vlastnosti hlavním rozdílem, že vlastní vlastnost musí podporovat typ obrázku. Protože je nutné vykreslit položku vlastnost obrázek ovládací prvek ActiveX, musí být počet přidání a úpravy provedeny pro vlastnost předtím, než může být plně implementováno.  
  
 Chcete-li implementovat vlastní vlastnosti obrázku, musíte udělat následující:  
  
-   [Přidejte do projektu řízení kód](#_core_additions_to_your_control_project).  
  
     Standardní obrázek vlastnost ID stránky, člena typu `CPictureHolder`a vlastní vlastnost typu **LPPICTUREDISP** s Get/Set, musí být přidaný implementace.  
  
-   [Upravit několik funkce ve třídě ovládacího](#_core_modifications_to_your_control_project).  
  
     Tyto změny budou provedeny několik funkcí, které jsou zodpovědní za vykreslování ovládacího prvku ActiveX.  
  
##  <a name="_core_additions_to_your_control_project"></a>Přidání do projektu ovládací prvek  
 Chcete-li přidat ID stránky vlastností pro standardní stránku vlastností obrázku, vložte následující řádek po `BEGIN_PROPPAGEIDS` makro v řídicím souboru implementace (. CPP):  
  
 [!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]  
  
 Musíte také zvýšit počet parametru vaší `BEGIN_PROPPAGEIDS` makro o jednu. To ukazuje následující řádek:  
  
 [!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]  
  
 Chcete-li přidat `CPictureHolder` – datový člen třídy ovládacího prvku, vložte následující řádek chráněné části deklarace třídy ovládacího prvku v záhlaví souboru ovládacího prvku (. H):  
  
 [!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]  
  
 Není nutné pojmenovat datový člen `m_pic`; postačí libovolný název.  
  
 V dalším kroku přidejte vlastní vlastnost, která podporuje typ obrázku:  
  
#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní obrázek vlastnosti pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce vyberte příkaz **přidat** a potom **přidat vlastnost**.  
  
5.  V **název vlastnosti** zadejte název vlastnosti. Například účely, `ControlPicture` se používá v tomto postupu.  
  
6.  V **typ vlastnosti** vyberte **IPictureDisp\***  pro typ vlastnosti.  
  
7.  Pro **typem implementace**, klikněte na tlačítko **metody Get/Set**.  
  
8.  Zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy. (V tomto příkladu výchozí názvy `GetControlPicture` a `SetControlPicture` se používají.)  
  
9. Klikněte na tlačítko **Dokončit**.  
  
 Průvodce přidáním vlastnosti přidá následující kód mezi poznámky mapy odesílání v hlavičce ovládací prvek (. H) soubor:  
  
 [!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]  
  
 Kromě toho následující kód byl vložen do mapy odesílání implementace ovládacího prvku (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]  
  
 Průvodce přidáním vlastnosti také přidá následující funkce dva se zakázaným inzerováním v řídicím souboru implementace:  
  
 [!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]  
  
> [!NOTE]
>  Názvy třídy a funkce řízení může lišit od příkladu nahoře.  
  
###  <a name="_core_modifications_to_your_control_project"></a>Úpravy řízení projektu  
 Po provedení potřebné dodatky do projektu ovládací prvek, budete muset upravit několik funkcí, které ovlivňují vykreslování ovládacího prvku ActiveX. Tyto funkce `OnResetState`, `OnDraw`, a funkce Get/Set vlastní vlastnosti obrázku, jsou umístěné v řídicím souboru implementace. (Všimněte si, že v tomto příkladu třída ovládacích prvků se nazývá `CSampleCtrl`, `CPictureHolder` – datový člen nazývá `m_pic`, a název vlastnosti vlastní obrázek je `ControlPicture`.)  
  
 V ovládacím prvku `OnResetState` fungovat, přidejte následující řádek volitelné po volání `COleControl::OnResetState`:  
  
 [!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]  
  
 Toto nastaví obrázek ovládacího prvku do prázdné obrázku.  
  
 Kreslení obrázku správně, ujistěte se, volání [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) v ovládacím prvku `OnDraw` funkce. Upravte funkce tak, aby připomínaly v následujícím příkladu:  
  
 [!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]  
  
 Ve funkci Get vlastní obrázek ovládacího prvku přidejte následující řádek:  
  
 [!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]  
  
 Ve funkci Set ovládacího prvku vlastní vlastnosti obrázku přidejte následující řádky:  
  
 [!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]  
  
 Vlastnost Obrázek musí být provedeny trvalé, tak, aby v době běhu se zobrazí informace o přidaných v době návrhu. Přidejte následující řádek na `COleControl`-odvozené třídy `DoPropExchange` funkce:  
  
 [!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]  
  
> [!NOTE]
>  Názvy třídy a funkce se může lišit od příkladu nahoře.  
  
 Po dokončení změny znovu sestavte projekt začlenění nové funkce vlastní obrázek vlastnosti a k otestování nové vlastnosti použít testovací kontejneru. V tématu [testování vlastností a událostí pomocí Test kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup kontejner testů.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Ovládací prvky MFC ActiveX: Použití písem](../mfc/mfc-activex-controls-using-fonts.md)   
 [MFC – ovládací prvky ActiveX: Stránky vlastností](../mfc/mfc-activex-controls-property-pages.md)

