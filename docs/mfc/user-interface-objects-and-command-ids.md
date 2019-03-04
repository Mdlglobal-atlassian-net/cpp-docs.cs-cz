---
title: Identifikátory objektů uživatelského rozhraní a příkazů
ms.date: 11/19/2018
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
ms.openlocfilehash: 54372facc51062add122c1db2e01e3081127512e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278415"
---
# <a name="user-interface-objects-and-command-ids"></a>Identifikátory objektů uživatelského rozhraní a příkazů

Položky nabídky, tlačítek panelu nástrojů a přístupové klávesy "objektů uživatelského rozhraní" jsou schopné generování příkazů. Každý takový objekt uživatelského rozhraní nemá identifikátor. Přidružíte objekt uživatelského rozhraní pomocí příkazu přiřazením stejné ID objektu a příkazu. Jak je vysvětleno v [zprávy](../mfc/messages.md), příkazy jsou implementovány jako speciální zprávy. Obrázek "Příkazy v rámci" níže ukazuje, jak rozhraní framework spravuje příkazy. Když objekt uživatelského rozhraní generuje příkazu, například `ID_EDIT_CLEAR_ALL`, jeden z objektů v aplikace zpracovává příkaz – na obrázku níže, objekt dokumentu `OnEditClearAll` přes mapu zpráv dokumentu je volána funkce.

![Příkazy v rámci](../mfc/media/vc385p1.gif "příkazy v rámci") <br/>
Příkazy v rámci

"Příkaz aktualizace v rámci" následující obrázek ukazuje, jak MFC aktualizace objektů uživatelského rozhraní, jako je například položky nabídky a tlačítka panelu nástrojů. Předtím, než nabídka se rozbalí nebo během nečinné smyčky v případě tlačítka na panelu nástrojů MFC směruje příkazu k aktualizaci. Na následujícím obrázku, objekt dokumentu volá příkaz její aktualizační rutina `OnUpdateEditClearAll`, můžete povolit nebo zakázat objekt uživatelského rozhraní.

![Příkaz aktualizace v rámci](../mfc/media/vc385p2.png "aktualizace v rámci příkazu") <br/>
Příkaz aktualizace v rámci

## <a name="see-also"></a>Viz také:

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
