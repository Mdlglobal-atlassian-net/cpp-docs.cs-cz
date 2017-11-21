---
title: "Postupy: vytvoření mapy zpráv pro třídu šablony | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73f6812b1dcc4652c1cb984ddb0ca67f3e72f631
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Postupy: Vytvoření mapy zpráv pro třídu šablony
Mapování zpráv v prostředí MFC poskytuje účinný způsob, jak přímé zpráv systému Windows na instanci objektu příslušné C++. Příklady cílů mapy zpráv knihovny MFC: třídy aplikace, třídy dokumentů a zobrazení, – třídy ovládacích prvků a tak dále.  
  
 Tradiční mapy zpráv knihovny MFC jsou deklarováno s použitím [begin_message_map –](reference/message-map-macros-mfc.md#begin_message_map) makro deklarovat spuštění mapy zpráv, makro záznam pro každou metodu třídu obslužné rutiny zpráv a nakonec [end_message_map –](reference/message-map-macros-mfc.md#end_message_map)makro deklarovat konec mapy zpráv.  
  
 Jedním z omezení s [begin_message_map –](reference/message-map-macros-mfc.md#begin_message_map) makro nastane, když se používá ve spojení s třídou obsahující argumenty šablony. Při použití s třídu šablony, tato makro způsobí chybu kompilace z důvodu chybějící parametry šablony během rozšiřování makro. [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) makro byla navržena k umožnění mapuje třídy obsahující jednu šablonu argument deklarovat vlastní zprávu.  
  
## <a name="example"></a>Příklad  
 Zvažte například kde knihovny MFC [clistbox –](../mfc/reference/clistbox-class.md) třída rozšířena zajistit synchronizaci s externího zdroje dat. Fiktivní **CSyncListBox** třída je deklarovaná následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 **CSyncListBox** třída je na jednoho typu, který popisuje zdroji dat, které se budou synchronizovat s použitím šablon. Také deklaruje tři metody, které budou součástí mapy zpráv třídy: **OnPaint**, **OnDestroy**, a **OnSynchronize**. **OnSynchronize** metoda je implementována následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 Výše uvedené implementace umožňuje **CSyncListBox** třídy se specializuje na všechny typu třídy, který implementuje **GetCount –** metoda, například **carray –**, **CList**, a **CMap**. **StringizeElement** funkce je deklaraci pomocí následující šablony funkce:  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 Mapy zpráv pro tuto třídu za normálních okolností by být definován jako:  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 kde **LBN_SYNCHRONIZE** je zpráva vlastní uživatelské definované aplikací, jako například:  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 Výše uvedené mapy makro nebude kompilovat, vzhledem k tomu, že specifikace šablony pro **CSyncListBox** třída bude chybět během rozšiřování makro. **BEGIN_TEMPLATE_MESSAGE_MAP** makro tento problém řeší začleněním parametr zadané šablony do rozšířené makro mapy. Mapy zpráv pro tuto třídu se změní na:  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 Následující ukazuje použití ukázkové **CSyncListBox** pomocí **CStringList** objektu:  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 K dokončení testu **StringizeElement** funkce musí být specializuje pro práci s **CStringList** třídy:  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

