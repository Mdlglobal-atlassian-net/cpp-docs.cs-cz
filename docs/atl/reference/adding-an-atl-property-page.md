---
title: Přidání stránky vlastností ATL
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 3e27d276e5500c1e32ca7b576b355f14f18a47f6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075264"
---
# <a name="adding-an-atl-property-page"></a>Přidání stránky vlastností ATL

> [!NOTE]
> Průvodce stránkou vlastností ATL není k dispozici v aplikaci Visual Studio 2019 a novějším.

Chcete-li přidat stránku vlastností knihovny ATL (Active Template Library) do projektu, projekt musí být vytvořen jako aplikace ATL nebo jako aplikace knihovny MFC, která obsahuje podporu knihovny ATL. [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) můžete použít k vytvoření aplikace ATL nebo k [Přidání objektu ATL do aplikace MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pro implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Pokud přidáváte stránku vlastností pro ovládací prvek, ovládací prvek musí podporovat rozhraní [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) . Ve výchozím nastavení je toto rozhraní v seznamu odvození vaší třídy ovládacího prvku při [vytváření ovládacího prvku ATL](../../atl/reference/adding-an-atl-control.md) pomocí [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Pokud vaše třída ovládacího prvku nemá [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) v seznamu odvozených tříd, je nutné ji přidat ručně.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Přidání stránky vlastností ATL do projektu

1. V buď **Průzkumník řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code)klikněte pravým tlačítkem myši na název projektu, do kterého chcete přidat stránku vlastností ATL.

1. V místní nabídce klikněte na **Přidat** a pak klikněte na **Přidat třídu**.

1. V dialogovém okně [Přidat třídu](../../ide/add-class-dialog-box.md) klikněte v podokně **šablony** na **Stránka vlastnost ATL** a potom kliknutím na tlačítko **otevřít** zobrazte [Průvodce stránkou vlastností ATL](../../atl/reference/atl-property-page-wizard.md).

Po vytvoření stránky vlastností pro ovládací prvek je třeba zadat položku [PROP_PAGE](property-map-macros.md#prop_page) v mapě vlastností ovládacího prvku.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../../atl/atl-com-property-pages.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)
