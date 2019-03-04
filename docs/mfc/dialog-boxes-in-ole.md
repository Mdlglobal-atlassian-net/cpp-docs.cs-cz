---
title: Dialogová okna v prostředí OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 1081a831cc2b9fc0ab22e2c80a4f657466534d86
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270888"
---
# <a name="dialog-boxes-in-ole"></a>Dialogová okna v prostředí OLE

Když uživatel spustí aplikaci povoleno OLE, jsou časy, kdy aplikace potřebuje informace od uživatele k provedení operace. Třídy MFC OLE poskytují celou řadou dialogová okna, jak získat požadované informace. Toto téma obsahuje seznam úkolů zpracovat dialogových oknech OLE a třídy potřebné k zobrazování těchto dialogových oken. Podrobnosti o dialogových oken OLE a konstrukce používané k úpravám jejich chování najdete v tématu [odkaz knihovny MFC](../mfc/mfc-desktop-applications.md).

*Insert – objekt*<br/>
Toto dialogové okno umožňuje uživateli vložení nově vytvořen nebo stávajících objektů do složeného dokumentu. Také umožňuje uživateli rozhodnout se, aby se zobrazila položka jako ikona a umožňuje změnit ikonu příkazové tlačítko. Zobrazte toto dialogové okno když uživatel vybere vložit objekt v nabídce Úpravy. Použití [coleinsertdialog –](../mfc/reference/coleinsertdialog-class.md) třídu dialogovému oknu. Všimněte si, že aplikace MDI nelze vložit do sebe sama. Aplikace, která je server/kontejner nelze vložit do sebe sama, pokud je aplikace SDI.

*Vložit speciální*<br/>
Toto dialogové okno umožňuje uživateli řídit formát používaný při vkládání dat do složeného dokumentu. Uživatel můžete zvolit, formát dat, jestli se má vložit nebo propojit data a, jestli se má zobrazit jako ikonu. Zobrazte toto dialogové okno když uživatel vybere Vložit jinak v nabídce Upravit. Použití [colepastespecialdialog –](../mfc/reference/colepastespecialdialog-class.md) třídu dialogovému oknu.

*Změnit ikonu*<br/>
Toto dialogové okno umožňuje uživateli vybrat, jaká ikona se zobrazí pro reprezentaci propojené nebo vložené položky. Zobrazte toto dialogové okno, když uživatel vybere ikonu změnit z nabídky Úpravy nebo vybere změnit ikonu tlačítka Vložit jinak nebo převést dialogových oknech. Také zobrazte jeho když uživatel otevře dialogové okno Vložit objekt a vybere zobrazit jako ikonu. Použití [colechangeicondialog –](../mfc/reference/colechangeicondialog-class.md) třídu dialogovému oknu.

*Převést*<br/>
Toto dialogové okno umožňuje uživateli změnit typ vložené nebo propojené položky. Například pokud s vloženými metasoubor ve složeném dokumentu a později budete chtít použít jinou aplikaci k úpravě vložený metasoubor, můžete použít dialogové okno Převést. Toto dialogové okno se obvykle zobrazí kliknutím *typ položky* objektu v nabídce Úpravy a potom v nabídce kaskádové příkaz převést. Použití [coleconvertdialog –](../mfc/reference/coleconvertdialog-class.md) třídu dialogovému oknu. Například spuštění ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md).

*Upravit odkazy nebo aktualizovat odkazy*<br/>
Dialogové okno Upravit propojení umožňuje uživatelům změnit informace o zdroji propojeného objektu. Dialogové okno Aktualizovat odkazy ověří zdroje všechny propojené položky v aktuálním dialogovém okně a zobrazí dialogové okno úpravy odkazů v případě potřeby. Zobrazte dialogové okno Upravit odkazy, když se uživatel rozhodne odkazy z nabídky Úpravy. Zobrazí dialogové okno Aktualizovat odkazy se obvykle při prvním otevření složeného dokumentu. Použijte buď [colelinksdialog –](../mfc/reference/colelinksdialog-class.md) nebo [coleupdatedialog –](../mfc/reference/coleupdatedialog-class.md) třídy, v závislosti na tom, které dialogové okno, které chcete zobrazit.

*Server je zaneprázdněn nebo Server neodpovídá*<br/>
Když se uživatel pokusí o aktivaci položky a server je v současnosti nemůže žádost zpracovat, obvykle, protože server je používáno jiným uživatelem nebo úloh, zobrazí se dialogové okno Server je zaneprázdněn. Pokud server nereaguje na požadavek na aktivaci vůbec, zobrazí se dialogové okno Server neodpovídá. Tyto dialogy se zobrazují prostřednictvím `COleMessageFilter`závislosti na implementaci rozhraní OLE `IMessageFilter`, a může se rozhodnout, jestli se má opakovat žádost o aktivaci. Použití [colebusydialog –](../mfc/reference/colebusydialog-class.md) třídu dialogovému oknu.

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
