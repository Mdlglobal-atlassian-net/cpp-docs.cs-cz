---
title: Přidání ovládacího prvku ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 26667c2ad3bb2cedb42767fe42ff0ad358fa6d66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487682"
---
# <a name="adding-an-atl-control"></a>Přidání ovládacího prvku ATL

Tohoto průvodce použijte k přidání do projektu, který podporuje rozhraní pro všechny potenciální kontejnery objekt uživatelského rozhraní. Pro podporu těchto rozhraní projektu musí být vytvořen jako aplikace ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

## <a name="to-add-an-atl-control-to-your-project"></a>Chcete-li přidat ovládací prvek ATL do projektu

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat jednoduchý objekt knihovny ATL.

1. Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../../ide/add-class-dialog-box.md) kliknutím na dialogové okno, v podokně šablony **ovládací prvek ATL**a potom klikněte na tlačítko **přidat** zobrazíte [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md).

Použití **Průvodce ovládacími prvky ATL**, můžete vytvořit jeden ze tří typů ovládacích prvků:

- Standardní ovládací prvek

- Složený ovládací prvek

- Ovládací prvek DHTML

Kromě toho může snížit velikost ovládacího prvku a odebrání rozhraní, které nejsou používány nástrojem většina kontejnery tak, že vyberete **minimální ovládací prvek** na **možnosti** stránky průvodce.

## <a name="see-also"></a>Viz také

[Přidání funkcí do složeného ovládacího prvku](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)
