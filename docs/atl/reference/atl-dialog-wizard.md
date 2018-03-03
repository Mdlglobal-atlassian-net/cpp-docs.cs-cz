---
title: "ATL – dialogové okno Průvodce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6cdf16b3e82ce69fa06b3eacda8d7b48643fb3c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-dialog-wizard"></a>Dialogové okno Průvodce knihovny ATL
Tento průvodce vloží do projektu objekt dialogového okna knihovny ATL odvozený od [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Dialogové okno odvozené z `CAxDialogImpl` může hostovat ovládací prvky ActiveX.  
  
 Průvodce vytvoří prostředek dialogové okno s výchozí **OK** a **zrušit** tlačítka. Můžete upravit prostředku dialogového okna a přidat ovládací prvky ActiveX pomocí [editoru dialogového okna](../../windows/dialog-editor.md) v zobrazení zdrojů.  
  
 Průvodce vloží do soubor hlaviček [mapy zpráv](../../atl/message-maps-atl.md) a deklarace pro zpracování výchozí položku události. V tématu [implementace dialogové okno](../../atl/implementing-a-dialog-box.md) Další informace o dialogových oken ATL.  
  
 **Krátký název**  
 Nastaví zkrácený název pro objekt knihovny ATL dialogové okno. Poskytnutý název určuje název třídy a (sada a .h) názvy souborů, pokud nezměníte tato pole samostatně.  
  
 `Class`  
 Nastaví název třídy, který se má vytvořit. Tento název je založen na názvu poskytují v **krátký název**, předcházet "C", typická předpona pro název třídy.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu poskytují v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud zvolíte existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **souboru**  
 Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **krátký název**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno knihovny ATL](../../atl/reference/adding-an-atl-dialog-box.md)

