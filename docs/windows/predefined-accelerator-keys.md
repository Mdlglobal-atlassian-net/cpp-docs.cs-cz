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
ms.openlocfilehash: 6ef8f84564d6fd1957452971cb1e88dc99aa27e9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320507"
---
# <a name="accelerator-keys-c"></a>Klávesy akcelerátoru (C++)

## <a name="predefined-accelerator-keys"></a>Předdefinované klávesy akcelerátoru

Existuje mnoho z předdefinované klávesy akcelerátoru, které mohou být součástí projektu aplikace Windows. Některé z těchto virtuální klíče jsou pro prostředí Windows. Další podpora prohlížeče nebo aplikace kódování Unicode. Můžete použít některý z těchto klíčů v jakékoli akcelerátoru.

|Key|Popis|
|---------|-----------------|
|VK_ACCEPT|Přijměte editoru IME|
|VK_BROWSER_BACK|Windows: Klíč Back prohlížeče|
|VK_BROWSER_FAVORITES|Windows: Klíč Oblíbené položky prohlížeče|
|VK_BROWSER_FORWARD|Windows: Forward klíč prohlížeče|
|VK_BROWSER_HOME|Windows: Spuštění prohlížeče a domovské klíče|
|VK_BROWSER_REFRESH|Windows: Prohlížeč obnovovací klíč|
|VK_BROWSER_SEARCH|Windows: Klíč hledání prohlížeče|
|VK_BROWSER_STOP|Windows: Klíč Stop prohlížeče|
|VK_CONVERT|Převést as|
|VK_FINAL|Poslední režim editoru IME|
|VK_HANGUEL|Režim editoru IME Hanguel (zachován z důvodu kompatibility; použijte VK_HANGUL)|
|VK_HANGUL|Režim editoru IME Korejská|
|VK_HANJA|Režim editoru IME Hanja|
|VK_JUNJA|Režim editoru IME Junja|
|VK_KANA|Režim editoru IME Kana|
|VK_KANJI|Režim editoru IME Kanji|
|VK_LAUNCH_APP1|Windows: Klíč aplikace 1|
|VK_LAUNCH_APP2|Windows: Klíč aplikace 2|
|VK_LAUNCH_MAIL|Windows: Klíč e-mailu|
|VK_LAUNCH_MEDIA_SELECT|Windows: Vyberte klíč média|
|VK_LCONTROL|Klávesy vlevo|
|VK_LMENU|Klíč nabídku vlevo|
|VK_LSHIFT|Klíč POSUNUTÍ doleva|
|VK_MEDIA_NEXT_TRACK|Windows: Další klíč sledování|
|VK_MEDIA_PLAY_PAUSE|Windows: Klíč pauzy a přehrávání média|
|VK_MEDIA_PREV_TRACK|Windows: Předchozí stopa klíč|
|VK_MEDIA_STOP|Windows: Zastavit klíč média|
|VK_MODECHANGE|Žádost o změnu režimu editoru IME|
|VK_NONCONVERT|Editor IME nonconvert|
|VK_OEM_1|Windows: Pro americké standardní klávesnici ";:' klíč|
|VK_OEM_102|Windows: Lomená závorka klíč nebo zpětné lomítko klávesu na klávesnici 102 klávesami RT|
|VK_OEM_2|Windows: Pro americké standardní klávesnici "/?" klíč|
|VK_OEM_3|Windows: Pro americké standardní klávesnici "~" klíč|
|VK_OEM_4|Windows: Pro americké standardní klávesnici "[{" klíč|
|VK_OEM_5|Windows: Pro americké standardní klávesnici "\\&#124;" klíč|
|VK_OEM_6|Windows: Pro standardní uživatelské USA "]}" klíče|
|VK_OEM_7|Windows: Pro americké standardní klávesnice klíč "single nabídky/dvojité uvozovky"|
|VK_OEM_COMMA|Windows: Pro žádné země ani oblasti, klíč ""|
|VK_OEM_MINUS|Windows: Pro žádné země ani oblasti "-" klíč|
|VK_OEM_PERIOD|Windows: Pro žádné země ani oblasti "." klíč|
|VK_OEM_PLUS|Windows: Pro žádné země ani oblasti, klíč '+'|
|VK_PACKET|Windows: Sloužící k předávání znaky znakové sady Unicode, jako by šlo úhozy na klávesnici.|
|VK_RCONTROL|Ovládací PRVEK vpravo klíč|
|VK_RMENU|Vpravo nabídka key|
|VK_RSHIFT|Klávesa SHIFT doprava|
|VK_SLEEP|Klíč v režimu spánku počítače|
|VK_VOLUME_DOWN|Windows: Svazek dolů|
|VK_VOLUME_MUTE|Windows: Ztlumit klíč svazku|
|VK_VOLUME_UP|Windows: Svazek nahoru|
|VK_XBUTTON1|Windows: Tlačítko myši x1|
|VK_XBUTTON2|Windows: Tlačítko myši x2|

## <a name="accelerator-key-association"></a>Přiřazení klíče akcelerátoru

V mnoha případech má položku nabídky a kombinace kláves pro stejný příkaz programu. To provedete tak, že stejný identifikátor prostředku (ID) přiřadíte k položce nabídky a záznam v tabulce akcelerátorů vaší aplikace. Potom upravte položku nabídky titulek, aby se zobrazil název akcelerátoru. Další informace o položky nabídky a přístupové klávesy, naleznete v tématu [přiřazení položky nabídky ke klávese akcelerátoru](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor akcelerátorů](../windows/accelerator-editor.md)<br/>