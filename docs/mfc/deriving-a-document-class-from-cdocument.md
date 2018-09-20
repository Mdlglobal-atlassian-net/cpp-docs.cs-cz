---
title: Odvození dokumentové třídy z objektu CDocument | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b45dadbc062bbba61cdcb4c883f91943b1b18ba8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429822"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Odvození dokumentové třídy z objektu CDocument

Dokumenty obsahují a spravujte data vaší aplikace. Pomocí Průvodce aplikací knihovny MFC zadaný dokument třídy, postupujte takto:

- Odvodit třídu z `CDocument` pro každý typ dokumentu.

- Přidání členské proměnné k ukládání dat každého dokumentu.

- Přepsat `CDocument`společnosti `Serialize` členské funkce ve třídě dokumentů. `Serialize` zapíše a čte data dokumentu z disku a disk.

## <a name="other-document-functions-often-overridden"></a>Často přepisované funkce jiných dokumentů

Můžete také přepsat jiné `CDocument` členské funkce. Zejména je často potřeba přepsat [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) a [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) inicializace dokumentu datové členy a [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) zničit. dynamicky přidělené data. Informace o členech overridable najdete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

