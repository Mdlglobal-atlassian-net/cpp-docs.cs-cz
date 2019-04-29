---
title: Přístup ke všem členům kolekce
ms.date: 11/04/2016
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
ms.openlocfilehash: ae866b71d2a9f001c56b2c61d99749cab824b313
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392983"
---
# <a name="accessing-all-members-of-a-collection"></a>Přístup ke všem členům kolekce

MFC – třídy kolekce pole – obě založené na šablonách a nikoli – použití indexů pro přístup k jejich prvky. MFC – třídy kolekce seznamu a mapy – obě založené na šablonách a nikoli – použít jako ukazatel typu **pozice** k popisu danou pozici v rámci kolekce. Pro přístup k jedné nebo více členové těchto kolekcí, je nejprve inicializovat Indikátor pozice v opakovaně předat této pozici do kolekce a požádejte ho vrátit další prvek. Kolekce není odpovědná za správu stavu informace o průběhu iterace. Tyto informace se ukládají v Indikátor pozice. Ale s ohledem na konkrétní pozici, kolekce je zodpovědná za navrácení další prvek.

Následující postupy ukazují, jak k iteraci přes tři hlavní typy kolekcí, které poskytuje s knihovnou MFC:

- [Iterace pole](#_core_to_iterate_an_array)

- [Iterace v seznamu](#_core_to_iterate_a_list)

- [Iterace mapy](#_core_to_iterate_a_map)

### <a name="_core_to_iterate_an_array"></a> Pro iteraci polem

1. Sekvenční index čísla s `GetAt` členské funkce:

   [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]

   V tomto příkladu, který obsahuje odkazy na pole s typem ukazatele `CPerson` objekty. Pole je odvozen od třídy `CObArray`, jeden nešablonových předdefinované třídy. `GetAt` vrací ukazatel `CPerson` objektu. Pro třídy kolekce typu ukazatele – pole nebo seznamy – první parametr určuje základní třídy; druhý parametr určuje typ, který chcete uložit.

   `CTypedPtrArray` Třídy také přetížení **[] č.** operátor tak, aby může používat běžné syntaxe dolní index pole pro přístup k prvků pole. O alternativu k příkazu v těle **pro** je výše uvedený cyklus

   [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]

   Tento operátor existuje v obou **const** a jiných-**const** verze. **Const** verzi, která je vyvolána **const** pole, se může objevit pouze na pravé straně příkazu přiřazení.

### <a name="_core_to_iterate_a_list"></a> K iteraci v seznamu

1. Pomocí členské funkce `GetHeadPosition` a `GetNext` pro procházení seznamu nahlíželi:

   [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]

   Tento příklad používá tak, aby obsahovala ukazatele na seznam typované ukazatele `CPerson` objekty. Seznam deklarací se podobá pro pole v postupu [pro iteraci polem](#_core_to_iterate_an_array) je odvozena z třídy, ale `CObList`. `GetNext` vrací ukazatel `CPerson` objektu.

### <a name="_core_to_iterate_a_map"></a> K iteraci v mapě

1. Použití `GetStartPosition` zobrazíte na začátek mapy a `GetNextAssoc` opakovaně získat další klíč a hodnotu z mapy, jak je znázorněno v následujícím příkladu:

   [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]

   Tento příklad používá šablonu jednoduché mapy (místo kolekce typu ukazatel), který používá `CString` klíče a ukládá ukazatele do `CPerson` objekty. Při použití funkcí přístup, jako jsou `GetNextAssoc`, třída poskytuje odkazy na `CPerson` objekty. Pokud používáte jednu z kolekcí mapy nešablonových místo, musíte přetypovat vráceného `CObject` ukazatel na ukazatel `CPerson`.

    > [!NOTE]
    >  Kompilátor pro mapování objektu bez šablony vyžaduje odkaz na `CObject` ukazatel v posledním parametru do `GetNextAssoc`. Na vstupu musí přetypování ukazatele na typ, jak je znázorněno v následujícím příkladu.

   Šablona řešení je jednodušší a zajišťuje vyšší bezpečnost typů. Kód objektu bez šablony je složitější, jak je vidět tady:

   [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]

Další informace najdete v tématu [odstraňování všech objektů v kolekcích CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md).

## <a name="see-also"></a>Viz také:

[Kolekce](../mfc/collections.md)
