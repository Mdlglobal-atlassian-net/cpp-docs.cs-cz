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
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375783"
---
# <a name="mbcs-support-in-visual-c"></a>Podpora znakové sady MBCS v jazyku Visual C++

Při spuštění v mbcs s podporou verze systému Windows, Visual C++ vývojový systém (včetně integrovaného editoru zdrojového kódu, ladicí program a nástroje příkazového řádku) je mbcs povoleno, s výjimkou okna paměti.

Okno paměti neinterpretuje bajty dat jako znaky MBCS, přestože je může interpretovat jako znaky ANSI nebo Unicode. Znaky ANSI mají vždy velikost 1 bajt a znaky Unicode mají velikost 2 bajty. S MBCS znaky mohou být 1 nebo 2 bajty ve velikosti a jejich interpretace závisí na tom, která znaková stránka je používán. Z tohoto důvodu je obtížné pro okno paměti spolehlivě zobrazit znaky MBCS. Okno paměti nemůže vědět, který bajt je začátek znaku. Vývojář může zobrazit hodnoty bajtů v okně paměti a vyhledat hodnotu v tabulkách k určení reprezentace znaků. To je možné, protože vývojář zná počáteční adresu řetězce na základě zdrojového kódu.

Visual C++ přijímá dvoubajtové znaky všude tam, kde je to vhodné. To zahrnuje názvy cest a názvů souborů v dialogových polích a textové položky v editoru prostředků Visual C++ (například statický text v editoru dialogů a statické textové položky v editoru ikon). Kromě toho preprocesor rozpozná některé dvoubajtové direktivy `#include` – například názvy `code_seg` souborů `data_seg` v příkazech a jako argumenty pro a pragmas. V editoru zdrojového kódu jsou přijímány dvoubajtové znaky v komentářích a řetězcových literálech, i když ne v elementech jazyka C/C++ (například názvy proměnných).

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Podpora editoru IME (IME)

Aplikace napsané pro východoasijské trhy, které používají mbcs (například Japonsko) obvykle podporují ime Windows IME pro zadávání jednobajtových i dvoubajtových znaků. Vývojové prostředí Visual C++ obsahuje plnou podporu pro ime.

Japonské klávesnice přímo nepodporují znaky Kanji. IME převede fonetický řetězec zadaný v jedné z dalších japonských abeced (Romaji, Katakana nebo Hiragana) na jeho možné reprezentace Kanji. Pokud je nejednoznačnost, můžete si vybrat z několika alternativ. Pokud jste vybrali zamýšlený znak Kanji, ime předá dvě `WM_CHAR` zprávy řídící aplikaci.

IME, aktivovaný kombinací\` kláves ALT+, se zobrazí jako sada tlačítek (indikátor) a konverzního okna. Aplikace umístí okno v textovém kurzoru. Aplikace musí `WM_MOVE` zpracovávat a `WM_SIZE` zprávy přemístěním okna převodu tak, aby odpovídalo novému umístění nebo velikosti cílového okna.

Pokud chcete, aby uživatelé vaší aplikace měli možnost zadávat znaky Kanji, musí aplikace zpracovávat zprávy ime systému Windows. Další informace o programování editoru IME naleznete [ve Správci vstupů](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Ladicí program Visual C++

Ladicí program Visual C++ umožňuje nastavit zarážky u zpráv IME. Kromě toho může okno Paměť zobrazit dvoubajtové znaky.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

Nástroje příkazového řádku Visual C++, včetně kompilátoru, NMAKE a kompilátoru prostředků (RC. EXE), jsou mbcs-enabled. Můžete použít kompilátor prostředků /c možnost změnit výchozí znakovou stránku při kompilaci prostředků aplikace.

Chcete-li změnit výchozí národní prostředí v době kompilace zdrojového kódu, použijte [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Grafické nástroje

Nástroje visual C++ pro Windows, jako je Spy++ a nástroje pro úpravy prostředků, plně podporují řetězce editoru IME.

## <a name="see-also"></a>Viz také

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)
