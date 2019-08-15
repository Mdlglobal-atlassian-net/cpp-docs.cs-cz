---
title: Podpora použití funkce wmain
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491200"
---
# <a name="support-for-using-wmain"></a>Podpora použití funkce wmain

Vizuál C++ podporuje definování funkce **wmain** a předání argumentů pro velké znaky do vaší aplikace pro kódování Unicode. Dodáte deklarace formálních parametrů na **wmain**pomocí formátu podobného `main`. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. Parametry `argv` a `envp` pro **wmain** jsou typu `wchar_t*`. Příklad:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Aplikace MFC Unicode používají `wWinMain` jako vstupní bod. V tomto případě `CWinApp::m_lpCmdLine` je to řetězec Unicode. Nezapomeňte nastavit `wWinMainCRTStartup` pomocí možnosti linkeru [/entry](../build/reference/entry-entry-point-symbol.md) .

Používá-li program funkci **Main** , je prostředí vícebajtového znaku vytvořeno při spuštění programu v běhové knihovně. Kopie prostředí s velkým počtem znaků je vytvořena pouze v případě potřeby (například voláním `_wgetenv` funkce nebo `_wputenv` ). Při prvním volání `_wputenv`nebo při prvním `_wgetenv` volání, pokud již existuje prostředí znakové sady MBCS, je vytvořeno odpovídající prostředí řetězce s velkým znakem. Prostředí je pak odkazováno pomocí `_wenviron` globální proměnné, což je verze celosvětové proměnné v `_environ` celém znaku. V tomto okamžiku existují dvě kopie prostředí (MBCS a Unicode) současně a jsou udržovány systémem za běhu po celou dobu životnosti programu.

Podobně platí, že pokud váš program používá funkci **wmain** , prostředí s velkým znakem se vytvoří při spuštění programu a ukazuje na `_wenviron` globální proměnnou. Prostředí znakové sady MBCS (ASCII) je vytvořeno při prvním volání `_putenv` nebo `getenv` a `_environ` ukazuje na globální proměnnou.

## <a name="see-also"></a>Viz také:

[Podpora pro Unicode](../text/support-for-unicode.md)<br/>
[Souhrn programování s kódem Unicode](../text/unicode-programming-summary.md)<br/>
[WinMain – funkce](/windows/win32/api/winbase/nf-winbase-winmain)
