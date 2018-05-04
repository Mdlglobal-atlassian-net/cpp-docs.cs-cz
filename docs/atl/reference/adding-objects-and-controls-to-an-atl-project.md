---
title: Přidání objektů a ovládacích prvků do projektu knihovny ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.controls
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a6f9102aeebd0cc60765c70cf74fb2329bc801f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Přidání objektů a ovládacích prvků do projektu knihovny ATL
Některého z průvodců kódu ATL můžete přidat do vašich projektů na základě knihovny ATL nebo MFC objekt nebo ovládacího prvku. Pro každý objekt COM nebo ovládací prvek přidáte, Průvodce generuje sada a souborů .h, jakož i soubor .rgs pro podporu založených na skriptech registru. Následující kód průvodce ATL jsou k dispozici v sadě Visual Studio:  
  
||||  
|-|-|-|  
|[Jednoduchého objektu knihovny ATL](../../atl/reference/atl-simple-object-wizard.md)|[Dialogové okno knihovny ATL](../../atl/reference/atl-dialog-wizard.md)|[Ovládací prvek ATL](../../atl/reference/atl-control-wizard.md)|  
|[Stránka vlastností knihovny ATL](../../atl/reference/atl-property-page-wizard.md)|[Komponenty ASP knihovny ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[Přidání podpory knihovny ATL s knihovnou MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Zprostředkovatel OLE DB knihovny ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  Před přidáním objektu knihovny ATL do projektu, měli byste zkontrolovat podrobnosti a požadavky pro objekt v příslušných tématech nápovědy.  
  
### <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Chcete-li přidat objekt nebo ovládacího prvku s použitím Průvodce ovládacím prvkem knihovny ATL  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na uzel projektu a klikněte na tlačítko **přidat** z místní nabídky. Klikněte na tlačítko **přidejte třídu**.  
  
     [Přidat třídu](../../ide/add-class-dialog-box.md) zobrazí se dialogové okno.  
  
2.  Složky knihovny ATL vybrané v podokně Kategorie vyberte objekt vložit z podokna šablony. Klikněte na tlačítko **otevřete**. Zobrazí se Průvodce kód pro vybraný objekt.  
  
    > [!NOTE]
    >  Pokud chcete přidat objekt knihovny ATL do projektu MFC, musíte přidat podpory knihovny ATL do existujícího projektu. To provedete podle pokynů v [přidání podpory knihovny ATL do projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
     Případně pokud se pokusíte přidat objekt knihovny ATL do projektu MFC bez dříve přidání podpory knihovny ATL, Visual Studio vás vyzve k určete, jestli má podpory knihovny ATL přidané do projektu. Klikněte na tlačítko **Ano** otevřete Průvodce vybrané knihovny ATL a přidání podpory knihovny ATL do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem knihovny ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

