---
title: Aktivace (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70017721fb59fa0c6d18d568546d9618257328b5
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="activation-c"></a>Aktivace (C++)
Tento článek vysvětluje roli aktivace ve visual úpravy OLE – položky. Poté, co uživatel má vložené položky OLE v kontejneru dokumentu, bude pravděpodobně nutné použít. K tomuto účelu poklepání položku, která aktivuje této položky. Nejčastěji se vyskytující aktivity pro aktivaci upravuje. Mnoho aktuální položky OLE, pokud je aktivován pro úpravy, způsobit nabídek a panelů nástrojů v aktuálním okně s rámečkem změnit tak, aby odrážela ty, které patří do serverové aplikace, který položku vytvořil. Toto chování známé jako místní aktivace, umožňuje uživatelům upravovat libovolnou položku vložené v složeného dokumentu bez opuštění okna dokumentu kontejneru.  
  
 Je také možné upravit vložené položky OLE v samostatném okně. To se stane, pokud aplikace na kontejneru nebo server nepodporuje aktivace na místě. V takovém případě při poklepání vložené položky, je server aplikace spuštěna v samostatném okně a vložená položka je zobrazena jako svůj vlastní dokument. Uživatel upravuje položky v tomto okně. Po dokončení úprav uživatel serverové aplikace se zavře a vrátí do kontejnerové aplikace.  
  
 Jako alternativu, uživatel může vybrat "Otevřít úpravy" s  **\<objekt > Otevřete** příkaz na **upravit** nabídky. Objekt se otevře v samostatném okně.  
  
> [!NOTE]
>  Úprava vložených položek v samostatném okně byl standardní chování v verze 1 OLE a některé aplikace rozhraní OLE mohou podporovat pouze tento styl úprav.  
  
 Aktivace na místě zvýší úroveň na střed dokumentu přístup k vytváření dokumentů. Uživatel může považovat za složeného dokumentu jedna entita, na něm pracovat bez přepínání mezi aplikacemi. Aktivace na místě se ale používá pouze pro vložené položky, ne pro propojené položky: je potřeba je upravit v samostatném okně. To je proto propojené položky je ve skutečnosti uložený na jiné místo. Úpravy propojené položky probíhá v rámci skutečné kontextu dat, to znamená, kde jsou data uložená. Úpravy propojené položky v samostatném okně upozorní uživatele, který data patří do jiného dokumentu.  
  
 MFC nepodporuje vnořené aktivace na místě. Pokud vytvoříte aplikaci typu server/kontejner a zda je server/kontejner vložené do jiného kontejneru a aktivaci ho nelze v místě aktivovat objekty vložená do ho.  
  
 Co se stane vložené položky při poklepání ho závisí na příkazy definován pro položku. Informace najdete v tématu [aktivace: příkazy](../mfc/activation-verbs.md).  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [Kontejnery](../mfc/containers.md)   
 [Servery](../mfc/servers.md)

