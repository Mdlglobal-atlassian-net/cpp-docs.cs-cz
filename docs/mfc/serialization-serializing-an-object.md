---
title: 'Serializace: Serializace objektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e05cce1132b180ac8f1350b68d951d776a62315f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381085"
---
# <a name="serialization-serializing-an-object"></a>Serializace: Serializace objektu

Tento článek [serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md) ukazuje, jak vytvořit třídu serializovatelný. Jakmile budete mít serializovatelné třídy, může serializovat objekty do a ze souboru pomocí třídy [CArchive](../mfc/reference/carchive-class.md) objektu. Tento článek vysvětluje:

- [Co je objekt CArchive](../mfc/what-is-a-carchive-object.md).

- [Dva způsoby, jak vytvořit CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Jak používat CArchive <\< a >> operátory](../mfc/using-the-carchive-output-and-input-operators.md).

- [Ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Můžete umožnit, aby rozhraní vytvořit archiv serializovatelný dokumentu nebo explicitně `CArchive` objektu sami. Můžete přenášet data mezi souborem a serializovatelný objekt pomocí <\< a >> operátory pro `CArchive` nebo v některých případech se pomocí volání `Serialize` funkce `CObject`-odvozené třídy.

## <a name="see-also"></a>Viz také

[Serializace](../mfc/serialization-in-mfc.md)

