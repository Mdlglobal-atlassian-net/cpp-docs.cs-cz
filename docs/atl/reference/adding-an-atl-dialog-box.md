---
title: Přidání dialogového okna ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ebbb610debe5d480cd1161149f89c4d357f9cd02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275793"
---
# <a name="adding-an-atl-dialog-box"></a>Přidání dialogového okna ATL

Přidání dialogového okna knihovny ATL do projektu, váš projekt musí být projekt knihovny ATL nebo projektu knihovny MFC, včetně podpory knihovny ATL. Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Ve výchozím nastavení, Průvodce dialogem ATL implementuje dialog odvozený od [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Tato třída obsahuje podporu pro hostování ovládacích prvků ActiveX a Windows. Pokud nechcete, aby nároky na podporu ovládacích prvků ActiveX, jakmile v Průvodci vygenerovala kódu, nahraďte všechny výskyty `CAxDialogImpl` s oběma [CSimpleDialog](../../atl/reference/csimpledialog-class.md) nebo [CDialogImpl](../../atl/reference/cdialogimpl-class.md) jako základní třídy. .

> [!NOTE]
> `CSimpleDialog` vytvoří pouze modálních dialogových oken, které podporují pouze běžných ovládacích prvků Windows. `CDialogImpl` Vytvoří modální a nemodální dialogová okna.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Chcete-li přidat dialogu knihovny ATL do projektu

1. Vytvořte projekt knihovny ATL pomocí [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md).

1. Z [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu a klikněte na tlačítko **přidat** z místní nabídky. Klikněte na tlačítko **přidejte třídu**.

1. V **šablony** podokně [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, klikněte na tlačítko **ATL Dialog**. Klikněte na tlačítko **otevřít** zobrazíte [Průvodce dialogem ATL](../../atl/reference/atl-dialog-wizard.md).

Další informace najdete v tématu [implementace dialogového okna](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Třídy oken](../../atl/atl-window-classes.md)<br/>
[Mapy zpráv](../../atl/message-maps-atl.md)
