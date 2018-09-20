---
title: Globální klávesové zkratky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d749fad0fabf8ae99bba129caee399e3f93ff9af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443849"
---
# <a name="global-hot-keys"></a>Globální klávesové zkratky

Globální klávesové zkratky je přidružen konkrétní nonchild okna. Umožňuje, aby uživatel mohl aktivovat okno z jakékoliv části systému. Aplikace nastaví globální klávesové zkratky pro konkrétní okno odesláním [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) zprávy do tohoto okna. Například pokud `m_HotKeyCtrl` je [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objektu a `pMainWnd` je ukazatel do okna a aktivovat, když se stiskne klávesovou zkratku, můžete použít následující kód k přidružení klávesovou zkratku zadaný v ovládacím prvku s v okně odkazované `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Pokaždé, když uživatel stiskne Globální klávesové zkratky, zadané okno přijímá [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) zprávu, která určuje **SC_HOTKEY** jako typ příkazu. Tato zpráva také aktivuje okně, které obdrží. Protože tuto zprávu neobsahuje žádné informace o přesnou klávesy, která byla stisknuta v okamžiku, pomocí této metody není povoleno rozlišování mezi různé klávesové zkratky, které mohou připojit pro stejné okno. Klávesové zkratky zůstane platný až do aplikace, která odeslala **WM_SETHOTKEY** ukončí.

## <a name="see-also"></a>Viz také

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

