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
ms.openlocfilehash: d34c141fc9a2b53eab6a4c0b0ce1799ff5243d84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263543"
---
# <a name="ole-common-dialog-classes"></a>Společné třídy dialogových oken OLE

Tyto třídy zpracování běžných úkolů OLE implementací počet standardní dialogová okna OLE. Obsahují taky konzistentní uživatelské rozhraní pro funkci OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Používá rozhraní tak, aby obsahovala běžné implementace pro všechna dialogová okna OLE. Všechny třídy dialogových oken v kategorii uživatelského rozhraní jsou odvozeny z této základní třídy. `COleDialog` nelze použít přímo.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Zobrazí dialogové okno Vložit objekt, tak se standardní uživatelské rozhraní pro vložení OLE nové propojené nebo vložené položky.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Zobrazí zvláštní vložení dialogové okno, standardní uživatelské rozhraní pro implementaci příkazu Upravit Vložit jinak.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Zobrazí dialogové okno Upravit odkazy, standardní uživatelské rozhraní pro úpravu informace o propojené položky.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Zobrazí dialogové okno změny ikony, standardní uživatelské rozhraní, že změníte ikony přidružené k OLE vložené nebo propojené položky.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod OLE – položky z jednoho typu na jiný.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Zapouzdřuje dialogové okno vlastnosti OLE Windows běžné. Společná dialogová okna OLE vlastnosti poskytují snadný způsob, jak zobrazit a upravit vlastnosti dokumentu položky OLE v souladu se standardy Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní pro aktualizaci všech odkazů v dokumentu. Dialogové okno obsahuje indikátor průběhu označuje, jak blízko bude dokončen.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cílová nebo zdrojová odkazu.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Zobrazí Serverbusy dialogových oknech a Server neodpovídá, standardní uživatelské rozhraní pro zpracování volání zaneprázdněný aplikací. Obvykle automaticky zobrazí `COleMessageFilter` implementace.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
