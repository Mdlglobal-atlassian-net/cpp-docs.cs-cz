---
title: Spolupráce s živými sdílenou složkou pro C++ v sadě Visual Studio
description: Pomocí Live Share pro C++ v sadě Visual Studio ke spolupráci a sdílení kódu v reálném čase.
ms.date: 05/24/2019
ms.openlocfilehash: 8886bb3ea4b7389a9d6953655e2dc6ccfa1c7c9a
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743393"
---
# <a name="collaborate-using-live-share-for-c"></a>Spolupráce pomocí Live Share proC++

Visual Studio 2019 a Visual Studio Code, můžete použít **Live Share** ke spolupráci na C++ projektů v reálném čase. S **Live Share** jinou osobu můžete upravit a ladění kódu, aniž byste museli nainstalovat do projektu nebo některá z jejích závislostí. Jak k nim dojde, a každé úpravě označené s názvem osoby, která se zobrazí úpravy uživatele toho druhého. 

![C&#43; &#43; živé úpravy sdílenou složku](../ide/media/live-share-edit-cpp.png "živé úpravy sdílené složkyC++")

## <a name="live-share-host-and-guests"></a>Živé sdílenou složku hostitele a hostů

V rámci relace Live Share je hostitele a nejméně hosty. Visual Studio nebo Visual Studio Code, můžete použít hostitele a hostů. Visual Studio 2019 hostitele, na Windows můžete sdílet s Visual Studio Code hostovaného v Linuxu.

Hostitel poskytuje hostů se vším, co potřebují k zajištění produktivity. Hosté nemusí mít zdrojový kód, kompilátor, externí závislosti, nebo dokonce stejné nainstalované součásti. 

Tyto funkce technologie IntelliSense můžete použít hostitele a hostů: 

- Seznam členů
- Parametr nápovědy
- Rychlé informace
- Ladění/zarážky
- Najít všechny odkazy
- Přejít k definici
- Hledání symbolu (Ctrl + T)
- Zvýraznění odkazů
- Diagnostika/chyby/podtržení vlnovkou.

![C&#43; &#43; živé ladění sdílenou složku](../ide/media/live-share-debug-cpp.png "živé ladění sdílené složkyC++")

## <a name="start-and-end-a-live-share-session"></a>Spuštění a ukončení relace Live Share

Pro spuštění relace Live Share v sadě Visual Studio, klikněte na tlačítko sdílet v pravé horní části nebo přejděte na **souboru** > **Start Session spolupráci**. Tím se vygeneruje odkaz, který můžete sdílet s vaší spolupracovníky.

![C&#43; &#43; Live tlačítko Sdílet](../ide/media/live-share-button-cpp.png "Live tlačítko sdílet")

Chcete-li ukončit relaci, vyberte **ukončit relaci spolupráci** z **sdílení** rozevíracího seznamu.

![C&#43; &#43; Live tlačítko Sdílet](../ide/media/live-share-end-session-cpp.png "Live tlačítko sdílet")

## <a name="for-more-information"></a>Další informace

Další informace o **Live Share** v sadě Visual Studio, naleznete v tématu [co je Visual Studio Live Share?](/visualstudio/liveshare/). Další informace o Live Share v aplikaci Visual Studio Code najdete v tématu [ Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Viz také

[Upravit a Refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Procházet vaše C++ kódové základny v sadě Visual Studio](navigate-code-cpp.md)</br>
[Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>