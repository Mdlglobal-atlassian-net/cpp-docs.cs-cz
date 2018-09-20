---
title: Předdefinované klávesy akcelerátoru (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70392d5654c5ed550e61bccf460d641bd4995349
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430602"
---
# <a name="predefined-accelerator-keys-c"></a>Předdefinované klávesy akcelerátoru (C++)

Existuje mnoho z předdefinované klávesy akcelerátoru, které mohou být součástí projektu aplikace Windows. Některé z těchto virtuální klíče jsou pro prostředí Windows. Další podpora prohlížeče nebo aplikace kódování Unicode. Můžete použít některý z těchto klíčů v jakékoli akcelerátoru.

|Key|Popis|
|---------|-----------------|
|VK_ACCEPT|Přijměte editoru IME|
|VK_BROWSER_BACK|Windows: Zpět v prohlížeči klávesu|
|VK_BROWSER_FAVORITES|Windows: Klíč Oblíbené položky prohlížeče|
|VK_BROWSER_FORWARD|Windows: Forward klíč prohlížeče|
|VK_BROWSER_HOME|Windows: Klíč spuštění prohlížeče a domovské|
|VK_BROWSER_REFRESH|Windows: Prohlížeč-obnovit klíč|
|VK_BROWSER_SEARCH|Windows: Klíč hledání prohlížeče|
|VK_BROWSER_STOP|Windows: Klíč prohlížeč-zastavit|
|VK_CONVERT|Převést as|
|VK_FINAL|Poslední režim editoru IME|
|VK_HANGUEL|Režim editoru IME Hanguel (zachován z důvodu kompatibility; použijte VK_HANGUL)|
|VK_HANGUL|Režim editoru IME Korejská|
|VK_HANJA|Režim editoru IME Hanja|
|VK_JUNJA|Režim editoru IME Junja|
|VK_KANA|Režim editoru IME Kana|
|VK_KANJI|Režim editoru IME Kanji|
|VK_LAUNCH_APP1|Windows: Klíč spuštění aplikace 1|
|VK_LAUNCH_APP2|Windows: Klíč spuštění aplikace 2|
|VK_LAUNCH_MAIL|Windows: E-mailu počáteční klíč|
|VK_LAUNCH_MEDIA_SELECT|Windows: Výběr klíč média|
|VK_LCONTROL|Klávesy vlevo|
|VK_LMENU|Klíč nabídku vlevo|
|VK_LSHIFT|Klíč POSUNUTÍ doleva|
|VK_MEDIA_NEXT_TRACK|Windows: Další sledování klávesu|
|VK_MEDIA_PLAY_PAUSE|Windows: Klíč pauzy a přehrávání média|
|VK_MEDIA_PREV_TRACK|Windows: Předchozí stopa klíč|
|VK_MEDIA_STOP|Windows: Klíč média Stop|
|VK_MODECHANGE|Žádost o změnu režimu editoru IME|
|VK_NONCONVERT|Editor IME nonconvert|
|VK_OEM_1|Windows: pro standardní uživatelské USA ";:' klíč|
|VK_OEM_102|Windows: Buď lomená závorka klíč nebo zpětné lomítko klávesu na klávesnici 102 klávesami RT|
|VK_OEM_2|Windows: pro standardní uživatelské USA "/?" klíč|
|VK_OEM_3|Windows: pro standardní uživatelské USA "~" klíč|
|VK_OEM_4|Windows: pro standardní uživatelské USA "[{" klíč|
|VK_OEM_5|Windows: pro standardní uživatelské USA "\\&#124;" klíč|
|VK_OEM_6|Windows: pro standardní uživatelské USA "]}" klíče|
|VK_OEM_7|Windows: pro standardní uživatelské USA, klíč "single nabídky/dvojité uvozovky"|
|VK_OEM_COMMA|Windows: pro žádné země ani oblasti, klíč ""|
|VK_OEM_MINUS|Windows: pro žádné země ani oblasti "-" klíč|
|VK_OEM_PERIOD|Windows: pro žádné země ani oblasti "." klíč|
|VK_OEM_PLUS|Windows: pro žádné země ani oblasti, klíč '+'|
|VK_PACKET|Windows: Sloužící k předávání znaky znakové sady Unicode, jako by byly úhozy na klávesnici.|
|VK_RCONTROL|Ovládací PRVEK vpravo klíč|
|VK_RMENU|Vpravo nabídka key|
|VK_RSHIFT|Klávesa SHIFT doprava|
|VK_SLEEP|Klíč v režimu spánku počítače|
|VK_VOLUME_DOWN|Windows: Svazek klávesy|
|VK_VOLUME_MUTE|Windows: Ztlumit klíč svazku|
|VK_VOLUME_UP|Windows: Svazek klíč|
|VK_XBUTTON1|Windows: X1 tlačítko myši|
|VK_XBUTTON2|Windows: X2 tlačítko myši|

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor akcelerátorů](../windows/accelerator-editor.md)<br/>
[Editory prostředků](../windows/resource-editors.md)