---
title: Nabídky a prostředky (OLE) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efe0a5f6dae2cece571eddabc4094ebb87df175b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-ole"></a>Nabídky a prostředky (OLE)
Tato skupina článků popisuje použití nabídky a prostředky v aplikacích MFC OLE dokumentu.  
  
 OLE úpravy s náhledem umístí další požadavky na v nabídce a dalším prostředkům poskytované OLE – aplikace dokumentů, protože nejsou k dispozici několika režimy v které i kontejneru a aplikací (součást) může být spuštění a použita. Úplný server aplikace můžete například spustit v některém z těchto tří režimech:  
  
-   Samostatná.  
  
-   Na místě pro úpravy položky v rámci kontejneru.  
  
-   Otevřete pro úpravy položky mimo kontext jeho kontejneru, často v samostatném okně.  
  
 To vyžaduje tři samostatné nabídky rozložení, jeden pro každou možné režimu aplikace. Tabulky akcelerátoru jsou také nezbytné pro každý nový režim. Kontejner aplikace může nebo nemusí podporovat aktivace na místě; Pokud ano, potřebuje nové struktury nabídky a související tabulky akcelerátoru.  
  
 Aktivace na místě vyžaduje, že kontejner a serverové aplikace musí si vyjednat nabídky panelu nástrojů a stav prostoru panelu. Všechny prostředky musí být vytvořeny s to na paměti. Článek [nabídky a prostředky: sloučení nabídky](../mfc/menus-and-resources-menu-merging.md) popisuje Toto téma podrobně.  
  
 Kvůli těmto problémům OLE – aplikace dokumentů vytvořené pomocí Průvodce aplikace může mít až čtyři samostatné nabídky a prostředky tabulka akcelerátoru. Ty se používají z následujících důvodů:  
  
|Název prostředku|Použití|  
|-------------------|---------|  
|**IDR_MAINFRAME**|Používat v aplikaci MDI, pokud žádný soubor je otevřený, nebo v aplikaci SDI bez ohledu na to otevřených souborů. Toto je standardní nabídky použité v aplikacích jiných než OLE.|  
|**IDR_\<Projekt > typ**|V aplikaci MDI použít, pokud existují otevřené soubory. Použít, když aplikace běží samostatné. Toto je standardní nabídky použité v aplikacích jiných než OLE.|  
|**IDR_\<Projekt > TYPE_SRVR_IP**|Používaný server nebo kontejneru při objekt je otevřený v místě.|  
|**IDR_\<Projekt > TYPE_SRVR_EMB**|Aplikace serveru používá objekt se při otevření bez použití aktivace na místě.|  
  
 Každý z těchto názvy prostředků představuje nabídky a obvykle tabulky akcelerátorů. Podobně jako schéma je třeba použít v aplikacích MFC, které nejsou vytvořené pomocí Průvodce aplikací.  
  
 Následující články popisují témata související s kontejnery, servery a v nabídce slučování nezbytné k implementaci aktivace na místě:  
  
-   [Nabídky a prostředky: Kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md)  
  
-   [Nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md)  
  
-   [Nabídky a prostředky: Sloučení nabídky](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)

