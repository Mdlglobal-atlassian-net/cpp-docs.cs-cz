---
title: Odvození třídy z objektu CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
ms.openlocfilehash: 26fdab5165ca098c5d7813ebf44983c261094449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152056"
---
# <a name="deriving-a-class-from-cobject"></a>Odvození třídy z objektu CObject

Tento článek popisuje minimální kroky potřebné k odvození třídy z [CObject](../mfc/reference/cobject-class.md). Další `CObject` třídy články popisují kroky potřebné k využít výhod konkrétní `CObject` funkce, jako je serializaci a diagnostických podporu ladění.

V diskuzích o `CObject`, často používají soubor podmínky"rozhraní" a "implementační soubor". Soubor rozhraní (často označované jako soubor hlaviček nebo. Soubor H) obsahuje deklaraci třídy a všechny ostatní informace potřebné k použití třídy. Implementace souboru (nebo). Soubor CPP) obsahuje definice třídy, jakož i kód, který implementuje členské funkce třídy. Například pro třídu s názvem `CPerson`, byste obvykle vytvořili soubor rozhraní s názvem osoby. H a implementační soubor s názvem osoby. CPP. Pro některé malé třídy, které se sdílejí mezi aplikacemi, je však někdy usnadňuje kombinovat rozhraní a implementaci do jednoho. Soubor CPP.

Můžete zvolit ze čtyř úrovní funkčnosti při odvození třídy z `CObject`:

- Základní funkce: Žádná podpora pro informace o třídě za běhu nebo serializace ale zahrnuje správu diagnostiky paměti.

- Základní funkce plus podporu pro informace o třídě za běhu.

- Základní funkce plus podporu pro informace o třídě za běhu a dynamické vytváření.

- Základní funkce plus podporu pro informace o třídě za běhu, dynamické vytváření a serializace.

Třídy pro opakované použití (ty, které bude později sloužit jako základní třídy) by měl obsahovat alespoň run-time třída podporu a podporu serializace, pokud všechny potřeby budoucí serializace je očekávané výsledky.

Vyberte úroveň funkčnosti pomocí konkrétní deklaraci a implementaci makra v deklaraci a implementaci tříd, které jsou odvozeny z `CObject`.

Následující tabulka ukazuje vztah mezi makra použitá pro podporu serializace a informace doby běhu.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra použitá k serializaci a informace doby běhu

|Použít – makro|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Základní `CObject` funkce|Ne|Ne|Ne|
|`DECLARE_DYNAMIC`|Ano|Ne|Ne|
|`DECLARE_DYNCREATE`|Ano|Ano|Ne|
|`DECLARE_SERIAL`|Ano|Ano|Ano|

#### <a name="to-use-basic-cobject-functionality"></a>Jak používat funkce základní třídy CObject

1. Použijte normální syntaxí jazyka C++ se odvodit třídu z `CObject` (nebo z třídy odvozené od `CObject`).

   Následující příklad ukazuje nejjednodušší případ odvození třídy z `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Za normálních okolností však můžete chtít potlačit některé `CObject`pro členské funkce pro zpracování podrobností o nové třídy. Například může obvykle chcete přepsat `Dump` funkce `CObject` zajištění výstupu ladění pro obsah vaší třídy. Podrobnosti ohledně postupu přepsání `Dump`, najdete v článku [úpravy výpisu paměti objektu](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100)). Můžete také přepsat `AssertValid` funkce `CObject` poskytnout vlastní testování k ověření konzistence datové členy třídy objektů. Popis toho, jak přepsat `AssertValid`, naleznete v tématu [MFC ASSERT_VALID a CObject::AssertValid](reference/diagnostic-services.md#assert_valid).

Tento článek [určení úrovní funkčnosti](../mfc/specifying-levels-of-functionality.md) popisuje, jak určit jiných úrovních funkčnosti, včetně informací o třídě za běhu, vytváření dynamických objektů a serializace.

## <a name="see-also"></a>Viz také:

[Použití objektů CObject](../mfc/using-cobject.md)
