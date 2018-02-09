---
title: "Podpora znakové sady MBCS v jazyku Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92d0b737c0cfb894f87da61519f30224f6a12fc1
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="mbcs-support-in-visual-c"></a>Podpora znakové sady MBCS v jazyku Visual C++
Při spuštění na znakovou sadou MBCS verzi Windows, vývoj systému Visual C++ (včetně nástroje editor, příkazový řádek a ladicí program integrované zdrojový kód) se znakovou sadou MBCS, s výjimkou paměť – okno.  
  
 Okna paměti neinterpretuje bajtů dat jako znaky znakové sady MBCS, i když je lze interpretovat jako znaky ANSI nebo Unicode. ANSI znaky jsou vždy 1 bajt a znaky znakové sady Unicode mají velikost 2 bajtů. Se znakovou sadou MBCS znaků může být 1 nebo 2 bajty velikost a jejich interpretace závisí na znakovou stránku, která se používá. Z toho důvodu je pro okno paměti spolehlivě zobrazit znaky znakové sady MBCS. Okna paměti nemůže vědět, který bajt je spuštění znaku. Vývojář můžete zobrazit hodnoty bajtů v okně paměti a vyhledat hodnotu v tabulkách určení reprezentace znaku. To je možné, protože vývojář zná počáteční adresa řetězec v závislosti na zdrojový kód.  
  
 Visual C++ přijme dvoubajtové znaky, kdykoli je to vhodné. To zahrnuje cesty a názvy souborů v dialogových oknech a text položky v editoru Visual C++ prostředků (například statický text v editoru dialogového okna) a statický text položky v editoru ikonu. Kromě toho preprocesor rozpoznává některé dvojbajtové direktivy – například názvy souborů v `#include` příkazy a jako argumenty pro **code_seg** a **data_seg** direktivy. V editoru zdrojového kódu je v komentáře a textové literály dvoubajtové znaky jsou přijata, i když není v elementy jazyka C/C++ (například názvy proměnných).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Podpora pro vstup metoda Editor IME  
 Aplikace napsané pro východoasijské trhy, které normálně ho používat MBCS (například Japonsko) podporují Windows editoru IME pro zadání obou jedním a dvoubajtové znaky. Vývojové prostředí Visual C++ obsahuje plnou podporu pro Editor IME. Další informace najdete v tématu [Ukázka IME: ukazuje, jak režim editoru IME kontroly a implementace editoru IME úroveň 3](http://msdn.microsoft.com/en-us/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Japonské klávesnice přímo nepodporují znaků Kanji. Editor IME převede výslovnosti řetězec zadaný v jednom z jiných japonských abeced (Romaji, Katakana nebo Hiragana) do jeho možné reprezentace Kanji. Pokud je nejednoznačnosti, můžete vybrat z několika alternativ. Pokud jste vybrali zamýšlený znak Kanji, editor IME předá dvě `WM_CHAR` zprávy řídící aplikaci.  
  
 Editor IME, aktivovaný ALT +\` kombinace klíče, se zobrazí jako sadu tlačítek (indikátor) a okno převodu. Aplikace se umístí okno na textový kurzor. Aplikace musí zpracovat `WM_MOVE` a `WM_SIZE` zprávy pomocí přemístění okna převodu tak, aby odpovídala nové umístění nebo velikost cílové okno.  
  
 Pokud chcete uživatelům vaší aplikace do mají možnost zadejte znaků Kanji, aplikace musí zpracovat zprávy editoru IME systému Windows. Další informace o programování IME najdete v tématu [Editor IME](https://msdn.microsoft.com/en-us/library/ms776145.aspx).  
  
## <a name="visual-c-debugger"></a>Ladicí program Visual C++  
 Ladicí program Visual C++ poskytuje možnost nastavit zarážky na zprávy editoru IME. Kromě toho můžete paměť – okno zobrazit dvoubajtové znaky.  
  
## <a name="command-line-tools"></a>Nástroje příkazového řádku  
 Nástroje příkazového řádku Visual C++, včetně kompilátoru, NMAKE a kompilátor prostředků (RC. Soubor EXE), se znakovou sadou MBCS. /C – možnost kompilátoru prostředků můžete změnit výchozí znakovou stránku, když kompilujete zdrojů vaší aplikace.  
  
 Chcete-li změnit výchozí národní prostředí v době kompilace zdrojového kódu, použijte [#pragma setlocale](../preprocessor/setlocale.md).  
  
## <a name="graphical-tools"></a>Nástroje s grafickým rozhraním  
 Nástroje systému Visual C++ Windows, například nástroje Spy ++ a prostředků, nástroje pro, úpravy, plně podporovat editoru IME řetězce.  
  
## <a name="see-also"></a>Viz také  
 [Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)