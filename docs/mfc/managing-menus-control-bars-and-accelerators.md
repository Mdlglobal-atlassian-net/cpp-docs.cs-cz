---
title: Správa nabídek, ovládacích pruhů a akcelerátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bd7a6515e943351980051d5f2344e80119cc9d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428652"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Správa nabídek, ovládacích pruhů a akcelerátorů

Okno rámce spravuje aktualizace objektů uživatelského rozhraní, včetně nabídek, tlačítek panelu nástrojů, stavový řádek a akcelerátory. Spravuje taky sdílení nabídek v aplikace MDI.

## <a name="managing-menus"></a>Správa nabídek

Okno rámce podílí na aktualizaci položky uživatelského rozhraní pomocí mechanismu ON_UPDATE_COMMAND_UI podle [aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md). Během nečinné smyčky jsou aktualizovány tlačítka na panely nástrojů a dalších ovládacích panelů. Položky nabídky v rozevíracích nabídkách na řádku nabídek se aktualizují, těsně před plánovaným začátkem rozbalení nabídky.

Pro aplikace MDI spravuje okna rámce MDI nabídek a popisek. Okna rámce MDI vlastní jeden výchozí nabídka, která se používá jako nabídek, když nejsou žádné aktivní podřízených oken MDI. Pokud existují aktivní podřízené položky, panel nabídek okna rámce MDI převzaty nabídku aktivní podřízené okno MDI. Pokud aplikace MDI podporuje více typů dokumentů, jako jsou například dokumenty grafu a listu, každý typ vloží vlastní nabídky do nabídek a změní titulek okna hlavního rámce.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md) poskytuje výchozí implementaci pro standardní příkazy v nabídce okno, které se zobrazí pro aplikace MDI. Zejména nové okno příkazu (id_window_new –) je implementováno s cílem vytvořit nový objekt okna rámce a zobrazení pro aktuální dokument. Je nutné přepsat tyto implementace, pouze pokud je potřeba upravit vlastní nastavení.

Více podřízených oken MDI stejného typu dokumentu sdílet prostředky nabídky. Pokud několik podřízených oken MDI jsou vytvořena pomocí stejné šablony dokumentu, můžete všechny používají stejný prostředek nabídky, uložení na systémové prostředky ve Windows.

## <a name="managing-the-status-bar"></a>Správa stavového řádku

Také umístí na stavovém řádku v rámci klientské oblasti okna rámce a spravuje stav pruhu ukazatele. Vymaže okno rámce a potřeby ho aktualizuje zprávy area ve stavovém řádku a zobrazí řetězce výzev uživatel vybere položky nabídky nebo tlačítka panelu nástrojů, jak je popsáno v [zobrazení informací o příkazu ve stavovém řádku](../mfc/how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Správa akcelerátorů

Každé okno rámce udržuje tabulky akcelerátorů volitelné, který automaticky klávesnice překlad akcelerátor za vás. Tento mechanismus umožňuje snadno definovat klávesy akcelerátoru (také nazývané klávesové zkratky), které vyvolají příkazů nabídky.

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

