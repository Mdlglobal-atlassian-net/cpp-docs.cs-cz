---
title: Identifikátory příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: 76071105e72f1ca4a851b9cdb76d5f1a96f44edb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219889"
---
# <a name="command-ids"></a>Identifikátory příkazů

Příkaz je podrobně popsané podle jejího ID. příkaz samostatně (kódovaný **wm_command –** zprávy). Toto ID se přiřadí objekt uživatelského rozhraní, který generuje příkazu. Obvykle jsou pojmenovány ID pro funkci objektu uživatelského rozhraní, které jsou přiřazeny.

Vymazat všechny položky v nabídce Úpravy může být přiřadit například ID, jako **id_edit_clear_all –**. Knihovna tříd predefines některé ID, zejména pro příkazy, že rozhraní framework zpracovává, jako například **id_edit_clear_all –** nebo **id_file_open –**. Vytvoříte další identifikátory příkazů sami.

Když vytvoříte vlastní nabídek ve Vizuálu C++ editor nabídek, je vhodné postupovat podle knihovna tříd je zásady vytváření názvů vidíte **id_file_open –**. [Standardní příkazy](../mfc/standard-commands.md) vysvětluje standardní příkazy definované v knihovně tříd rozhraní.

## <a name="see-also"></a>Viz také:

[Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)
