---
title: "Postupy: aktualizace objektů uživatelského rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79a5b24c1e9d71f422748f4c6fb8cba97786462d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-update-user-interface-objects"></a>Postupy: aktualizace objektů uživatelského rozhraní
Položky nabídky a tlačítka panelu nástrojů obvykle mají více než jeden stav. Položky nabídky například je šedý (neaktivní), pokud není k dispozici v rámci přítomen. Položky nabídky může být také zaškrtnuté nebo nezaškrtnuté. Tlačítka panelu nástrojů může být zakázán i pokud není k dispozici nebo je možné zkontrolovat.  
  
 Kdo aktualizuje stav tyto položky jako programu podmínky změnu logicky, pokud položku nabídky generuje příkaz, který se zpracovává souborem, indikované, dokument, má smysl mít dokumentu aktualizovat položku nabídky. Dokument pravděpodobně obsahuje informace, na kterých je založena aktualizace.  
  
 Pokud příkaz obsahuje více objektů uživatelského rozhraní (možná položku nabídky a tlačítka panelu nástrojů), obě jsou směrovány do stejné funkce obslužné rutiny. To zapouzdří kódu aktualizace uživatelského rozhraní pro všechny objekty ekvivalentní uživatelského rozhraní na jednom místě.  
  
 Rozhraní framework poskytuje pohodlné rozhraní pro automatické aktualizace objektů uživatelského rozhraní. Můžete provést aktualizaci jiným způsobem, ale rozhraní dodané je efektivní a snadno se používá.  
  
 Následující témata vysvětlují použití obslužné rutiny aktualizace.  
  
-   [Kdy jsou volány obslužné rutiny aktualizace](../mfc/when-update-handlers-are-called.md)  
  
-   [On_update_command_ui – makro](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI – třída](../mfc/the-ccmdui-class.md)  
  
## <a name="see-also"></a>Viz také  
 [Nabídky](../mfc/menus-mfc.md)

