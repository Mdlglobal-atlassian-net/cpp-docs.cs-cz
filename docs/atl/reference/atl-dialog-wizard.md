---
title: Průvodce dialogem ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe3311e46ea28424717a0274fbe9e956610cdc54
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767709"
---
# <a name="atl-dialog-wizard"></a>Průvodce dialogem ATL

Tento průvodce vloží do projektu ATL objekt dialogového okna, odvozený z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Dialogové okno odvozené od `CAxDialogImpl` může být hostitelem ovládacích prvků ActiveX.

Průvodce vytvoří prostředek dialogového okna s výchozí **OK** a **zrušit** tlačítka. Můžete upravit prostředku dialogového okna a přidání ovládacích prvků ActiveX pomocí [editoru dialogového okna](../../windows/dialog-editor.md) v okně zobrazení prostředků.

Průvodce se vloží do hlavičky souboru [mapu zpráv](../../atl/message-maps-atl.md) a deklarace pro výchozí zpracování události kliknutí. Zobrazit [implementace dialogového okna](../../atl/implementing-a-dialog-box.md) Další informace o dialogová okna ATL.

**Krátký název**  
Nastaví zkrácený název objektu ATL dialogového okna. Název, který poskytnete Určuje název třídy a souboru (.cpp a .h) názvy, pokud nezměníte těchto polí samostatně.

`Class`  
Nastaví název třídy, který se má vytvořit. Tento název je založen na názvu je zadat v **krátký název**, předchází "C", typická předpona pro název třídy.

**soubor .h**  
Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

**soubor .cpp**  
Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

## <a name="see-also"></a>Viz také

[Dialogového okna ATL](../../atl/reference/adding-an-atl-dialog-box.md)

