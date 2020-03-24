---
title: Klávesy akcelerátoruC++()
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: beb4e878138da3dc2905c86e18fedc658d7ceecf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215147"
---
# <a name="accelerator-keys-c"></a>Klávesy akcelerátoruC++()

## <a name="predefined-accelerator-keys"></a>Předdefinované klávesy akcelerátoru

Existuje několik předdefinovaných kláves akcelerátorů, které mohou být součástí projektu aplikace systému Windows. Některé z těchto virtuálních klíčů jsou pro prostředí systému Windows. Ostatní podporují prohlížeč nebo aplikace Unicode. Libovolný z těchto klíčů můžete použít v jakémkoli akcelerátoru.

|Klíč|Popis|
|---------|-----------------|
|VK_ACCEPT|(IME) přijmout|
|VK_BROWSER_BACK|Systému Prohlížeč, **zpětný** klíč|
|VK_BROWSER_FAVORITES|Systému Prohlížeč, klíč **Oblíbené položky**|
|VK_BROWSER_FORWARD|Systému Prohlížeč, **dopředný** klíč|
|VK_BROWSER_HOME|Systému Prohlížeč, **spouštěcí** a **domovské** klávesy|
|VK_BROWSER_REFRESH|Systému Prohlížeč, **aktualizovat** klíč|
|VK_BROWSER_SEARCH|Systému Prohlížeč, klíč **hledání**|
|VK_BROWSER_STOP|Systému Prohlížeč, **stop** Key|
|VK_CONVERT|(IME) převod|
|VK_FINAL|(IME) finální režim|
|VK_HANGUEL|REŽIM Režim Hanguel (se zachovává pro kompatibilitu, použití VK_HANGUL)|
|VK_HANGUL|REŽIM Režim Hangul|
|VK_HANJA|REŽIM Režim Hanja|
|VK_JUNJA|REŽIM Junja režim|
|VK_KANA|REŽIM Režim kana|
|VK_KANJI|REŽIM Režim kanji|
|VK_LAUNCH_APP1|Systému **Spustit klíč aplikace 1**|
|VK_LAUNCH_APP2|Systému **Spustit klíč aplikace 2**|
|VK_LAUNCH_MAIL|Systému **Spustit poštovní** klíč|
|VK_LAUNCH_MEDIA_SELECT|Systému **Vybrat mediální** klíč|
|VK_LCONTROL|Klávesa **Ctrl + šipka vlevo**|
|VK_LMENU|Klávesa **levé nabídky**|
|VK_LSHIFT|Klávesa **levý SHIFT**|
|VK_MEDIA_NEXT_TRACK|Systému Klíč **Další stopy**|
|VK_MEDIA_PLAY_PAUSE|Systému **Přehrát/pozastavit Media** Key|
|VK_MEDIA_PREV_TRACK|Systému **Předchozí klíč stopy**|
|VK_MEDIA_STOP|Systému **Zastavit mediální** klíč|
|VK_MODECHANGE|(IME) režim žádosti o změnu|
|VK_NONCONVERT|(IME) nepřevedeno|
|VK_OEM_1|Systému Pro klávesnici US Standard, klíč **;:**|
|VK_OEM_102|Systému Klávesa lomená závorka nebo zpětné lomítko na klávesnici RT 102-Key|
|VK_OEM_2|Systému Pro klávesnici US Standard, **/?** key|
|VK_OEM_3|Systému Pro klávesnici US Standard je **`~** klíč|
|VK_OEM_4|Systému Pro klávesnici US Standard je to **[{** Key|
|VK_OEM_5|Systému Pro klávesnici US Standard je **\\&#124;**  klíč|
|VK_OEM_6|Systému Pro klávesnici US Standard, klíč **]}**|
|VK_OEM_7|Systému Pro klávesnici US Standard je klíč "Single-quote/Double-quote".|
|VK_OEM_COMMA|Systému Pro každou zemi nebo oblast **, klíč**|
|VK_OEM_MINUS|Systému U každé země nebo oblasti **-** klíč|
|VK_OEM_PERIOD|Systému V případě jakékoli země/oblasti, **.** key|
|VK_OEM_PLUS|Systému U každé země nebo oblasti **+** klíč|
|VK_PACKET|Systému Slouží k předávání znaků Unicode, jako by se jedná o stisknutí kláves.|
|VK_RCONTROL|Klávesa **CTRL + ŠIPKA vpravo**|
|VK_RMENU|Klávesa **pravé nabídky**|
|VK_RSHIFT|Klávesa **SHIFT + šipka doprava**|
|VK_SLEEP|Klíč **spánku počítače**|
|VK_VOLUME_DOWN|Systému **Odstínový** klíč|
|VK_VOLUME_MUTE|Systému Klíč **ztlumení svazku**|
|VK_VOLUME_UP|Systému Klíč ke **svazku**|
|VK_XBUTTON1|Systému **X1** – tlačítko myši|
|VK_XBUTTON2|Systému **X2** – tlačítko myši|

## <a name="accelerator-key-association"></a>Asociace klávesových zkratek

Mnohokrát budete chtít, aby položka nabídky a kombinace kláves byly vydány stejným příkazem programu. Tuto akci provedete přiřazením stejného identifikátoru prostředku (ID) k položce nabídky a záznamem v tabulce akcelerátorů vaší aplikace. Potom upravíte titulek položky nabídky a zobrazí se název akcelerátoru. Další informace o položkách nabídek a klávesách akcelerátorů naleznete v tématu [příkazy nabídky](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor akcelerátorů](../windows/accelerator-editor.md)<br/>
