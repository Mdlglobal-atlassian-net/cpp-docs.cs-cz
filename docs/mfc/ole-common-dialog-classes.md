---
title: Společné třídy dialogových oken OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: b44a7b203c17f09f872cfedbb05798affb57f0f9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447671"
---
# <a name="ole-common-dialog-classes"></a>Společné třídy dialogových oken OLE

Tyto třídy zpracovávají běžné úlohy OLE implementací řady standardních dialogových oken OLE. Poskytují také konzistentní uživatelské rozhraní pro funkce OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Používá se rozhraním pro zahrnutí běžných implementací pro všechna dialogová okna OLE. Všechny třídy dialogového okna v kategorii uživatelského rozhraní jsou odvozeny z této základní třídy. `COleDialog` nelze použít přímo.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Zobrazí dialogové okno Vložit objekt, standardní uživatelské rozhraní pro vkládání nových propojených nebo vložených položek OLE.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Zobrazí dialogové okno Vložit speciální, které obsahuje standardní uživatelské rozhraní pro implementaci příkazu Upravit speciální vložení.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Zobrazí dialogové okno Upravit odkazy, které obsahuje standardní uživatelské rozhraní pro úpravu informací o propojených položkách.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Zobrazí dialogové okno Změnit ikonu, standardní uživatelské rozhraní pro změnu ikony přidružené k vložené nebo propojené položce OLE.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod položek OLE z jednoho typu na jiný.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Zapouzdřuje dialogové okno Windows Common OLE Properties. Dialogová okna společných vlastností OLE poskytují snadný způsob, jak zobrazit a upravit vlastnosti položky dokumentu OLE způsobem konzistentním s normami systému Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní pro aktualizaci všech odkazů v dokumentu. Dialogové okno obsahuje indikátor průběhu, který určuje, jak se má postup aktualizace dokončit.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cíle nebo zdroje odkazu.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Zobrazí dialogová okna zaneprázdněný serverem a server neodpovídá, standardní uživatelské rozhraní pro zpracování volání zaneprázdněných aplikací. Obvykle se automaticky zobrazí pomocí implementace `COleMessageFilter`.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
