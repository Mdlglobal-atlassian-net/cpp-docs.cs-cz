---
title: Odvození dokumentové třídy z objektu CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 5998d5707eb741be0e8ac270f6ac5ce77a9ff8d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272058"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Odvození dokumentové třídy z objektu CDocument

Dokumenty obsahují a spravujte data vaší aplikace. Pomocí Průvodce aplikací knihovny MFC zadaný dokument třídy, postupujte takto:

- Odvodit třídu z `CDocument` pro každý typ dokumentu.

- Přidání členské proměnné k ukládání dat každého dokumentu.

- Přepsat `CDocument`společnosti `Serialize` členské funkce ve třídě dokumentů. `Serialize` zapíše a čte data dokumentu z disku a disk.

## <a name="other-document-functions-often-overridden"></a>Často přepisované funkce jiných dokumentů

Můžete také přepsat jiné `CDocument` členské funkce. Zejména je často potřeba přepsat [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) a [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) inicializace dokumentu datové členy a [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) zničit. dynamicky přidělené data. Informace o členech overridable najdete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také:

[Použití dokumentů](../mfc/using-documents.md)
