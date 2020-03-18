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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446362"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Ukládání a načítání objektů CObject prostřednictvím archivu

Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další pozornost. V některých případech byste měli zavolat funkci `Serialize` objektu, kde je objekt `CArchive` parametr `Serialize` volání, a to na rozdíl od **<\<** nebo **>>ho** operátoru `CArchive`. Důležitým faktem, který je třeba pamatovat, je, že operátor `CArchive` **>>** sestaví `CObject` v paměti na základě `CRuntimeClass` informací, které byly dříve zapsány do souboru uložením archivu.

Proto bez ohledu na to, zda používáte `CArchive` **<\<** a **>>** operátory, a volání `Serialize`, závisí na tom, zda *potřebujete* archiv načítání k dynamickému rekonstrukci objektu na základě dříve uložených `CRuntimeClass` informací. Použijte funkci `Serialize` v následujících případech:

- Při deserializaci objektu je třeba předem znát přesnou třídu objektu.

- Při deserializaci objektu již máte přidělenou paměť.

> [!CAUTION]
>  Pokud načtete objekt pomocí funkce `Serialize`, je také nutné uložit objekt pomocí funkce `Serialize`. Neukládat pomocí operátoru `CArchive` **<<** a pak ho načíst pomocí funkce `Serialize` nebo uložit pomocí `Serialize` funkce a pak načíst pomocí operátoru `CArchive >>`.

Následující příklad znázorňuje případy:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

V souhrnu, pokud vaše serializovatelný třída definuje vložený `CObject` jako člen *, neměli byste používat `CArchive`* **<\<** a **>>** operátory pro daný objekt, ale měli byste místo toho volat funkci `Serialize`. Také Pokud vaše serializovatelný třída definuje ukazatel na `CObject` (nebo objekt odvozený z `CObject`) jako člen, ale sestaví tento druhý objekt ve svém vlastním konstruktoru, měli byste také volat `Serialize`.

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
