---
title: Třídy společných dialogů OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e3cedbe3cd08a425bd2bde2b4a6ca8c5a493c72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-common-dialog-classes"></a>Společné třídy dialogových oken OLE
Tyto třídy zpracování běžných úloh OLE implementací počet standardní dialogových oken OLE. Obsahují taky konzistentní uživatelské rozhraní pro funkci OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Používá rozhraní tak, aby obsahovala běžné implementace pro všechny dialogových oken OLE. Všechny třídy dialogových oken v kategorii uživatelského rozhraní jsou odvozené z této základní třídy. `COleDialog` nelze použít přímo.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Zobrazí dialogové okno Vložit objekt, standardní uživatelské rozhraní, pro vkládání nové OLE propojené nebo vložené položky.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Zobrazí Vložit jinak dialogové okno, standardní uživatelské rozhraní pro implementaci příkaz Upravit Vložit jinak.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Zobrazí dialogové okno Upravit odkazy, standardní uživatelské rozhraní pro úpravy informace o propojené položky.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Zobrazí dialogové okno Změnit ikonu, standardní uživatelské rozhraní pro změny, které ikony přidružené OLE vložené nebo propojené položky.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod OLE – položky z jednoho typu do jiného.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Zapouzdří běžné vlastnosti OLE dialogové okno. Společná dialogová okna OLE vlastnosti poskytují snadný způsob, jak zobrazit a upravit vlastnosti položky OLE dokumentu v souladu s normami systému Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní k aktualizaci všech propojení v dokumentu. Dialogové okno obsahuje indikátor průběhu k označení, jak blízko aktualizace je dokončen.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cílová nebo zdrojová odkazu.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Zobrazí zaneprázdněný Server a Server neodpovídá dialogových oknech, standardní uživatelské rozhraní pro zpracování volání do zaneprázdněn aplikací. Obvykle zobrazují automaticky pomocí `COleMessageFilter` implementace.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

