---
title: Identifikátory příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: ecec4a7bd705dc74a3f45cc07da4abcdb168f43f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445627"
---
# <a name="command-ids"></a>Identifikátory příkazů

Příkaz je podrobně popsané podle jejího ID. příkaz samostatně (kódovaný **wm_command –** zprávy). Toto ID se přiřadí objekt uživatelského rozhraní, který generuje příkazu. Obvykle jsou pojmenovány ID pro funkci objektu uživatelského rozhraní, které jsou přiřazeny.

Vymazat všechny položky v nabídce Úpravy může být přiřadit například ID, jako **id_edit_clear_all –**. Knihovna tříd predefines některé ID, zejména pro příkazy, že rozhraní framework zpracovává, jako například **id_edit_clear_all –** nebo **id_file_open –**. Vytvoříte další identifikátory příkazů sami.

Když vytvoříte vlastní nabídky v jazyce Visual C++ editor nabídek, je vhodné postupovat podle knihovna tříd je zásady vytváření názvů vidíte **id_file_open –**. [Standardní příkazy](../mfc/standard-commands.md) vysvětluje standardní příkazy definované v knihovně tříd rozhraní.

## <a name="see-also"></a>Viz také

[Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)

