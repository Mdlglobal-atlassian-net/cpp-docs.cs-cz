---
title: Přidání objektů a ovládacích prvků do projektu ATL | Dokumentace Microsoftu
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
ms.openlocfilehash: a5cb510bb02f71f71b35191d3ba9c4fee6b7059d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093958"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Přidání objektů a ovládacích prvků do projektu ATL

Některého z průvodců kódu knihovny ATL slouží k přidání objektu nebo ovládacího prvku do vašich projektů na základě knihovny ATL nebo MFC. Pro každý objekt modelu COM nebo ovládacího prvku přidáte, průvodce se vygeneruje, .cpp a .h souborů, jakož i souboru .rgs pro podporu založených na skriptech registru. Následující průvodci kódem knihovny ATL jsou k dispozici v sadě Visual Studio:

||||
|-|-|-|
|[Jednoduchý objekt knihovny ATL](../../atl/reference/atl-simple-object-wizard.md)|[ATL Dialog](../../atl/reference/atl-dialog-wizard.md)|[Ovládací prvek ATL](../../atl/reference/atl-control-wizard.md)|
|[Stránka vlastností knihovny ATL](../../atl/reference/atl-property-page-wizard.md)|[Komponenta knihovny ATL Active Server Page](../../atl/reference/atl-active-server-page-component-wizard.md)|[Příjemce knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Přidat podporu ATL do MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Zprostředkovatel knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Před přidáním objekt knihovny ATL do projektu, měli byste zkontrolovat podrobnosti a požadavky pro objekt v příslušných tématech nápovědy.

### <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Chcete-li přidat objekt nebo ovládacího prvku s použitím Průvodce ovládacími prvky ATL

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu a klikněte na tlačítko **přidat** z místní nabídky. Klikněte na tlačítko **přidejte třídu**.

   [Přidat třídu](../../ide/add-class-dialog-box.md) zobrazí se dialogové okno.

2. Ve složce ATL vybrané v podokně Kategorie vyberte objekt vložit v podokně šablony. Klikněte na tlačítko **otevřít**. Zobrazí se Průvodce kód pro vybraný objekt.

   > [!NOTE]
   >  Pokud chcete přidat objekt ATL do projektu knihovny MFC, musíte přidat podporu ATL do existujícího projektu. Můžete to provést pomocí následujících pokynů [přidání podpory knihovny ATL do projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Můžete také při pokusu o přidání objektu ATL bez dříve přidání podpory knihovny ATL do projektu knihovny MFC, Visual Studio vás vyzve k určení, zda chcete podpory knihovny ATL přidané do projektu. Klikněte na tlačítko **Ano** přidat podporu ATL do projektu a otevřete Průvodce vybrané knihovny ATL.

## <a name="see-also"></a>Viz také

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tvorba desktopových projektů pomocí průvodců aplikací](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

