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
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442038"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dva způsoby vytvoření objektu CArchive

Existují dva způsoby, jak vytvořit objekt `CArchive`:

- [Implicitní vytvoření objektu CArchive prostřednictvím rozhraní .NET Framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Explicitní vytvoření objektu CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Implicitní vytvoření objektu CArchive prostřednictvím rozhraní .NET Framework

Nejběžnějším a nejjednodušším způsobem je umožnit rozhraní vytvořit objekt `CArchive` pro váš dokument jménem v příkazech uložit, Uložit jako a otevřít v nabídce soubor.

Tady je rozhraní, když uživatel vaší aplikace vydá příkaz Uložit jako v nabídce soubor:

1. Zobrazí dialogové okno **Uložit jako** a získá název souboru od uživatele.

1. Otevře soubor s názvem uživatel jako objekt `CFile`.

1. Vytvoří objekt `CArchive`, který odkazuje na tento objekt `CFile`. Při vytváření objektu `CArchive` rozhraní nastaví režim na "Uložit" (zápis, serializace) na rozdíl od "Load" (čtení, deserializace).

1. Volá funkci `Serialize` definovanou ve vaší třídě odvozené `CDocument`a předá jí odkaz na objekt `CArchive`.

Funkce `Serialize` vašeho dokumentu potom zapisuje data do objektu `CArchive`, jak je vysvětleno krátce. Při návratu z funkce `Serialize` rozhraní zničí objekt `CArchive` a pak objekt `CFile`.

Proto pokud necháte rozhraní vytvořit objekt `CArchive` pro váš dokument, stačí, abyste implementovali funkci `Serialize` dokumentu, která zapisuje a čte do archivu a z něj. Také je nutné implementovat `Serialize` pro všechny objekty odvozené `CObject`, které `Serialize` funkce dokumentu v přímém nebo nepřímém serializaci.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Explicitní vytvoření objektu CArchive

Kromě serializace dokumentu přes rozhraní existují další případy, kdy budete potřebovat objekt `CArchive`. Například můžete chtít serializovat data do a ze schránky reprezentované objektem `CSharedFile`. Nebo můžete chtít použít uživatelské rozhraní pro uložení souboru, který je jiný než ten, který je nabízený rozhraním. V takovém případě můžete vytvořit objekt `CArchive` explicitně. To můžete provést stejným způsobem jako rozhraní, a to pomocí následujícího postupu.

#### <a name="to-explicitly-create-a-carchive-object"></a>Explicitní vytvoření objektu CArchive

1. Konstrukce objektu `CFile` nebo objektu odvozeného z `CFile`.

1. Předejte objekt `CFile` do konstruktoru pro `CArchive`, jak je znázorněno v následujícím příkladu:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Druhý argument konstruktoru `CArchive` je Výčtová hodnota, která určuje, zda bude archiv použit k ukládání nebo načítání dat do nebo ze souboru. Funkce `Serialize` objektu tento stav kontroluje voláním funkce `IsStoring` pro objekt archivu.

Až budete hotovi s ukládáním nebo načítáním dat do objektu `CArchive` nebo z něj, zavřete ho. I když objekty `CArchive` (a `CFile`) automaticky zavřou archiv (a soubor), je dobrým zvykem to provést, protože díky tomu je zotavení z chyb snazší. Další informace o zpracování chyb naleznete v článku [výjimky: zachytávání a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Zavření objektu CArchive

1. Následující příklad ukazuje, jak zavřít objekt `CArchive`:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
