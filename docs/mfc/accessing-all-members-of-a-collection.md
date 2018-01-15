---
title: "Přístup ke všem členům kolekce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 34ba2795c12695702b2e38034081e17d69c156d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-all-members-of-a-collection"></a>Přístup ke všem členům kolekce
Třídy MFC pole kolekce – i na základě šablon a není – používat pro přístup k jejich elementů indexy. Třídy MFC seznamu a mapy kolekce – i na základě šablon a není – použít jako ukazatel typu **pozice** k popisu dané pozici v rámci kolekce. Pro přístup k jedné nebo více členové těchto kolekcí, budete nejprve inicializovat označení pozice opakovaně předat tuto pozici do kolekce a požádejte ho vrátit na další prvek. Kolekce není zodpovědná za údržbu informace o průběhu iterace stavu. Tyto informace se ukládají v označení pozice. Ale s ohledem na konkrétní pozici, kolekce je odpovědná za vrácení na další prvek.  
  
 Následující postupy ukazují, jak k iteraci nad tři hlavní typy kolekcí dodávané s knihovnou MFC:  
  
-   [Iterace pole](#_core_to_iterate_an_array)  
  
-   [Iterace v seznamu](#_core_to_iterate_a_list)  
  
-   [Iterace mapy](#_core_to_iterate_a_map)  
  
### <a name="_core_to_iterate_an_array"></a>K iteraci v pole  
  
1.  Použít pořadová čísla indexu s `GetAt` – členská funkce:  
  
     [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]  
  
     Tento příklad používá pole typu ukazatele, které obsahuje odkazy na `CPerson` objekty. Toto pole je odvozená od třídy `CObArray`, jeden objektu bez šablony předdefinované třídy. `GetAt`vrátí ukazatel na `CPerson` objektu. Pro typové ukazatel kolekce třídy – pole nebo seznamy – první parametr určuje základní třídy; druhý parametr určuje typ úložiště.  
  
     `CTypedPtrArray` Třídy také přetížení **[]** operátor tak, aby můžete použít obvyklé syntaxe pole-dolní index přístup prvky pole. Alternativu k příkazu v textu `for` smyčka výše je  
  
     [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]  
  
     Tento operátor existuje v obou **const** a jiných-**const** verze. **Const** verze, která se vyvolá pro **const** pole, může se objevit pouze na pravé straně příkazu přiřazení.  
  
### <a name="_core_to_iterate_a_list"></a>K iteraci v seznamu  
  
1.  Použít členské funkce `GetHeadPosition` a `GetNext` k procházení seznamu:  
  
     [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]  
  
     Tento příklad používá seznam typu ukazatele tak, aby obsahovala odkazy na `CPerson` objekty. Seznam deklaraci podobá pro pole v postupu [k iteraci v pole](#_core_to_iterate_an_array) , ale je odvozená od třídy `CObList`. `GetNext`vrátí ukazatel na `CPerson` objektu.  
  
### <a name="_core_to_iterate_a_map"></a>K iteraci v mapy  
  
1.  Použití `GetStartPosition` získat na začátek mapy a `GetNextAssoc` opakovaně získat další klíč a hodnotu z mapování, jak je znázorněno v následujícím příkladu:  
  
     [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]  
  
     Tento příklad používá šablonu jednoduché mapy (nikoli ukazatel typu kolekce), který používá `CString` klíče a ukládá ukazatele na `CPerson` objekty. Při použití funkce přístupu, jako `GetNextAssoc`, třída poskytuje odkazy na `CPerson` objekty. Pokud použijete jednu z kolekce mapu objektu bez šablony místo, musíte vysílat vrácený `CObject` ukazatel na ukazatel na `CPerson`.  
  
    > [!NOTE]
    >  Pro mapování objektu bez šablony kompilátor vyžaduje odkaz na `CObject` ukazatel v poslední parametr `GetNextAssoc`. Na vstupu musíte vysílat ukazatele na typu, jak je znázorněno v následujícím příkladu.  
  
     Šablona řešení je jednodušší a pomáhá zajistit lepší zabezpečení typů. Kód objektu bez šablony je složitější, jak je vidět tady:  
  
     [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]  
  
 Další informace najdete v tématu [odstraňování všech objektů v kolekcích CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md).  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../mfc/collections.md)

