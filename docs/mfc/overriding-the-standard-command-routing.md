---
title: Přepsání standardního směrování příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410158"
---
# <a name="overriding-the-standard-command-routing"></a>Přepsání standardního směrování příkazů

Ve výjimečných případech při musí implementovat několik variant standardní framework směrování, lze jej přepsat. Chcete-li změnit směrování v jedné nebo více tříd tak, že přepíšete spočívá `OnCmdMsg` v těchto tříd. Udělat:

- Ve třídě by to poškodilo pořadí předat objekt jiný než výchozí.

- Nový objekt nevýchozí nebo cíle příkazů se pak předává příkazů.

Je-li vložit některé nového objektu do směrování, jeho třída musí být příkaz cílovou třídu. V přepsání verze `OnCmdMsg`, nezapomeňte volat verzi, která jste přepsání. Najdete v článku [oncmdmsg –](../mfc/reference/ccmdtarget-class.md#oncmdmsg) členské funkce třídy `CCmdTarget` v *odkaz knihovny MFC* a verzí v těchto tříd jako `CView` a `CDocument` v zadaný zdrojový kód pro příklady.

## <a name="see-also"></a>Viz také:

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)
