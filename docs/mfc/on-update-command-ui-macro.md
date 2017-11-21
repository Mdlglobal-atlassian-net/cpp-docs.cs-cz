---
title: "On_update_command_ui – makro | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ON_UPDATE_COMMAND_UI
dev_langs: C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 64b9c77d8c851364790d61e7844b46f25880168c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI – makro
Použití **vlastnosti** okno pro připojení objektu uživatelského rozhraní pro obslužnou rutinu aktualizace příkaz v příkazu cílový objekt. Se automaticky připojí ID objektu uživatelské rozhraní `ON_UPDATE_COMMAND_UI` makro a vytvořit obslužnou rutinu v objektu, která zpracuje aktualizaci. V tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md) Další informace.  
  
 Například pokud chcete aktualizovat příkaz Vymazat vše v nabídce Upravit vašeho programu, použijte **vlastnosti** okno Přidat položku mapování zpráv ve vybrané třídě deklaraci funkce pro obslužné rutiny aktualizace příkazů jmenuje `OnUpdateEditClearAll` ve třídě deklarace a šablonu prázdný funkce v souboru implementace třídy. Prototyp funkce vypadá takto:  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 Všechny rutiny, zobrazí funkce, jako **afx_msg** – klíčové slovo. Jako všechny obslužné rutiny aktualizace, jak dlouho trvá jeden argument, odkazy `CCmdUI` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

