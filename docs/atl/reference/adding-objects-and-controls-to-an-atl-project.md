---
title: Přidání objektů a ovládacích prvků do projektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: d16e9a9e7b92d2a98f8994227c5641994677fdda
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221207"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Přidání objektů a ovládacích prvků do projektu ATL

Některého z průvodců kódu knihovny ATL slouží k přidání objektu nebo ovládacího prvku do vašich projektů na základě knihovny ATL nebo MFC. Pro každý objekt modelu COM nebo ovládacího prvku přidáte, průvodce se vygeneruje, .cpp a .h souborů, jakož i souboru .rgs pro podporu založených na skriptech registru. Následující průvodci kódem knihovny ATL jsou k dispozici v sadě Visual Studio:

||||
|-|-|-|
|[Jednoduchý objekt knihovny ATL](../../atl/reference/atl-simple-object-wizard.md)|[ATL Dialog](../../atl/reference/atl-dialog-wizard.md)|[ATL Control](../../atl/reference/atl-control-wizard.md)|
|[Stránka vlastností knihovny ATL](../../atl/reference/atl-property-page-wizard.md)|[Komponenta knihovny ATL Active Server Page](../../atl/reference/atl-active-server-page-component-wizard.md)|[Příjemce knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Přidat podporu ATL do MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Zprostředkovatel knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Před přidáním objekt knihovny ATL do projektu, měli byste zkontrolovat podrobnosti a požadavky pro objekt v příslušných tématech nápovědy.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Chcete-li přidat objekt nebo ovládacího prvku s použitím Průvodce ovládacími prvky ATL

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a klikněte na tlačítko **přidat** z místní nabídky. Klikněte na tlačítko **přidejte třídu**.

   [Přidat třídu](../../ide/add-class-dialog-box.md) zobrazí se dialogové okno.

1. S **ATL** do vybrané složky **kategorie** podokně, vyberte příslušný objekt pro vložení z **šablony** podokně. Klikněte na tlačítko **otevřít**. Zobrazí se Průvodce kód pro vybraný objekt.

   > [!NOTE]
   > Pokud chcete přidat objekt ATL do projektu knihovny MFC, musíte přidat podporu ATL do existujícího projektu. Můžete to provést pomocí následujících pokynů [přidání podpory knihovny ATL do projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Můžete také při pokusu o přidání objektu ATL bez dříve přidání podpory knihovny ATL do projektu knihovny MFC, Visual Studio vás vyzve k určení, zda chcete podpory knihovny ATL přidané do projektu. Klikněte na tlačítko **Ano** přidat podporu ATL do projektu a otevřete Průvodce vybrané knihovny ATL.

## <a name="see-also"></a>Viz také:

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[C++typy projektů v sadě Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
