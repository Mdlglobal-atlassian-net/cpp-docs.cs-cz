---
title: "Identifikátory příkazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b651c734fbd7098705801aefcaa490293a4d661d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-ids"></a>Identifikátory příkazů
Příkaz je podrobně popsán pomocí jejího ID příkaz samostatně (v kódování **wm_command –** zprávy). Toto ID je přiřazený k objektu uživatelského rozhraní, která generuje příkaz. Obvykle jsou pojmenované ID pro funkce, které jsou přiřazeny k objektu uživatelského rozhraní.  
  
 Například vymazat všechny položky v nabídce Upravit může být přiřazen ID jako **id_edit_clear_all –**. Knihovny tříd predefines některé identifikátory, zejména pro příkazy, že rozhraní zpracovává samostatně, jako například **id_edit_clear_all –** nebo `ID_FILE_OPEN`. Vytvoříte další identifikátory příkazů sami.  
  
 Když vytvoříte vlastní nabídky v jazyce Visual C++ editor nabídek, je vhodné postupovat podle knihovny tříd je zásady vytváření názvů vidíte `ID_FILE_OPEN`. [Standardní příkazy](../mfc/standard-commands.md) vysvětluje standardní příkazy, které jsou definované v knihovně tříd.  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)

