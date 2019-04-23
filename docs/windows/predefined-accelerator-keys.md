---
title: Klávesy akcelerátoru (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027509"
---
# <a name="accelerator-keys-c"></a>Klávesy akcelerátoru (C++)

## <a name="predefined-accelerator-keys"></a>Předdefinované klávesy akcelerátoru

Existuje mnoho z předdefinované klávesy akcelerátoru, které mohou být součástí projektu aplikace Windows. Některé z těchto virtuální klíče jsou pro prostředí Windows. Jiné podporují prohlížeč nebo aplikace kódování Unicode. Můžete použít některý z těchto klíčů v jakékoli akcelerátoru.

|Key|Popis|
|---------|-----------------|
|VK_ACCEPT|(IME) přijměte|
|VK_BROWSER_BACK|(Windows) Prohlížeč, **zpět** klíč|
|VK_BROWSER_FAVORITES|(Windows) Prohlížeč, **Oblíbené** klíč|
|VK_BROWSER_FORWARD|(Windows) Prohlížeč, **vpřed** klíč|
|VK_BROWSER_HOME|(Windows) Prohlížeč, **Start** a **Domů** klíč|
|VK_BROWSER_REFRESH|(Windows) Prohlížeč, **aktualizovat** klíč|
|VK_BROWSER_SEARCH|(Windows) Prohlížeč, **hledání** klíč|
|VK_BROWSER_STOP|(Windows) Prohlížeč, **Zastavit** klíč|
|VK_CONVERT|Převést (IME)|
|VK_FINAL|Poslední režim (IME)|
|VK_HANGUEL|(IME) Režim Hanguel (zachován z důvodu kompatibility, použijte VK_HANGUL)|
|VK_HANGUL|(IME) Korejská režimu|
|VK_HANJA|(IME) Režim Hanja|
|VK_JUNJA|(IME) Režim Junja|
|VK_KANA|(IME) Režim Kana|
|VK_KANJI|(IME) Režim Kanji|
|VK_LAUNCH_APP1|(Windows) **Spuštění aplikace 1** klíč|
|VK_LAUNCH_APP2|(Windows) **Spuštění aplikace 2** klíč|
|VK_LAUNCH_MAIL|(Windows) **Spustit poštu** klíč|
|VK_LAUNCH_MEDIA_SELECT|(Windows) **Výběr média** klíč|
|VK_LCONTROL|**Vlevo Ctrl** klíč|
|VK_LMENU|**Nabídku vlevo** klíč|
|VK_LSHIFT|**Posunutí doleva** klíč|
|VK_MEDIA_NEXT_TRACK|(Windows) **Další stopa** klíč|
|VK_MEDIA_PLAY_PAUSE|(Windows) **Pauzy a přehrávání médií** klíč|
|VK_MEDIA_PREV_TRACK|(Windows) **Předchozí stopa** klíč|
|VK_MEDIA_STOP|(Windows) **Zastavit média** klíč|
|VK_MODECHANGE|Žádost o změnu režimu (IME)|
|VK_NONCONVERT|Nonconvert (IME)|
|VK_OEM_1|(Windows) Pro americké standardní klávesnici **;:** klíč|
|VK_OEM_102|(Windows) Lomená závorka klíč nebo zpětné lomítko klávesu na klávesnici 102 klávesami RT|
|VK_OEM_2|(Windows) Pro americké standardní klávesnici **/?** klíč|
|VK_OEM_3|(Windows) Pro americké standardní klávesnici **`~** klíč|
|VK_OEM_4|(Windows) Pro americké standardní klávesnici **[{** klíč|
|VK_OEM_5|(Windows) Pro americké standardní klávesnici **\\ &#124;** klíč|
|VK_OEM_6|(Windows) Pro americké standardní klávesnici **]}** klíč|
|VK_OEM_7|(Windows) Pro americké standardní klávesnice klíč "single nabídky/dvojité uvozovky"|
|VK_OEM_COMMA|(Windows) Pro žádné země ani oblasti **,** klíč|
|VK_OEM_MINUS|(Windows) Pro žádné země ani oblasti **-** klíč|
|VK_OEM_PERIOD|(Windows) Pro žádné země ani oblasti **.** klíč|
|VK_OEM_PLUS|(Windows) Pro žádné země ani oblasti **+** klíč|
|VK_PACKET|(Windows) Sloužící k předávání znaky znakové sady Unicode, jako by šlo úhozy na klávesnici.|
|VK_RCONTROL|**Pravé Ctrl** klíč|
|VK_RMENU|**Nabídka vpravo** klíč|
|VK_RSHIFT|**Pravý Shift** klíč|
|VK_SLEEP|**Počítač v režimu spánku** klíč|
|VK_VOLUME_DOWN|(Windows) **Svazku dolů** klíč|
|VK_VOLUME_MUTE|(Windows) **Svazku Ztlumit** klíč|
|VK_VOLUME_UP|(Windows) **Svazku nahoru** klíč|
|VK_XBUTTON1|(Windows) **X1** tlačítko myši.|
|VK_XBUTTON2|(Windows) **X2** tlačítko myši.|

## <a name="accelerator-key-association"></a>Přiřazení klíče akcelerátoru

V mnoha případech má položku nabídky a kombinace kláves pro stejný příkaz programu. Tuto akci proveďte, přiřazením stejný identifikátor prostředku (ID) na položku nabídky a záznam v tabulce akcelerátorů vaší aplikace. Potom upravte položku nabídky titulek, aby se zobrazil název akcelerátoru. Další informace o položky nabídky a přístupové klávesy, naleznete v tématu [příkazy nabídky](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editor akcelerátorů](../windows/accelerator-editor.md)<br/>