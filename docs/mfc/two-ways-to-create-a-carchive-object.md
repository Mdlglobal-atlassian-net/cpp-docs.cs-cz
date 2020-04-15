---
title: Dva způsoby vytvoření objektu CArchive
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370949"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dva způsoby vytvoření objektu CArchive

Objekt lze vytvořit dvěma `CArchive` způsoby:

- [Implicitní vytvoření objektu CArchive prostřednictvím rámce](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Explicitní vytvoření objektu CArchive](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Implicitní vytvoření objektu CArchive prostřednictvím rámce

Nejběžnějším a nejjednodušším způsobem je nechat rozhraní `CArchive` vytvořit objekt pro váš dokument jménem příkazů Uložit, Uložit jako a Otevřít v nabídce Soubor.

Zde je to, co framework dělá, když uživatel vaší aplikace vydá příkaz Uložit jako z nabídky Soubor:

1. Zobrazí dialogové okno **Uložit jako** a získá název souboru od uživatele.

1. Otevře soubor pojmenovaný uživatelem `CFile` jako objekt.

1. Vytvoří `CArchive` objekt, který `CFile` odkazuje na tento objekt. Při vytváření `CArchive` objektu framework nastaví režim "ukládat" (psát, serializovat), na rozdíl od "zatížení" (čtení, deserializovat).

1. Volá `Serialize` funkci definovanou `CDocument`ve vaší odvozené třídě a `CArchive` předá ji jako odkaz na objekt.

`Serialize` Funkce dokumentu pak zapíše data `CArchive` do objektu, jak je vysvětleno v nejbližší době. Po návratu `Serialize` z funkce framework zničí `CArchive` objekt a `CFile` potom objekt.

Pokud tedy necháte rozhraní vytvořit `CArchive` objekt pro váš dokument, stačí implementovat `Serialize` funkci dokumentu, která zapisuje a čte do a z archivu. Je také třeba `Serialize` implementovat pro všechny `CObject`odvozené `Serialize` objekty, které funkce dokumentu zase serializes přímo nebo nepřímo.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>Explicitní vytvoření objektu CArchive

Kromě serializace dokumentu prostřednictvím rozhraní, existují i jiné `CArchive` případy, kdy budete potřebovat objekt. Můžete například serializovat data do a ze schránky, reprezentované objektem. `CSharedFile` Nebo můžete chtít použít uživatelské rozhraní pro uložení souboru, který se liší od souboru, který nabízí rozhraní. V takovém případě můžete explicitně vytvořit `CArchive` objekt. Provést stejným způsobem rozhraní framework pomocí následujícího postupu.

#### <a name="to-explicitly-create-a-carchive-object"></a>Explicitní vytvoření objektu CArchive

1. Vytvořte `CFile` objekt nebo objekt `CFile`odvozený z aplikace .

1. Předá `CFile` objekt konstruktoru `CArchive`pro , jak je znázorněno v následujícím příkladu:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Druhý argument konstruktoru `CArchive` je výčtová hodnota, která určuje, zda bude archiv použit pro ukládání nebo načítání dat do nebo ze souboru. Funkce `Serialize` objektu zkontroluje tento stav `IsStoring` voláním funkce objektu archivu.

Po dokončení ukládání nebo načítání dat do nebo `CArchive` z objektu zavřete. Přestože `CArchive` (a `CFile`) objekty automaticky zavře archiv (a soubor), je vhodné explicitně tak učinit, protože usnadňuje zotavení z chyb. Další informace o zpracování chyb naleznete v článku [Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Zavření objektu CArchive

1. Následující příklad ukazuje, jak `CArchive` zavřít objekt:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
