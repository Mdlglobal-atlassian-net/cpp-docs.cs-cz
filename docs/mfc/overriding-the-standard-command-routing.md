---
title: Přepsání standardního směrování příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 132831939c05f7e8f84c306f5d08bba9cd5e8ea4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648436"
---
# <a name="overriding-the-standard-command-routing"></a>Přepsání standardního směrování příkazů

Ve výjimečných případech při musí implementovat několik variant standardní framework směrování, lze jej přepsat. Chcete-li změnit směrování v jedné nebo více tříd tak, že přepíšete spočívá `OnCmdMsg` v těchto tříd. Udělat:

- Ve třídě by to poškodilo pořadí předat objekt jiný než výchozí.

- Nový objekt nevýchozí nebo cíle příkazů se pak předává příkazů.

Je-li vložit některé nového objektu do směrování, jeho třída musí být příkaz cílovou třídu. V přepsání verze `OnCmdMsg`, nezapomeňte volat verzi, která jste přepsání. Najdete v článku [oncmdmsg –](../mfc/reference/ccmdtarget-class.md#oncmdmsg) členské funkce třídy `CCmdTarget` v *odkaz knihovny MFC* a verzí v těchto tříd jako `CView` a `CDocument` v zadaný zdrojový kód pro příklady.

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

