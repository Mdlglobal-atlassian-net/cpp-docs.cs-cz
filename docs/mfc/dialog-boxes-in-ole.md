---
title: Dialogová okna v OLE
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
ms.openlocfilehash: 997bfc0bda05f5a2520c102cb38777b533bcef95
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685778"
---
# <a name="dialog-boxes-in-ole"></a>Dialogová okna v OLE

Když uživatel spustí aplikaci s podporou technologie OLE, existují časy, kdy aplikace potřebuje informace od uživatele, aby mohla operaci provést. Třídy knihovny MFC technologie OLE poskytují počet dialogových oken pro shromáždění požadovaných informací. Toto téma obsahuje seznam úkolů zpracovávaných dialogovým oknem OLE a tříd potřebných pro zobrazení těchto dialogových oken. Podrobnosti o dialogových oknech OLE a strukturách, které slouží k přizpůsobení jejich chování, naleznete v tématu [MFC Reference](../mfc/mfc-desktop-applications.md).

*Vložit objekt*<br/>
Toto dialogové okno umožňuje uživateli vložit do složeného dokumentu nově vytvořené nebo existující objekty. Umožňuje také uživateli zvolit zobrazení položky jako ikony a povolit příkazové tlačítko změnit ikonu. Toto dialogové okno se zobrazí, když uživatel zvolí možnost Vložit objekt z nabídky upravit. Použijte třídu [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) k zobrazení tohoto dialogového okna. Všimněte si, že aplikaci MDI nelze vložit do sebe samé. Aplikaci, která je kontejnerem nebo serverem, nelze vložit do sebe samé, pokud se nejedná o aplikaci SDI.

*Vložit jinak*<br/>
Toto dialogové okno umožňuje uživateli řídit formát používaný při vkládání dat do složeného dokumentu. Uživatel může zvolit formát dat, bez ohledu na to, zda data vložit nebo propojit, a zda se má zobrazit jako ikona. Toto dialogové okno se zobrazí, když uživatel zvolí možnost Vložit jinak z nabídky upravit. Použijte třídu [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) k zobrazení tohoto dialogového okna.

*Změnit ikonu*<br/>
Toto dialogové okno umožňuje uživateli vybrat, která ikona se zobrazí, aby představovala propojenou nebo vloženou položku. Toto dialogové okno se zobrazí, když uživatel zvolí ikonu změnit z nabídky upravit nebo klepne na tlačítko změnit ikonu v dialogových oknech vložit speciální nebo převést. Zobrazí se také v případě, že uživatel otevře dialogové okno Vložit objekt a zvolí možnost Zobrazit jako ikonu. Použijte třídu [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) k zobrazení tohoto dialogového okna.

*Převést*<br/>
Toto dialogové okno umožňuje uživateli změnit typ vložené nebo propojené položky. Například pokud jste do složeného dokumentu vložili metasoubor a později chcete použít jinou aplikaci pro úpravu vloženého metasouboru, můžete použít dialogové okno převést. Toto dialogové okno se obvykle zobrazuje tak, že v nabídce Upravit kliknete na *položku objekt typu položky* a potom v nabídce CSS kliknete na možnost převést. Použijte třídu [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) k zobrazení tohoto dialogového okna. Například spusťte ukázkovou [OCLIENT](../overview/visual-cpp-samples.md)knihovny MFC OLE.

*Upravit odkazy nebo aktualizovat odkazy*<br/>
Dialogové okno Upravit odkazy umožní uživateli změnit informace o zdroji propojeného objektu. Dialogové okno aktualizovat odkazy ověří zdroje všech propojených položek v aktuálním dialogovém okně a v případě potřeby zobrazí dialogové okno Upravit odkazy. Pokud uživatel zvolí odkazy z nabídky upravit, zobrazí se dialogové okno Upravit odkazy. Dialogové okno aktualizace odkazů se obvykle zobrazuje při prvním otevření složeného dokumentu. Použijte buď třídu [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) nebo [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) , v závislosti na tom, které dialogové okno chcete zobrazit.

*Zaneprázdněný Server nebo server neodpovídá*<br/>
Dialogové okno zaneprázdněný serverem se zobrazí, když se uživatel pokusí aktivovat položku a server aktuálně nemůže požadavek zpracovat, obvykle proto, že server používá jiný uživatel nebo úloha. Pokud server vůbec nereaguje na požadavek na aktivaci, zobrazí se dialogové okno neodpovídá serveru. Tato dialogová okna se zobrazují prostřednictvím `COleMessageFilter` na základě implementace rozhraní OLE `IMessageFilter` a uživatel se může rozhodnout, jestli se má znovu pokusit o aktivaci. Použijte třídu [COleBusyDialog](../mfc/reference/colebusydialog-class.md) k zobrazení tohoto dialogového okna.

## <a name="see-also"></a>Další informace najdete v tématech

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OBJEKTŮ](../mfc/ole-in-mfc.md)
