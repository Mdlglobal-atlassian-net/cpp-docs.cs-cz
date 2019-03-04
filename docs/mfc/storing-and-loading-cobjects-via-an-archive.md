---
title: Ukládání a načítání objektů CObject prostřednictvím archivu
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 591ce7032aa3d70b1e5a020cd9173ed4c9d0fa9b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299939"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Ukládání a načítání objektů CObject prostřednictvím archivu

Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další zkoumání. V některých případech, měli byste zavolat `Serialize` funkce objektu, kde `CArchive` objektu je parametr `Serialize` volání, na rozdíl od použití **< \<** nebo **>>** operátoru `CArchive`. Je důležité skutečnosti potřeba mít na paměti, že `CArchive` **>>** operátor konstrukce `CObject` v paměti na základě `CRuntimeClass` informace předtím zapsala do souboru pomocí ukládání archivu.

Proto, ať už používáte `CArchive` **< \<** a **>>** operátory porovnání volání `Serialize`, závisí na tom, zda jste *potřebovat* načítání archiv k dynamicky rekonstrukci objektu na základě dříve uložené `CRuntimeClass` informace. Použití `Serialize` funkce v následujících případech:

- Při deserializaci objektu, víte přesně třídu objektu předem.

- Při deserializaci objektu, máte již pro něj přidělené paměti.

> [!CAUTION]
>  Pokud načtete pomocí objektu `Serialize` funkce, musíte také uložit objekt pomocí `Serialize` funkce. Neukládejte pomocí `CArchive` **<<** operátor a potom zatížení pomocí `Serialize` funkce nebo ukládat pomocí `Serialize` funkci a pak načíst pomocí `CArchive >>` operátor.

Následující příklad ukazuje případy:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Stručně řečeno, pokud serializovatelné třídy definuje vložený `CObject` jako člena, měli byste *není* použít `CArchive` **< \<** a **>>** operátory pro daný objekt by měly volat, ale `Serialize` namísto toho funkci. Navíc pokud serializovatelné třídy definuje ukazatel na `CObject` (nebo objekt odvozený od `CObject`) jako člen, ale konstrukce tento jiný objekt ve své vlastní konstruktor, měli byste také zavolat `Serialize`.

## <a name="see-also"></a>Viz také:

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
