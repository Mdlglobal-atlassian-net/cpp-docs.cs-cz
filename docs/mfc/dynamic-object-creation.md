---
title: Vytváření dynamických objektů
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364798"
---
# <a name="dynamic-object-creation"></a>Vytváření dynamických objektů

Tento článek vysvětluje, jak vytvořit objekt dynamicky za běhu. Postup používá informace o třídě za běhu, jak je popsáno v článku [Přístup k informacím o třídě run-time](../mfc/accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Dynamicky vytvořit objekt s ohledem na jeho třídu run-time

1. Pomocí následujícího kódu můžete dynamicky `CreateObject` vytvořit objekt `CRuntimeClass`pomocí funkce . Při selhání `CreateObject` vrátí **null** namísto vyvolání výjimky:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Viz také

[Zničení objektů](tn017-destroying-window-objects.md)
okna[pomocí objektu CObject](using-cobject.md)
