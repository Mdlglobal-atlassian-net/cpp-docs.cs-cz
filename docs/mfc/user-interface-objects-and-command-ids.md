---
title: "Identifikátory objektů uživatelského rozhraní a příkazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ec4b281812f66ba54d73866bce3b907d26a8ceb5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="user-interface-objects-and-command-ids"></a>Identifikátory objektů uživatelského rozhraní a příkazů
Položky nabídky, tlačítek panelu nástrojů a klávesy akcelerátoru jsou "objekty uživatelského rozhraní" schopný vytvářet příkazy. Každý uživatelského rozhraní objekt má identifikátor. Příkaz přiřazením stejné ID objektu a příkaz přidružíte objekt uživatelského rozhraní. Jak je popsáno v [zprávy](../mfc/messages.md), příkazy jsou implementované jako speciální zprávy. Obrázek "Příkazy v rámci" níže ukazuje, jak rozhraní spravuje příkazy. Objekt uživatelského rozhraní vygeneruje-li příkaz, jako například `ID_EDIT_CLEAR_ALL`, jeden z objektů v aplikaci zpracovává příkaz – na obrázku níže objekt dokumentu `OnEditClearAll` funkce je volána prostřednictvím mapy zpráv dokumentu.  
  
 ![Příkazy v rámci](../mfc/media/vc385p1.gif "vc385p1")  
Příkazy v rozhraní Framework  
  
 Obrázek "Příkaz aktualizace v rámci" níže ukazuje, jak MFC aktualizace objektů uživatelského rozhraní, jako je například položek nabídky a tlačítka panelu nástrojů. Před rozbalení nabídky nebo během nečinné smyčky v případě tlačítka panelu nástrojů, MFC směruje příkazu pro aktualizaci. Následující obrázek objekt dokument volá příkaz její aktualizační rutina `OnUpdateEditClearAll`, abyste mohli povolit nebo zakázat objekt uživatelského rozhraní.  
  
 ![Příkaz aktualizace v rámci](../mfc/media/vc385p2.png "vc385p2")  
Příkaz aktualizace v rozhraní Framework  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v rozhraní Framework](../mfc/messages-and-commands-in-the-framework.md)

