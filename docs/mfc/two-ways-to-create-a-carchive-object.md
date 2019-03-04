---
title: Dva způsoby vytvoření objektu CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
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
ms.openlocfilehash: 80e3e73840bce53691c3f5fdafb62c60bdb8f832
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273800"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dva způsoby vytvoření objektu CArchive

Existují dva způsoby, jak vytvořit `CArchive` objektu:

- [Implicitní vytvoření objektu CArchive prostřednictvím rozhraní framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Explicitní vytvoření objektu CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Implicitní vytvoření objektu CArchive prostřednictvím rozhraní Framework

Nejvíce nejčastější a nejjednodušší, způsob, jak je chcete, aby rozhraní vytvořit `CArchive` objekt dokumentu jménem uložit, uložit jako a spuštění příkazů v nabídce Soubor.

Zde je, co systém provádí, když uživatel aplikace vydá příkazu Uložit jako, v nabídce Soubor:

1. Uvede počet **uložit jako** dialogové okno a získá název souboru od uživatele.

1. Otevře se soubor s názvem podle uživatele jako datový typ `CFile` objektu.

1. Vytvoří `CArchive` objekt, který ukazuje na to `CFile` objektu. Při vytváření `CArchive` objektu rozhraní nastaví režim na "úložiště" (zápis, serializaci), na rozdíl od "načítání" (čtení a deserializovat).

1. Volání `Serialize` funkci definovanou v vaše `CDocument`-odvozené třídy předáním odkazu na `CArchive` objektu.

Váš dokument `Serialize` pak zapíše data do funkce `CArchive` objektu, jak je vysvětleno za chvíli. Po návratu z vaší `Serialize` zničí rozhraní framework funkce, `CArchive` objekt a potom `CFile` objektu.

Proto pokud necháte rozhraní vytvořit `CArchive` objekt dokumentu, vše, co musíte provést je implementovat dokumentu `Serialize` funkce, která zapisuje a načte do a z archivu. Budete také muset implementovat `Serialize` pro všechny `CObject`-odvozené objekty, které dokumentu `Serialize` funkce zase serializuje přímo nebo nepřímo.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Explicitní vytvoření objektu CArchive

Kromě serializaci do dokumentu prostřednictvím rozhraní framework, jsou jiné situace, kdy je nutné `CArchive` objektu. Například můžete chtít serializaci dat do a ze schránky, reprezentovaný `CSharedFile` objektu. Nebo můžete chtít použít uživatelské rozhraní pro uložení souboru, který je odlišné od těch, které nabízí rozhraní. V takovém případě můžete explicitně vytvořit `CArchive` objektu. To provedete stejným způsobem, který nemá rozhraní, pomocí následujícího postupu.

#### <a name="to-explicitly-create-a-carchive-object"></a>Explicitní vytvoření objektu CArchive

1. Vytvoření `CFile` nebo objektu odvozené z `CFile`.

1. Předání `CFile` objekt konstruktoru pro `CArchive`, jak je znázorněno v následujícím příkladu:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Druhý argument `CArchive` konstruktor je Výčtová hodnota, která určuje, zda archivu se použije pro ukládání nebo načítání dat do nebo ze souboru. `Serialize` Funkce objektu voláním zkontroluje tento stav `IsStoring` funkce pro objekt archivu.

Po dokončení, ukládání nebo načítání dat do nebo z `CArchive` objektu, zavřete ho. I když `CArchive` (a `CFile`) objekty se automaticky zavře archivu (a soubor), je vhodné to provést explicitně, protože je jednodušší zotavení z chyb. Další informace o zpracování chyb, naleznete v článku [výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Zavřete objekt CArchive

1. Následující příklad ukazuje, jak lze uzavřít `CArchive` objektu:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Viz také:

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
