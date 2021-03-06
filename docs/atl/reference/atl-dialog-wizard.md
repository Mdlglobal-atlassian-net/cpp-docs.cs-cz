---
title: Průvodce dialogem ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 043c170021ce1ceb072dba3e5a450375f556753a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248847"
---
# <a name="atl-dialog-wizard"></a>Průvodce dialogem ATL

Tento průvodce vloží do projektu ATL objekt dialogového okna, odvozený z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Dialogové okno odvozené od `CAxDialogImpl` může být hostitelem ovládacích prvků ActiveX.

Průvodce vytvoří prostředek dialogového okna s výchozí **OK** a **zrušit** tlačítka. Můžete upravit prostředku dialogového okna a přidání ovládacích prvků ActiveX pomocí [editoru dialogového okna](../../windows/dialog-editor.md) v okně zobrazení prostředků.

Průvodce se vloží do hlavičky souboru [mapu zpráv](../../atl/message-maps-atl.md) a deklarace pro výchozí zpracování události kliknutí. Zobrazit [implementace dialogového okna](../../atl/implementing-a-dialog-box.md) Další informace o dialogová okna ATL.

- **Krátký název**

   Nastaví zkrácený název objektu ATL dialogového okna. Název, který poskytnete Určuje název třídy a souboru (.cpp a .h) názvy, pokud nezměníte těchto polí samostatně.

- **Třída**

   Nastaví název třídy, který se má vytvořit. Tento název je založen na názvu je zadat v **krátký název**, předchází "C", typická předpona pro název třídy.

- **.h file**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

## <a name="see-also"></a>Viz také:

[Dialogového okna ATL](../../atl/reference/adding-an-atl-dialog-box.md)
