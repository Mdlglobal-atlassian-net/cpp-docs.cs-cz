---
title: Podpora znakové sady MBCS v jazyku Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501948"
---
# <a name="mbcs-support-in-visual-c"></a>Podpora znakové sady MBCS v jazyku Visual C++

Při spuštění ve verzi Windows s podporou znakové sady MBCS má Visual C++ Development systém (včetně editoru integrovaného zdrojového kódu, ladicího programu a nástrojů příkazového řádku) znakovou sadu MBCS s výjimkou okna paměti.

Okno paměti neinterpretuje bajty dat jako znaky znakové sady MBCS, a to i v případě, že je může interpretovat jako znaky ANSI nebo Unicode. Znaky ANSI mají velikost vždy 1 bajt a znaky Unicode mají velikost 2 bajty. Se znakovou sadou MBCS mohou mít znaky velikost 1 nebo 2 bajty a jejich interpretace závisí na tom, která znaková stránka je používána. Z tohoto důvodu je obtížné, aby okno paměti spolehlivě zobrazovalo znaky znakové sady MBCS. Okno paměti nemůže zjistit, který bajt je začátek znaku. Vývojář může zobrazit hodnoty bajtů v okně paměti a vyhledat hodnotu v tabulkách a zjistit reprezentace znaků. To je možné, protože vývojář zná počáteční adresu řetězce na základě zdrojového kódu.

Vizuál C++ přijímá dvoubajtové znaky, kdykoli je to vhodné. To zahrnuje názvy cest a názvů souborů v dialogových oknech a textových položkách v C++ editoru vizuálních prostředků (například statický text v editoru dialogového okna a statické textové položky v editoru ikon). Kromě toho preprocesor rozpoznává některé dvoubajtové směrnice – například názvy souborů v `#include` příkazech a jako argumenty `code_seg` direktiv pragma a `data_seg` . V editoru zdrojového kódu jsou dvoubajtové znaky v komentářích a řetězcové literály přijaty, i když nejsou v prvcích C/C++ jazyka (například názvy proměnných).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Podpora editoru IME (Input Method Editor)

Aplikace napsané pro východní asijské trhy, které používají znakovou sadu MBCS (například Japonsko), standardně podporují Windows IME pro zadávání jednoduchých i dvoubajtových znaků. Prostředí pro C++ vizuální vývoj obsahuje úplnou podporu pro Editor IME.

Japonské klávesnice nepodporují přímo znaky kanji. Editor IME převede fonetický řetězec zadaný v jedné z ostatních japonských abeced (Romaji, Katakana nebo Hiragana) do jeho možné reprezentace Kanji. Pokud dojde k nejednoznačnosti, můžete vybrat z několika alternativ. Pokud jste vybrali zamýšlený znak Kanji, editor IME předá do řídicí `WM_CHAR` aplikace dvě zprávy.

Editor IME aktivovaný kombinací kláves ALT +\` se zobrazí jako sada tlačítek (indikátor) a okno pro převod. Aplikace umístí okno na místo vložení textu. Aplikace musí zpracovat `WM_MOVE` a `WM_SIZE` zprávy přeumístěním okna převodu tak, aby odpovídalo novému umístění nebo velikosti cílového okna.

Pokud chcete, aby uživatelé vaší aplikace měli možnost zadat znaky kanji, musí aplikace zpracovat zprávy Windows IME. Další informace o programování IME naleznete v tématu [správce metod vstupu](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Vizuální C++ ladicí program

Vizuální C++ ladicí program poskytuje možnost nastavovat zarážky pro zprávy editoru IME. Kromě toho okno paměti může zobrazit dvoubajtové znaky.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

Nástroje příkazového řádku jazyka Visual C++ , včetně kompilátoru, NMAKE a kompilátoru prostředků (RC. EXE), jsou povoleny znakové sady MBCS. Pro změnu výchozí znakové stránky při kompilování prostředků vaší aplikace můžete použít možnost/c kompilátoru prostředků.

Chcete-li změnit výchozí národní prostředí v době kompilace zdrojového kódu, použijte [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Grafické nástroje

Nástroje pro C++ Visual v systému Windows, například Spy + + a nástroje pro úpravu prostředků, plně podporují řetězce editoru IME.

## <a name="see-also"></a>Viz také:

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)
