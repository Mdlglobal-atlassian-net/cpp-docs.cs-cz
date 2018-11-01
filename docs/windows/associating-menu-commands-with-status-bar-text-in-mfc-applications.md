---
title: Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
ms.openlocfilehash: fc39695358a9c1f2f62878487a5e4fedf5db2b82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468884"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC

Vaše aplikace knihovny MFC můžete zobrazit popisný text pro všechny příkazy nabídek, které může uživatel vybrat. To provedete tak, že přiřadíte textový řetězec pro každý pomocí příkazu nabídky **výzvy** vlastnost **vlastnosti** okna. Pokud máte řetězci [tabulka řetězců](../windows/string-editor.md) jehož ID je stejný jako příkaz, aplikace knihovny MFC, automaticky zobrazí tento prostředek řetězce ve stavovém řádku běžící aplikaci. když uživatel najede myší položku nabídky.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Chcete přidružit k příkazu nabídky stavového řádku textový řetězec

1. V **nabídky** editoru, vyberte příkaz nabídky.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte text přidružený stavového řádku v **výzvy** pole.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Přidání komentářů k nabídce](../windows/adding-commands-to-a-menu.md)<br/>
[Editor nabídek](../windows/menu-editor.md)