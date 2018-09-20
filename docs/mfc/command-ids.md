---
title: Identifikátory příkazů | Dokumentace Microsoftu
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
ms.openlocfilehash: 5087c271151793169cbf7350f78750044ccead0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446969"
---
# <a name="command-ids"></a>Identifikátory příkazů

Příkaz je podrobně popsané podle jejího ID. příkaz samostatně (kódovaný **wm_command –** zprávy). Toto ID se přiřadí objekt uživatelského rozhraní, který generuje příkazu. Obvykle jsou pojmenovány ID pro funkci objektu uživatelského rozhraní, které jsou přiřazeny.

Vymazat všechny položky v nabídce Úpravy může být přiřadit například ID, jako **id_edit_clear_all –**. Knihovna tříd predefines některé ID, zejména pro příkazy, že rozhraní framework zpracovává, jako například **id_edit_clear_all –** nebo **id_file_open –**. Vytvoříte další identifikátory příkazů sami.

Když vytvoříte vlastní nabídky v jazyce Visual C++ editor nabídek, je vhodné postupovat podle knihovna tříd je zásady vytváření názvů vidíte **id_file_open –**. [Standardní příkazy](../mfc/standard-commands.md) vysvětluje standardní příkazy definované v knihovně tříd rozhraní.

## <a name="see-also"></a>Viz také

[Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)

