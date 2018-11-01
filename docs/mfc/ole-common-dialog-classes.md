---
title: Společné třídy dialogových oken OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: e11e072ad3133d5df9614afa8753178e11b2d025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614068"
---
# <a name="ole-common-dialog-classes"></a>Společné třídy dialogových oken OLE

Tyto třídy zpracování běžných úkolů OLE implementací počet standardní dialogová okna OLE. Obsahují taky konzistentní uživatelské rozhraní pro funkci OLE.

[Coledialog –](../mfc/reference/coledialog-class.md)<br/>
Používá rozhraní tak, aby obsahovala běžné implementace pro všechna dialogová okna OLE. Všechny třídy dialogových oken v kategorii uživatelského rozhraní jsou odvozeny z této základní třídy. `COleDialog` nelze použít přímo.

[Coleinsertdialog –](../mfc/reference/coleinsertdialog-class.md)<br/>
Zobrazí dialogové okno Vložit objekt, tak se standardní uživatelské rozhraní pro vložení OLE nové propojené nebo vložené položky.

[Colepastespecialdialog –](../mfc/reference/colepastespecialdialog-class.md)<br/>
Zobrazí zvláštní vložení dialogové okno, standardní uživatelské rozhraní pro implementaci příkazu Upravit Vložit jinak.

[Colelinksdialog –](../mfc/reference/colelinksdialog-class.md)<br/>
Zobrazí dialogové okno Upravit odkazy, standardní uživatelské rozhraní pro úpravu informace o propojené položky.

[Colechangeicondialog –](../mfc/reference/colechangeicondialog-class.md)<br/>
Zobrazí dialogové okno změny ikony, standardní uživatelské rozhraní, že změníte ikony přidružené k OLE vložené nebo propojené položky.

[Coleconvertdialog –](../mfc/reference/coleconvertdialog-class.md)<br/>
Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod OLE – položky z jednoho typu na jiný.

[Colepropertiesdialog –](../mfc/reference/colepropertiesdialog-class.md)<br/>
Zapouzdřuje dialogové okno vlastnosti OLE Windows běžné. Společná dialogová okna OLE vlastnosti poskytují snadný způsob, jak zobrazit a upravit vlastnosti dokumentu položky OLE v souladu se standardy Windows.

[Coleupdatedialog –](../mfc/reference/coleupdatedialog-class.md)<br/>
Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní pro aktualizaci všech odkazů v dokumentu. Dialogové okno obsahuje indikátor průběhu označuje, jak blízko bude dokončen.

[Colechangesourcedialog –](../mfc/reference/colechangesourcedialog-class.md)<br/>
Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cílová nebo zdrojová odkazu.

[Colebusydialog –](../mfc/reference/colebusydialog-class.md)<br/>
Zobrazí Serverbusy dialogových oknech a Server neodpovídá, standardní uživatelské rozhraní pro zpracování volání zaneprázdněný aplikací. Obvykle automaticky zobrazí `COleMessageFilter` implementace.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

