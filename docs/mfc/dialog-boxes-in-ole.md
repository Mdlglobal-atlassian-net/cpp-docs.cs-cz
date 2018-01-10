---
title: "Dialogová okna v prostředí OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96dfe1828ae3451411adf3ab57c1ec67db24c34e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-boxes-in-ole"></a>Dialogová okna v prostředí OLE
Když uživatel spustí aplikaci OLE povolena, jsou časy, když aplikace potřebuje informace od uživatele, aby bylo možné provést operaci. Třídy MFC OLE poskytují několik dialogových oken získat požadované informace. Toto téma obsahuje seznam úloh zpracovávaných dialogových oken OLE a třídy, které jsou potřebné k zobrazování těchto dialogových oken. Informace o dialogových oknech OLE a struktury používané k přizpůsobení jejich chování najdete v tématu [odkaz knihovny MFC](../mfc/mfc-desktop-applications.md).  
  
 *Insert – objekt*  
 Toto dialogové okno umožňuje uživatelům vložení nově vytvořený nebo stávající objekty do složeného dokumentu. Také umožňuje uživateli vybrat zobrazení položky jako ikonu a umožňuje změnit ikonu příkazového tlačítka. Toto dialogové okno zobrazí, když uživatel vybere objekt vložit z nabídky Úpravy. Použití [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) třída k zobrazení tohoto dialogového okna. Všimněte si, že aplikace MDI nelze vložit do sebe sama. Aplikace, která je server/kontejner nelze vložit do sebe, pokud je aplikace SDI.  
  
 *Vložte speciální*  
 Toto dialogové okno umožňuje uživateli řídit formát použitý při vkládání dat do složeného dokumentu. Uživatel může vybrat formát dat, jestli se má vložit nebo propojit data a jestli se mají zobrazit jako ikonu. Toto dialogové okno zobrazení, když uživatel vybere Vložit jinak v nabídce Upravit. Použití [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) třída k zobrazení tohoto dialogového okna.  
  
 *Změnit ikonu*  
 Toto dialogové okno umožňuje uživateli vybrat, které, zobrazí se ikona představují propojené nebo vložené položky. Když uživatel vybere ikonu změnit z nabídky Úpravy nebo zvolí na tlačítko Změnit ikonu Vložit jinak nebo převést dialogových oken, zobrazí toto dialogové okno. Také zobrazte ji když uživatel otevře dialogové okno Vložit objekt a vybere zobrazit jako ikonu. Použití [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) třída k zobrazení tohoto dialogového okna.  
  
 *Převést*  
 Toto dialogové okno umožňuje uživatelům změnit typ vložené nebo propojené položky. Například pokud vložených metasoubory v složeného dokumentu a později se chcete k úpravě embedded metafile použijte jiná aplikace, můžete dialogové okno Převést. Toto dialogové okno se obvykle zobrazují kliknutím *typ položky* objekt v nabídce Upravit a pak v nabídce kaskádových příkaz převést. Použití [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) třída k zobrazení tohoto dialogového okna. Příklad, ukázku MFC OLE spustit [OCLIENT](../visual-cpp-samples.md).  
  
 *Upravit nebo aktualizace odkazů*  
 Dialogové okno Upravit propojení umožňuje uživatelům změnit informace o zdroji propojeného objektu. Dialogové okno Aktualizovat odkazy ověřuje zdroje všechny propojené položky v dialogovém okně aktuální a v případě potřeby zobrazí dialogové okno Upravit propojení. Když uživatel vybere odkazy z nabídky Úpravy, zobrazte dialogové okno Upravit propojení. Při prvním otevření složené dokumentu je obvykle zobrazí dialogové okno Aktualizovat odkazy. Použijte buď [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) nebo [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) třídy, v závislosti na tom, které dialogové okno, které chcete zobrazit.  
  
 *Server je zaneprázdněn nebo Server neodpovídá*  
 Když se uživatel pokusí o aktivaci položku a server je v současnosti nemůže žádost zpracovat, obvykle, protože je server používá jiný uživatel nebo úloha, zobrazí se dialogové okno Server zaneprázdněn. Pokud server nereaguje na požadavek na aktivaci vůbec, zobrazí se dialogové okno Server neodpovídá. Tyto dialogy zobrazují prostřednictvím `COleMessageFilter`, podle implementace rozhraní OLE **IMessageFilter**, a uživatele můžete rozhodnout, zda k pokusu o žádost o aktivaci opakujte. Použití [COleBusyDialog](../mfc/reference/colebusydialog-class.md) třída k zobrazení tohoto dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

