---
title: Globální klávesové zkratky
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508567"
---
# <a name="global-hot-keys"></a>Globální klávesové zkratky

Globální klávesová zkratka je přidružená k určitému nepodřízenému oknu. Umožňuje uživateli aktivovat okno z jakékoli části systému. Aplikace nastaví globální klávesovou zkratku pro konkrétní okno odesláním zprávy [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) do tohoto okna. Například pokud `m_HotKeyCtrl` je objekt [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) a `pMainWnd` je ukazatelem na okno, které má být aktivováno při stisknutí klávesové zkratky, můžete použít následující kód k přidružení klávesové zkratky zadaného v ovládacím prvku s oknem, na které ukazuje. `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Pokaždé, když uživatel stiskne globální klávesovou zkratku, zadané okno obdrží zprávu [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) , která určuje **SC_HOTKEY** jako typ příkazu. Tato zpráva také aktivuje okno, které ho přijme. Vzhledem k tomu, že tato zpráva neobsahuje žádné informace o přesném stisknutí klávesy, použití této metody neumožňuje rozlišovat různé klávesové zkratky, které mohou být připojeny ke stejnému oknu. Klávesová zkratka zůstane platná, dokud nebude aplikace, která odesílá **WM_SETHOTKEY** , ukončena.

## <a name="see-also"></a>Viz také:

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
