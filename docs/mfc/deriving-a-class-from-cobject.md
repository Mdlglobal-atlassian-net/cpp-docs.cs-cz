---
title: Odvození třídy z objektu CObject
ms.date: 11/04/2016
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
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446976"
---
# <a name="deriving-a-class-from-cobject"></a>Odvození třídy z objektu CObject

Tento článek popisuje minimální kroky nezbytné k odvození třídy z [CObject](../mfc/reference/cobject-class.md). Další články `CObject` třídy popisují kroky potřebné k tomu, abyste mohli využít konkrétní `CObject` funkce, jako je například serializace a podpora ladění diagnostiky.

V diskuzích `CObject`se často používají výrazy "soubor rozhraní" a "implementační soubor". Soubor rozhraní (často se nazývá hlavičkový soubor nebo. H soubor) obsahuje deklaraci třídy a všechny další informace potřebné k použití třídy. Implementační soubor (nebo. Soubor CPP) obsahuje definici třídy a také kód, který implementuje členské funkce třídy. Například pro třídu s názvem `CPerson`obvykle vytvoříte soubor rozhraní s názvem PERSON. H a implementační soubor s názvem PERSON. CPP. Nicméně pro některé malé třídy, které nebudou sdíleny mezi aplikacemi, je někdy snazší kombinovat rozhraní a implementaci do jediného. Soubor CPP.

Při odvozování třídy z `CObject`můžete zvolit ze čtyř úrovní funkčnosti:

- Základní funkce: žádná podpora pro běhové informace třídy nebo serializace, ale zahrnuje správu diagnostiky paměti.

- Základní funkce Plus Podpora pro běhové informace třídy.

- Základní funkce Plus Podpora pro informace o třídách za běhu a dynamické vytváření.

- Základní funkce Plus Podpora pro běhové informace třídy, dynamické vytváření a serializace.

Třídy navržené pro opakované použití (ty, které budou později sloužit jako základní třídy) by měly přinejmenším zahrnovat podporu tříd runtime a podporu serializace, pokud je předpokládaná budoucí nutnost serializace.

Zvolíte úroveň funkčnosti pomocí konkrétní deklarace a implementační makra v deklaraci a implementaci tříd odvozených z `CObject`.

Následující tabulka ukazuje vztah mezi makry použitými pro podporu serializace a běhových informací.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra používaná pro serializaci a běhové informace

|Použité makro|CObject::IsKindOf|CRuntimeClass::<br /><br /> Metody|CArchive:: operator > ><br /><br /> CArchive:: operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Základní funkce `CObject`|Ne|Ne|Ne|
|`DECLARE_DYNAMIC`|Ano|Ne|Ne|
|`DECLARE_DYNCREATE`|Ano|Ano|Ne|
|`DECLARE_SERIAL`|Ano|Ano|Ano|

#### <a name="to-use-basic-cobject-functionality"></a>Použití základní funkce CObject

1. K odvození C++ vaší třídy z `CObject` (nebo z třídy odvozené od `CObject`) použijte syntaxi Normal.

   Následující příklad ukazuje nejjednodušší případ, odvození třídy z `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Obvykle však můžete chtít přepsat některé z členských funkcí `CObject`pro zpracování specifických vlastností vaší nové třídy. Například může být obvykle vhodné přepsat funkci `Dump` `CObject` a poskytnout tak výstup ladění pro obsah vaší třídy. Podrobnosti o tom, jak přepsat `Dump`, najdete v článku [přizpůsobení výpisu stavu objektu](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100)). Můžete také přepsat funkci `AssertValid` `CObject` a poskytnout tak přizpůsobené testování, aby bylo možné ověřit konzistenci datových členů objektů třídy. Popis způsobu přepsání `AssertValid`naleznete v tématu [MFC ASSERT_VALID a CObject:: AssertValid](reference/diagnostic-services.md#assert_valid).

Článek [určující úrovně funkčnosti](../mfc/specifying-levels-of-functionality.md) popisuje, jak určit další úrovně funkčnosti, včetně informací o třídách modulu runtime, vytváření dynamických objektů a serializaci.

## <a name="see-also"></a>Viz také

[Použití objektů CObject](../mfc/using-cobject.md)
