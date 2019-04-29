---
title: Použití objektů CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: 6c4355f43df33f37838cfc9be4453e42271ae9f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411759"
---
# <a name="using-cobject"></a>Použití objektů CObject

[CObject –](../mfc/reference/cobject-class.md) je kořenová základní třída pro většinu z třídy knihovny MFC (Microsoft Foundation). `CObject` Třída obsahuje mnoho užitečných funkcí, které možná budete chtít začlenit do vlastní objekty programu, včetně podpory serializace, run-time třída informace a výstup diagnostiky objektu. Pokud odvodíte třídu od `CObject`, vaše třída může zneužít tyto `CObject` funkce.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Odvodit třídu z objektu CObject](../mfc/deriving-a-class-from-cobject.md)

- [Přidání podpory pro informace o třídě za běhu, dynamické vytváření a serializace Moje odvozené třídy](../mfc/specifying-levels-of-functionality.md)

- [Přístup k informacím run-time třída](../mfc/accessing-run-time-class-information.md)

- [Dynamicky vytvořit objekty](../mfc/dynamic-object-creation.md)

- [Výpis objektu dat k diagnostickým účelům](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))

- Ověření objektu vnitřní stav (viz [MFC ASSERT_VALID a CObject::AssertValid](reference/diagnostic-services.md#assert_valid))

- [Třída serializovat sama sebe do trvalého úložiště](../mfc/serialization-in-mfc.md)

- Podívejte se do seznamu [CObject – nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>Viz také:

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass – struktura](../mfc/reference/cruntimeclass-structure.md)<br/>
[Soubory](../mfc/files-in-mfc.md)<br/>
[Serializace](../mfc/serialization-in-mfc.md)
