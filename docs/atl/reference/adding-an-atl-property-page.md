---
title: Přidání stránky vlastností ATL
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: ed715cd822aaf0f55b8898efc80b5514938ca8ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668065"
---
# <a name="adding-an-atl-property-page"></a>Přidání stránky vlastností ATL

Chcete-li do svého projektu přidat stránku vlastností Active Template Library (ATL), váš projekt musí být vytvořen jako aplikace ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Pokud přidáváte stránky vlastností pro ovládací prvek, ovládací prvek musí podporovat [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) rozhraní. Ve výchozím nastavení, toto rozhraní je v seznamu odvození ovládacího prvku třídu při vám [vytvoření ovládacího prvku ATL](../../atl/reference/adding-an-atl-control.md) pomocí [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Pokud nemá žádné třídy vašeho ovládacího prvku [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) ve svém seznamu odvození, je třeba přidat ji ručně.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Přidání stránky vlastností ATL do projektu

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat stránku vlastností ATL.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../../ide/add-class-dialog-box.md) v dialogu **šablony** podokně klikněte na tlačítko **stránka vlastností knihovny ATL** a potom klikněte na **otevřít** zobrazíte [Průvodce stránkou vlastností ATL](../../atl/reference/atl-property-page-wizard.md).

Jakmile vytvoříte stránky vlastností pro ovládací prvek, je nutné zadat [PROP_PAGE](property-map-macros.md#prop_page) položky v mapování ovládacího prvku.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../../atl/atl-com-property-pages.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)
