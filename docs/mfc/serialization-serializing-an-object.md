---
title: 'Serializace: Serializace objektu'
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 5c1106f180c587894283575a82a88e9e18b5c01a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308040"
---
# <a name="serialization-serializing-an-object"></a>Serializace: Serializace objektu

Tento článek [serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md) ukazuje, jak vytvořit třídu serializovatelný. Jakmile budete mít serializovatelné třídy, může serializovat objekty do a ze souboru pomocí třídy [CArchive](../mfc/reference/carchive-class.md) objektu. Tento článek vysvětluje:

- [Co je objekt CArchive](../mfc/what-is-a-carchive-object.md).

- [Dva způsoby, jak vytvořit CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Jak používat CArchive <\< a >> operátory](../mfc/using-the-carchive-output-and-input-operators.md).

- [Ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Můžete umožnit, aby rozhraní vytvořit archiv serializovatelný dokumentu nebo explicitně `CArchive` objektu sami. Můžete přenášet data mezi souborem a serializovatelný objekt pomocí <\< a >> operátory pro `CArchive` nebo v některých případech se pomocí volání `Serialize` funkce `CObject`-odvozené třídy.

## <a name="see-also"></a>Viz také:

[Serializace](../mfc/serialization-in-mfc.md)
