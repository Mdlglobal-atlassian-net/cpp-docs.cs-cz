---
title: "Přidání stránky vlastností ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abf50e98d32789e357f5e13339ee2fc0a0daa331
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-property-page"></a>Přidání stránky vlastnosti knihovny ATL
Pokud chcete přidat stránku vlastností Active Template Library (ATL) do projektu, projektu musí být vytvořen jako aplikace knihovny ATL nebo MFC aplikaci, která obsahuje podpory knihovny ATL Můžete použít [ATL – Průvodce projektem](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt knihovny ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) implementovat ATL – podpora pro aplikace MFC.  
  
 Pokud přidáváte stránky vlastností pro ovládací prvek, musí podporovat vlastního ovládacího prvku [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) rozhraní. Ve výchozím nastavení, toto rozhraní je v seznamu odvození ovládacího prvku třídy, kdy jste [vytvoření ovládacího prvku knihovny ATL](../../atl/reference/adding-an-atl-control.md) pomocí [Průvodce ovládacím prvkem ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Pokud vaše třída ovládacích prvků nemá [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) ve svém seznamu odvození je musí přidat ručně.  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>Chcete-li přidat stránku vlastností knihovny ATL do projektu  
  
1.  Buď **Průzkumníku řešení** nebo [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název projektu, do které chcete přidat stránku vlastností ATL.  
  
2.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat třídu**.  
  
3.  V [přidat třídu](../../ide/add-class-dialog-box.md) kliknutím na dialogové okno, v podokně šablon **stránka vlastností ATL** a pak klikněte na **otevřete** zobrazíte [ATL vlastnost stránky průvodce](../../atl/reference/atl-property-page-wizard.md).  
  
 Jakmile vytvoříte stránky vlastností pro ovládací prvek, je nutné zadat [PROP_PAGE](property-map-macros.md#prop_page) položku v mapě vlastností pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../../atl/atl-com-property-pages.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)

