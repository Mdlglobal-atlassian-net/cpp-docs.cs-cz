---
title: Spolupráce s Live Share pro C++ v aplikaci Visual Studio
description: Pomocí Live Share pro C++ v aplikaci Visual Studio můžete spolupracovat a sdílet kód v reálném čase.
ms.date: 05/24/2019
ms.openlocfilehash: e6e983c6acb56dffd12756d8bbaccef32dd57f38
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077750"
---
# <a name="collaborate-using-live-share-for-c"></a>Spolupráce přes Live Share pro C++

V aplikaci Visual Studio 2019 a Visual Studio Code můžete pomocí **Live Share** spolupracovat na C++ projektech v reálném čase. **Live Share** může jiný uživatel upravovat a ladit váš kód, aniž by musel instalovat svůj projekt nebo žádnou z jeho závislostí. Uvidíte, jak se upravují změny, a každá úprava je označena jménem osoby, která ji vytvořila.

![Úpravy&#43; &#43; v jazyce C Live Share](../ide/media/live-share-edit-cpp.png "Live Share úpravy vC++")

## <a name="live-share-host-and-guests"></a>Live Share hostitel a hosty

V Live Share relace je hostitelem a jedním nebo více hostů. Hostitel i hosté můžou použít buď Visual Studio, nebo Visual Studio Code. Hostitel sady Visual Studio 2019 ve Windows může sdílet s Visual Studio Code hostem v systému Linux.

Hostitel poskytuje hostům všechno, co potřebují k zajištění produktivity. Pro hosty není nutné mít zdrojový kód, kompilátor, externí závislosti ani stejné nainstalované součásti.

Hostitelé a hosté můžou tyto funkce IntelliSense použít:

- Seznam členů
- Help – parametr
- Rychlé informace
- Ladění/zarážky
- Najít všechny odkazy
- Přejít k definici
- Hledání symbolů (CTRL + T)
- Zvýrazňování odkazů
- Diagnostika/chyby/vlnovky

![Ladění&#43; &#43; v jazyce C Live Share](../ide/media/live-share-debug-cpp.png "Live Share ladění vC++")

## <a name="start-and-end-a-live-share-session"></a>Spuštění a ukončení relace Live Share

Pokud chcete spustit relaci Live Share v aplikaci Visual Studio, klikněte na tlačítko sdílet v pravém horním rohu nebo přejděte na **soubor** > **spustit relaci spolupráce**. Tím se vygeneruje odkaz, který můžete sdílet s vašimi spolupracovníky.

![Tlačítko&#43; &#43; Live Share jazyka C](../ide/media/live-share-button-cpp.png "Live Share – tlačítko")

Chcete-li ukončit relaci, vyberte možnost **ukončit relaci spolupráce** v rozevíracím seznamu **sdílení** .

![Tlačítko&#43; &#43; Live Share jazyka C](../ide/media/live-share-end-session-cpp.png "Live Share – tlačítko")

## <a name="for-more-information"></a>Další informace

Další informace o **Live Share** v aplikaci Visual Studio najdete v tématu [co je Visual Studio Live Share?](/visualstudio/liveshare/). Další informace o Live Share v Visual Studio Code najdete v tématu [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Viz také

[Upravit a Refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Procházení základu C++ kódu v aplikaci Visual Studio](navigate-code-cpp.md)</br>
[Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>