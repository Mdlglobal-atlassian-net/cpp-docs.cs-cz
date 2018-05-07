---
title: 'Ovládací prvky MFC ActiveX: Přidání přizpůsobených vlastností | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc3aa3f7aa8b6f4abf28c12a11f75540f59238e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností
Vlastní vlastnosti se liší od uložených vlastností, že vlastní vlastnosti nejsou už implementované `COleControl` třídy. Vlastní vlastnost se používá ke zveřejnění stavu nebo vzhledu ovládacího prvku ActiveX pro programátory, pomocí ovládacího prvku.  
  
 Tento článek popisuje, jak přidat vlastní vlastnosti do ovládacího prvku ActiveX pomocí Průvodce přidáním vlastnosti a vysvětluje výsledné změny kódu. Témata zahrnují:  
  
-   [Pomocí Průvodce přidáním vlastnosti přidáte vlastní vlastnosti](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [Přidat vlastnost průvodce změní pro vlastní vlastnosti](#_core_classwizard_changes_for_custom_properties)  
  
 Vlastní vlastnosti mají čtyři typy implementace: členské proměnné, členské proměnné s Parameterized, oznámení a metody Get/Set.  
  
-   Implementace členské proměnné  
  
     Tato implementace představuje stav vlastnosti jako členské proměnné ve třídě ovládacího prvku. Členské proměnné implementace použijte, když není důležité vědět, kdy se změní hodnota vlastnosti. Tato implementace tři typy vytvoří minimem kód podpory pro vlastnost. Makro položka mapy odesílání pro implementace členské proměnné je [disp_property –](../mfc/reference/dispatch-maps.md#disp_property).  
  
-   Členské proměnné s implementací oznámení  
  
     Tato implementace se skládá z členské proměnné a funkce oznámení vytvořený pomocí průvodce přidat vlastnost. Funkce oznámení je automaticky voláno rámcem po změně hodnoty vlastnosti. Použijte když potřebujete upozorněni po změně hodnoty vlastnosti s implementací oznámení proměnné členů. Tato implementace vyžaduje více času, protože vyžaduje volání funkce. Makro položka mapy odeslání pro tuto implementaci je [disp_property_notify –](../mfc/reference/dispatch-maps.md#disp_property_notify).  
  
-   Implementace metody GET nebo nastavení  
  
     Tato implementace se skládá z dvojice členské funkce ve třídě ovládacího prvku. Implementace metody Get/Set automaticky volá člen Get funkce při ovládacího prvku uživatel požádá o aktuální hodnota vlastnosti a funkce členů sady, pokud ovládacího prvku uživatel požádá o změnit vlastnost. Tuto implementaci používejte třeba k výpočtu hodnoty vlastnosti za běhu, ověřte hodnotu předanou ovládacího prvku uživatele před změnou skutečné vlastnost, nebo implementaci typ vlastnosti jen pro čtení nebo zápisu. Makro položka mapy odeslání pro tuto implementaci je [disp_property_ex –](../mfc/reference/dispatch-maps.md#disp_property_ex). V následující části [pomocí Průvodce přidáním vlastnosti přidáte vlastní vlastnost](#_core_using_classwizard_to_add_a_custom_property), používá vlastní vlastnost CircleOffset k předvedení tuto implementaci.  
  
-   Parametrizované implementace  
  
     Parametrizované implementace podporuje Průvodce přidáním vlastnosti. Parametrizovaná vlastnost (někdy nazývané vlastnost pole) slouží pro přístup k sadu hodnot prostřednictvím jedné vlastnosti ovládacího prvku. Makro položka mapy odeslání pro tuto implementaci je `DISP_PROPERTY_PARAM`. Další informace o implementaci tohoto typu, najdete v části [implementace Parametrizovaná vlastnost](../mfc/mfc-activex-controls-advanced-topics.md) v článku – ovládací prvky ActiveX: Advanced témata.  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> Pomocí Průvodce přidáním vlastnosti přidat vlastní vlastnosti  
 Následující postup předvádí, přidání vlastní vlastnosti, CircleOffset, který používá implementace metody Get/Set. Vlastní vlastnost CircleOffset umožňuje uživatelům ovládacího prvku posun kruhu z centra ohraničující obdélník ovládacího prvku. Je velmi podobný postup pro přidání vlastních vlastností s implementace než metody Get/Set.  
  
 Stejný postup lze také přidat další požadované vlastní vlastnosti. Nahraďte název vlastní vlastnost pro název vlastnosti CircleOffset a parametry.  
  
#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastní vlastnost CircleOffset pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).  
  
5.  V **název vlastnosti** zadejte `CircleOffset`.  
  
6.  Pro **typem implementace**, klikněte na tlačítko **metody Get/Set**.  
  
7.  V **typ vlastnosti** vyberte **krátké**.  
  
8.  Zadejte jedinečné názvy pro získání a nastavení funkce nebo přijměte výchozí názvy.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> Přidat vlastnost průvodce změní pro vlastní vlastnosti  
 Když přidáte vlastní vlastnost CircleOffset, Průvodce přidáním vlastnosti provede změny v hlavičce (. H) a implementaci (. Soubory CPP) třídy ovládacího prvku.  
  
 Následující řádky jsou přidány do. Soubor H deklarovat dvě funkce volané `GetCircleOffset` a `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 Následující řádek je přidán do ovládacího prvku. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 Tento řádek přiřadí vlastnost CircleOffset na konkrétní číslo ID převzaty z metody pozici v seznamu metod a vlastností, Průvodce přidáním vlastnosti.  
  
 Kromě toho se přidá následující řádek na mapě odeslání (v. Soubor CPP třídy ovládacího prvku) pro mapování vlastnost CircleOffset na dvě funkce obslužná rutina ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 Nakonec implementace `GetCircleOffset` a `SetCircleOffset` funkce jsou přidány na konec ovládacího prvku. Soubor CPP. Ve většině případů budete upravovat Get funkce vrátí hodnotu vlastnosti. Funkce sady bude obvykle obsahovat kód, který se má provést před nebo po provedení změn vlastnosti.  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 Všimněte si, že Průvodce přidáním vlastnosti automaticky přidá volání, na [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), k tělu funkci Set. Ovládací prvek volání této funkce označí, jako jsou změny. Pokud byl upraven ovládacího prvku, jeho nového stavu bude uloženo při uložení kontejneru. Tato funkce by měla být volána při každé změně hodnoty vlastnosti, jako součást trvalý stav ovládacího prvku, uložit.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)
