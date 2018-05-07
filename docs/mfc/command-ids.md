---
title: Identifikátory příkazů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc27e39f6e2753b7b468e39c283d58c3e585d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="command-ids"></a>Identifikátory příkazů
Příkaz je podrobně popsán pomocí jejího ID příkaz samostatně (v kódování **wm_command –** zprávy). Toto ID je přiřazený k objektu uživatelského rozhraní, která generuje příkaz. Obvykle jsou pojmenované ID pro funkce, které jsou přiřazeny k objektu uživatelského rozhraní.  
  
 Například vymazat všechny položky v nabídce Upravit může být přiřazen ID jako **id_edit_clear_all –**. Knihovny tříd predefines některé identifikátory, zejména pro příkazy, že rozhraní zpracovává samostatně, jako například **id_edit_clear_all –** nebo `ID_FILE_OPEN`. Vytvoříte další identifikátory příkazů sami.  
  
 Když vytvoříte vlastní nabídky v jazyce Visual C++ editor nabídek, je vhodné postupovat podle knihovny tříd je zásady vytváření názvů vidíte `ID_FILE_OPEN`. [Standardní příkazy](../mfc/standard-commands.md) vysvětluje standardní příkazy, které jsou definované v knihovně tříd.  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)

