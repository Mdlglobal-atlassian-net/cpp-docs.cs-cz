---
title: Ukládání a načítání objektů CObject prostřednictvím archivu
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372150"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Ukládání a načítání objektů CObject prostřednictvím archivu

Ukládání a načítání `CObject`s přes archiv vyžaduje zvláštní pozornost. V některých případech byste `Serialize` měli volat funkci `CArchive` objektu, kde `Serialize` je objekt parametrem volání, **>>** na `CArchive`rozdíl od použití operátoru ** < ** nebo . Důležité skutečnosti je mít na `CArchive` **>>** paměti, že `CObject` operátor konstruuje v paměti na `CRuntimeClass` základě informací dříve zapsané do souboru ukládání archivu.

Proto, `CArchive` ** < ** zda používáte **>>** operátory `Serialize`a versus volání , závisí na tom, zda *potřebujete* načítací archiv dynamicky rekonstruovat objekt na základě dříve uložených `CRuntimeClass` informací. Použijte `Serialize` funkci v následujících případech:

- Při deserializaci objektu znáte přesnou třídu objektu předem.

- Při deserializaci objektu již máte přidělenou paměť.

> [!CAUTION]
> Pokud načtete objekt `Serialize` pomocí funkce, musíte také `Serialize` uložit objekt pomocí funkce. Neukládejte pomocí `CArchive` **<<** operátoru a `Serialize` pak načíst pomocí `Serialize` funkce nebo `CArchive >>` uložit pomocí funkce a pak načíst pomocí operátoru.

Následující příklad ilustruje případy:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Stručně řečeno, pokud vaše serializovatelná třída `CObject` definuje vložený jako člen, `CArchive` ** < ** *neměli* byste pro tento `Serialize` objekt používat operátory a, **>>** ale místo toho byste měli volat funkci. Také pokud serializovatelné třídy definuje ukazatel `CObject` na (nebo objekt `CObject`odvozený z) jako člen, ale vytvoří tento jiný objekt `Serialize`ve svém vlastním konstruktoru, měli byste také volat .

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
