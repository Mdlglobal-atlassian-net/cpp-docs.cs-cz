---
title: Spolupráce s live share pro C++ v Visual Studiu
description: Pomocí živého sdílení pro C++ ve Visual Studiu můžete spolupracovat a sdílet kód v reálném čase.
ms.date: 05/24/2019
ms.openlocfilehash: 0ebdd77d0e277778b48cf69024b24841f775d968
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377289"
---
# <a name="collaborate-using-live-share-for-c"></a>Spolupráce přes Live Share pro C++

V Sadě Visual Studio 2019 a Visual Studio Code můžete pomocí **live share** spolupracovat na projektech C++ v reálném čase. S **Live Share** může jiný člověk upravovat a ladit váš kód bez nutnosti instalace projektu nebo některé z jeho závislostí. Při jejich výskytu se zobrazují úpravy ostatních a každá úprava je označena jménem osoby, která je provedla.

![C&#43;&#43; Live Share Úpravy](../ide/media/live-share-edit-cpp.png "Živé úpravy sdílení v jazyce C++")

## <a name="live-share-host-and-guests"></a>Live Share hostitele a hosty

V relaci Live Share je hostitel a jeden nebo více hostů. Hostitel i hosté mohou používat visual studio nebo kód sady Visual Studio. Hostitel Visual Studia 2019 v systému Windows může sdílet s hostem kódu Visual Studia na Linuxu.

Hostitel poskytuje hostům vše, co potřebují, aby byli produktivní. Hosté nemusí mít zdrojový kód, kompilátor, externí závislosti nebo dokonce stejné nainstalované součásti.

Hostitel a hosté mohou používat tyto funkce Technologie IntelliSense:

- Seznam členů
- Nápověda k parametrům
- Rychlé informace
- Ladění/zarážky
- Najít všechny odkazy
- Přejít na definici
- Hledání symbolů (Ctrl+T)
- Zvýraznění odkazů
- Diagnostika/Chyby/Vlnky

![C&#43;&#43; Živé ladění sdílení](../ide/media/live-share-debug-cpp.png "Živé ladění sdílení v jazyce C++")

## <a name="start-and-end-a-live-share-session"></a>Zahájení a ukončení relace živého sdílení

Chcete-li zahájit relaci živého sdílení v sadě Visual Studio, klepněte na tlačítko Sdílet v pravém horním rohu nebo přejděte na**Relaci spolupráce při zahájení** **souborů** > . Tím se vygeneruje odkaz, který můžete sdílet se svými spolupracovníky.

![C&#43;&#43; tlačítko Živé sdílení](../ide/media/live-share-button-cpp.png "Tlačítko Živé sdílení")

Chcete-li ukončit relaci, vyberte v rozevíracím souboru **Sdílení** možnost **Ukončit relaci spolupráce.**

![C&#43;&#43; tlačítko Živé sdílení](../ide/media/live-share-end-session-cpp.png "Tlačítko Živé sdílení")

## <a name="for-more-information"></a>Další informace

Další informace o **živé sdílení** ve Visual Studiu najdete v tématu Co je Visual Studio [Live Share?](/visualstudio/liveshare/). Další informace o živé sdílení v kódu sady Visual Studio najdete v tématu [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Viz také

[Upravit a refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navigace v základu kódu Jazyka C++ v sadě Visual Studio](navigate-code-cpp.md)</br>
[Čtení a pochopení kódu C++](read-and-understand-code-cpp.md)</br>
