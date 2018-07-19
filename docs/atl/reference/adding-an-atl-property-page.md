---
title: Přidání stránky vlastností ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54546c590104545a7ea5cd80bfaa774f5391cef3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956565"
---
# <a name="adding-an-atl-property-page"></a>Přidání stránky vlastností ATL
Chcete-li do svého projektu přidat stránku vlastností Active Template Library (ATL), váš projekt musí být vytvořen jako aplikace ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.  
  
 Pokud přidáváte stránky vlastností pro ovládací prvek, ovládací prvek musí podporovat [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) rozhraní. Ve výchozím nastavení, toto rozhraní je v seznamu odvození ovládacího prvku třídu při vám [vytvoření ovládacího prvku ATL](../../atl/reference/adding-an-atl-control.md) pomocí [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Pokud nemá žádné třídy vašeho ovládacího prvku [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) ve svém seznamu odvození, je třeba přidat ji ručně.  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>Přidání stránky vlastností ATL do projektu  
  
1.  V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat stránku vlastností ATL.  
  
2.  V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu**.  
  
3.  V [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, v podokně šablon, klikněte na tlačítko **stránka vlastností knihovny ATL** a potom klikněte na tlačítko **otevřít** zobrazíte [Průvodce stránkou vlastností ATL](../../atl/reference/atl-property-page-wizard.md).  
  
 Jakmile vytvoříte stránky vlastností pro ovládací prvek, je nutné zadat [PROP_PAGE](property-map-macros.md#prop_page) položky v mapování ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../../atl/atl-com-property-pages.md)   
 [Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)

