---
title: "Přidání ovládacího prvku knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb5ad74cf1905b14db46cb119766914e5e57f6cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-atl-control"></a>Přidání ovládacího prvku knihovny ATL
Pomocí tohoto průvodce můžete přidat objekt uživatelského rozhraní pro projekt, který podporuje rozhraní pro všechny potenciální kontejnery. Pro podporu těchto rozhraní, projekt musí být vytvořen jako aplikace knihovny ATL nebo jako aplikace knihovny MFC, který obsahuje podpory knihovny ATL Můžete použít [ATL – Průvodce projektem](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt knihovny ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) implementovat ATL – podpora pro aplikace MFC.  
  
### <a name="to-add-an-atl-control-to-your-project"></a>Přidání ovládacího prvku knihovny ATL do projektu  
  
1.  Buď **Průzkumníku řešení** nebo [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název projektu, do které chcete přidat ATL jednoduchého objektu.  
  
2.  Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **přidat třídu**.  
  
3.  V [přidat třídu](../../ide/add-class-dialog-box.md) kliknutím na dialogové okno, v podokně šablon **ovládací prvek ATL**a potom klikněte na **přidat** zobrazíte [Průvodce ovládacím prvkem ATL](../../atl/reference/atl-control-wizard.md).  
  
 Pomocí **Průvodce ovládacím prvkem ATL**, můžete vytvořit tři typy ovládacích prvků:  
  
-   Standardního ovládacího prvku  
  
-   Složeného ovládacího prvku  
  
-   Ovládací prvek DHTML  
  
 Kromě toho může snížit velikost ovládacího prvku a odebrat rozhraní, které nejsou využívány většina kontejnery výběrem **minimální ovládací prvek** na **možnosti** stránce průvodce.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkcí do složeného ovládacího prvku](../../atl/adding-functionality-to-the-composite-control.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Ukázka ATLFire](http://msdn.microsoft.com/en-us/5b2649f1-f45b-4cfb-9c4b-4d9459c26b09)

