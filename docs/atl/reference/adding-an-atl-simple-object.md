---
title: Přidání jednoduchého objektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 95a93268ca76516c1b3f736c106518ae6d94cc27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261615"
---
# <a name="adding-an-atl-simple-object"></a>Přidání jednoduchého objektu ATL

Chcete-li do svého projektu přidat objekt ATL (knihovnu Active Template Library), váš projekt musí být vytvořen jako aplikace ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Můžete definovat rozhraní modelu COM pro nový objekt knihovny ATL při vytvoření, nebo je přidat později pomocí [implementovat rozhraní](../../ide/implement-interface-wizard.md) příkaz **zobrazení tříd** nabídku.

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Přidání jednoduchého objektu ATL do projektu knihovny ATL modelu COM

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat jednoduchý objekt knihovny ATL.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../../ide/add-class-dialog-box.md) v dialogu **šablony** podokně klikněte na tlačítko **jednoduchý objekt knihovny ATL**a potom klikněte na **otevřít** zobrazíte [Průvodce jednoduchým objektem ATL](../../atl/reference/atl-simple-object-wizard.md).

1. Nastavit další možnosti pro váš projekt na [možnosti](../../atl/reference/options-atl-simple-object-wizard.md) stránku **jednoduchý objekt knihovny ATL** průvodce.

1. Klikněte na tlačítko **Dokončit** pro přidání objektu do projektu.

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání nového rozhraní projektu ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Přidání bodů připojení objektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Přidání metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC Class](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání generické třídy jazyka C++](../../ide/adding-a-generic-cpp-class.md)
