---
title: "Standardní příkazy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbdb763b2d7da04267a195e5d534da9528f2b74d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="standard-commands"></a>Standardní příkazy
Rozhraní framework definuje mnoho zpráv standardních příkazů. ID pro tyto příkazy obvykle mít formu:  
  
 **Id_** *zdroj*_*položky*  
  
 kde *zdroj* je obvykle název nabídky a *položky* je položku nabídky. ID příkazu pro příkaz nové v nabídce Soubor je například `ID_FILE_NEW`. Identifikátory standardních příkazů jsou zobrazeny tučně v dokumentaci. Programátorem definované identifikátory jsou uvedené v písmo, které se liší od okolního textu.  
  
 Následuje seznam některé nejdůležitější podporované příkazy:  
  
 *Příkazy nabídky Soubor*  
 Nový otevřete, zavřete, uložit, uložit jako, nastavení stránky, nastavení tisku, tisk, náhled, ukončení a naposledy použité soubory.  
  
 *Příkazy nabídky Upravit*  
 Vymazat, zrušte všechny, kopírování, vyjímání, najít, vložení, opakujte, nahraďte, Vybrat vše vrátit zpět a vrátit.  
  
 *Příkazy nabídky zobrazení*  
 Panel nástrojů a stavový řádek.  
  
 *Příkazy nabídky okna*  
 Nový, uspořádání, přeneseny, dlaždici vodorovných, dlaždici svislého a rozdělení.  
  
 *Příkazy nabídky nápovědy*  
 Index, pomocí nápovědy a o.  
  
 *Příkazy OLE (nabídka Úpravy)*  
 Vložit nový objekt, upravit odkazy, vložte odkaz, Vložit jinak a *typename* objektu (příkaz příkazů).  
  
 Rozhraní framework poskytuje různé úrovně podpory pro tyto příkazy. Některé příkazy jsou podporovány pouze jako identifikátory definované příkazů, zatímco jiné jsou podporovány důkladné implementace. Například rozhraní implementuje příkaz Otevřít v nabídce Soubor ve vytvoření nového objektu dokumentu, zobrazení otevřené dialogové okno, otevírání a čtení souboru. Naproti tomu je nutné implementovat příkazy nabídky upravit sami, od příkazy, jako je **id_edit_copy –** závisí na povaze data kopírujete.  
  
 Další informace o příkazech podporovány a úroveň implementace poskytuje najdete v tématu [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md). Standardní příkazy jsou definovány v souboru AFXRES. H.  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)

