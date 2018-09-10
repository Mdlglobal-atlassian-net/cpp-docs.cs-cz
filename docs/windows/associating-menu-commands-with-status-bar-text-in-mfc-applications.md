---
title: Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16de276478485cb52b11b3f1bbb869c5b75d05a4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316754"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC

Vaše aplikace knihovny MFC můžete zobrazit popisný text pro všechny příkazy nabídek, které může uživatel vybrat. To provedete tak, že přiřadíte textový řetězec pro každý pomocí příkazu nabídky **výzvy** vlastnost **vlastnosti** okna. Pokud máte řetězci [tabulka řetězců](../windows/string-editor.md) jehož ID je stejný jako příkaz, aplikace knihovny MFC, automaticky zobrazí tento prostředek řetězce ve stavovém řádku běžící aplikaci. když uživatel najede myší položku nabídky.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Chcete přidružit k příkazu nabídky stavového řádku textový řetězec

1. V **nabídky** editoru, vyberte příkaz nabídky.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte text přidružený stavového řádku v **výzvy** pole.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Přidání komentářů k nabídce](../windows/adding-commands-to-a-menu.md)  
[Editor nabídek](../windows/menu-editor.md)