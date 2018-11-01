---
title: Vytváření dynamických objektů
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 75d4a055f047abfcac4451c04bcd1cc75650c89a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563720"
---
# <a name="dynamic-object-creation"></a>Vytváření dynamických objektů

Tento článek vysvětluje, jak vytvořit objekt dynamicky za běhu. Postup používá run-time třída informace, jak je popsáno v článku [přístup k informacím o třídě Run-Time](../mfc/accessing-run-time-class-information.md).

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Dynamicky se vytvářejí objekt dle jeho run-time třída

1. Pomocí následujícího kódu dynamicky vytvořit objekt s použitím `CreateObject` funkce `CRuntimeClass`. Všimněte si, že při selhání, `CreateObject` vrátí **NULL** namísto vyvolání výjimky:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Viz také

[Použití objektů CObject](../mfc/using-cobject.md)

