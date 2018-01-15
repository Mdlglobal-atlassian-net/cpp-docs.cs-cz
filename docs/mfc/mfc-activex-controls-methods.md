---
title: "Ovládací prvky MFC ActiveX: Metody | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e3b343b13118930612e4adfed4c33a65a9e7be8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-methods"></a>MFC – ovládací prvky ActiveX: Metody
Ovládací prvek ActiveX aktivuje události pro komunikaci mezi samostatně a jeho kontejneru ovládacího prvku. Kontejner může také komunikovat s ovládacím prvkem prostřednictvím metody a vlastnosti. Metody se také nazývají funkce.  
  
 Metody a vlastnosti poskytnout exportovaný rozhraní pro použití jiné aplikace, jako je například klienti automatizace a ActiveX – kontejnery ovládacích prvků. Další informace o vlastnosti ovládacích prvků ActiveX, najdete v článku [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md).  
  
 Metody jsou podobné se používají a účel členské funkce třídy C++. Existují dva typy metod můžete implementovat vlastní ovládací prvek: uložených a vlastní. Podobně jako stock události, stock metody jsou tyto metody pro kterou [COleControl](../mfc/reference/colecontrol-class.md) poskytuje implementaci. Další informace o uložených metod najdete v článku [MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md). Vlastní metody, které jsou definované na vývojáři a povolit další přizpůsobení ovládacího prvku. Další informace najdete v článku [MFC – ovládací prvky ActiveX: Přidání vlastních metod](../mfc/mfc-activex-controls-adding-custom-methods.md).  
  
 Microsoft Foundation Class Library (MFC) implementuje mechanismus, který umožňuje ovládací prvek pro podporu stock a vlastních metod. První část je třída `COleControl`. Odvozené z `CWnd`, `COleControl` členské funkce podporují uložených metod, které jsou společné pro všechny ovládací prvky ActiveX. Druhá část tento mechanismus je expediční mapy. Mapy odesílání je podobná mapy zpráv; ale namísto mapování funkce na ID zpráv systému Windows, mapy odesílání mapuje virtuální členské funkce IDispatch ID.  
  
 Pro ovládací prvek pro podporu různých metodách správně musí deklarovat své třídy expediční mapy. To lze provést následující řádek kódu v záhlaví třídy ovládacího prvku (. H) soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 Hlavním účelem mapy odesílání je k navázání vztahu mezi názvy metoda používaná externí volající (například kontejneru) a členské funkce ovládacího prvku třídy, které implementují metody. Po bylo deklarováno expediční mapy, musí být definován v implementaci ovládacího prvku (. Soubor CPP). Následující řádky kódu definovat mapy odesílání:  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 Pokud jste použili [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md) a vytvořte tak projekt, tyto řádky byly přidány automaticky. Pokud nebyl použit Průvodce ovládacím prvkem ActiveX knihovny MFC, je nutné ručně přidat tyto řádky.  
  
 Následující články popisují metody podrobně:  
  
-   [MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [MFC – ovládací prvky ActiveX: Přidání vlastních metod](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

