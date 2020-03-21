---
title: Přidání objektů a ovládacích prvků do projektu ATL
ms.date: 05/09/2019
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
ms.openlocfilehash: 415432eb2f5e0bc8f58fc84edaf8409ee8792f27
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075291"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Přidání objektů a ovládacích prvků do projektu ATL

> [!NOTE]
> Průvodce komponentami ATL COM+ 1,0, Průvodce OLE DB příjemce ATL a Průvodce komponentami ATL Active Server stránky nejsou k dispozici v aplikaci Visual Studio 2019 a novější.

K přidání objektu nebo ovládacího prvku do projektů založených na knihovně ATL nebo MFC lze použít jednoho z průvodců kódem ATL. Pro každý objekt modelu COM nebo ovládací prvek, který přidáte, vygeneruje průvodce soubory. cpp a. h a také soubor. rgs pro podporu registru založenou na skriptech. Následující průvodci kódem ATL jsou k dispozici v aplikaci Visual Studio:

||||
|-|-|-|
|[Jednoduchý objekt ATL](../../atl/reference/atl-simple-object-wizard.md)|[Dialog ATL](../../atl/reference/atl-dialog-wizard.md)|[Ovládací prvek ATL](../../atl/reference/atl-control-wizard.md)|
|[ATL – stránka vlastností](../../atl/reference/atl-property-page-wizard.md)|[Komponenta Active Server stránky ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[OLE DB příjemce ATL](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Přidat podporu knihovny ATL do knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Průvodce komponentami ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Zprostředkovatel OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Před přidáním objektu ATL do projektu byste si měli projít podrobnosti a požadavky pro objekt v jeho souvisejících tématech nápovědy.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Přidání objektu nebo ovládacího prvku pomocí Průvodce ovládacím prvkem ATL

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a v místní nabídce klikněte na tlačítko **Přidat** . Klikněte na **Přidat třídu**.

   Zobrazí se dialogové okno [Přidat třídu](../../ide/add-class-dialog-box.md) .

1. Pomocí složky **ATL** vybrané v podokně **kategorie** vyberte objekt, který chcete vložit z podokna **šablony** . Klikněte na **Otevřít**. Zobrazí se průvodce kódem pro vybraný objekt.

   > [!NOTE]
   > Chcete-li přidat objekt ATL do projektu knihovny MFC, je nutné přidat podporu knihovny ATL do existujícího projektu. To můžete provést podle pokynů v tématu [Přidání podpory knihovny ATL do projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Případně, pokud se pokusíte přidat objekt ATL do projektu knihovny MFC bez předchozího přidání podpory knihovny ATL, aplikace Visual Studio zobrazí výzvu k určení, zda chcete přidat podporu knihovny ATL do projektu. Klikněte na **Ano** , pokud chcete přidat podporu ATL do projektu a otevřít vybraného průvodce ATL.

## <a name="see-also"></a>Viz také

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[C++typy projektů v aplikaci Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
