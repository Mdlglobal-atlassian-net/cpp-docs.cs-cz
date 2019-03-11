---
title: Podpora znakové sady MBCS v jazyku Visual C++
ms.date: 11/04/2016
f1_keywords:
- _mbcs
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
ms.openlocfilehash: b292bb12888ce0c08f96d3c46e27297f61bc428d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750491"
---
# <a name="mbcs-support-in-visual-c"></a>Podpora znakové sady MBCS v jazyku Visual C++

Při spuštění na znakovou sadou MBCS verzi Windows, vývojový systém Visual C++ (včetně nástroje integrovaného zdrojového kódu editoru, ladicího programu a příkazového řádku) se znakovou sadou MBCS, s výjimkou okna paměť.

Okno paměti neinterpretuje bajtů dat jako znaky znakové sady MBCS, i v případě, že je lze interpretovat jako ANSI nebo Unicode znaky. ANSI znaky jsou vždy 1 bajt a znaky znakové sady Unicode jsou 2 bajty. Pomocí znakové sady MBCS znaky mohou být 1 nebo 2 bajty a jejich interpretaci závisí na znakovou stránku, která se používá. Z toho důvodu je obtížné pro okna paměti a spolehlivě zobrazí znaky znakové sady MBCS. Okno paměti nemůže vědět, jaké bajt je počáteční znak. Vývojář můžete zobrazit bajtové hodnoty v okně paměť a vyhledat hodnotu v tabulkách k určení reprezentace znaku. To je možné, protože vývojář zná počáteční adresu řetězce na základě zdrojového kódu.

Visual C++ přijímá dvoubajtové znaky, kdykoli je to vhodné. To zahrnuje cesty a názvy souborů v dialogových oknech a textu položky v editoru prostředků Visual C++ (například statický text v editoru dialogového okna) a položky statický text v editoru ikon. Kromě toho preprocesor rozpoznává některé direktivy dvoubajtové – například názvy souborů v `#include` příkazy a jako argumenty, které mají `code_seg` a `data_seg` direktivy pragma. V editoru zdrojového kódu je dvoubajtové znaky v komentáři a řetězcové literály jsou přijata, i když není v elementy jazyka C/C++ (například názvy proměnných).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> Podpora pro Input Method Editor (IME)

Aplikace napsané pro východoasijské trhy, které používají znakovou sadu MBCS (například Japonsko) obvykle podporu Windows editoru IME pro zadání obou jednou a dvoubajtové znaky. Vývojové prostředí Visual C++ obsahuje plnou podporu pro Editor IME.

Japonské klávesnice přímo nepodporují znaků Kanji. Editor IME převede řetězec zapsané ve fonetické, zadat v jednom z jiných japonské abecedy (Romaji, Katakana nebo Hiragana) do jeho možné reprezentace Kanji. Pokud existuje nejednoznačnost, můžete vybrat z několika alternativ. Po výběru zamýšlený znaků Kanji Editor IME předá dva `WM_CHAR` zprávy k řídicí aplikaci.

Editor IME aktivoval ALT +\` kombinace kláves, se zobrazí jako sadu tlačítek (indikátor) a okno převodu. Aplikace se umístí v kurzor textového okna. Aplikace musí zpracovat `WM_MOVE` a `WM_SIZE` zprávy podle přemístění okna převodu tak, aby odpovídal na nové umístění nebo velikost cílového okna.

Pokud chcete uživatelům umožnit zadávání znaků Kanji vaší aplikace, aplikace musí zpracovat zprávy Windows editoru IME. Další informace o programování v editoru IME, naleznete v tématu [vstupní metody správce](/windows/desktop/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Ladicí program Visual C++

Ladicí program Visual C++ poskytuje možnost nastavit zarážky u zpráv s IME. Okno paměti můžete navíc zobrazit dvoubajtové znaky.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

Nástroje příkazového řádku jazyka Visual C++, včetně kompilátor NMAKE a kompilátor prostředků (RC. Soubor EXE), jsou povolené znakové sady MBCS. /C – možnost kompilátoru prostředku můžete změnit výchozí znaková stránka při kompilaci zdrojů vaší aplikace.

Chcete-li změnit výchozí národní prostředí v době kompilace zdrojového kódu, použijte [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Grafické nástroje

Nástroje založené na Windows Visual C++, například nástroje Spy ++ a prostředků, nástroje, pro úpravy plně podporují řetězce editoru IME.

## <a name="see-also"></a>Viz také:

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)
