---
title: Použití objektů CObject
ms.date: 11/04/2016
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: b5399f02819407a529fd5ec66d4f5acbb16ca002
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441924"
---
# <a name="using-cobject"></a>Použití objektů CObject

[CObject](../mfc/reference/cobject-class.md) je kořenová základní třída pro většinu knihovna Microsoft Foundation Class (MFC). Třída `CObject` obsahuje mnoho užitečných funkcí, které můžete chtít začlenit do vlastních objektů programu, včetně podpory serializace, běhových informací o třídě a výstupu diagnostiky objektů. Pokud třídu odvodíte z `CObject`, vaše třída může tyto `CObject` funkce zneužít.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Odvození třídy z CObject](../mfc/deriving-a-class-from-cobject.md)

- [Přidání podpory pro informace o třídách za běhu, dynamické vytváření a serializaci do naší odvozené třídy](../mfc/specifying-levels-of-functionality.md)

- [Přístup k běhovým informacím o třídě](../mfc/accessing-run-time-class-information.md)

- [Dynamicky vytvářet objekty](../mfc/dynamic-object-creation.md)

- [Vypsat data objektu pro diagnostické účely](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))

- Ověřte vnitřní stav objektu (viz [MFC ASSERT_VALID a CObject:: AssertValid](reference/diagnostic-services.md#assert_valid))

- [Vlastní serializace třídy do trvalého úložiště](../mfc/serialization-in-mfc.md)

- Zobrazit seznam [nejčastějších dotazů k CObject](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass – struktura](../mfc/reference/cruntimeclass-structure.md)<br/>
[Soubory](../mfc/files-in-mfc.md)<br/>
[Serializace](../mfc/serialization-in-mfc.md)
