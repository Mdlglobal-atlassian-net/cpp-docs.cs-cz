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
ms.openlocfilehash: 4ef970174a56361fdbd2102f363b4849ad4af9f3
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894182"
---
# <a name="support-for-using-wmain"></a>Podpora použití funkce wmain

Jazyk Visual C++ podporuje definování **wmain** funkce a předávání argumentů širokého znaku Unicode aplikace. Deklarovat formální parametry **wmain**, pomocí ve formátu podobném `main`. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. `argv` a `envp` parametry **wmain** jsou typu `wchar_t*`. Příklad:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Použití aplikace knihovny MFC kódování Unicode `wWinMain` jako vstupní bod. V takovém případě `CWinApp::m_lpCmdLine` je řetězec znaků Unicode. Nezapomeňte nastavit `wWinMainCRTStartup` s [/Entry](../build/reference/entry-entry-point-symbol.md) – možnost linkeru.

Pokud program používá **hlavní** funkce, vytvoří prostředí vícebajtových znaků knihovny run-time při spuštění programu. Kopie širokého znaku prostředí je vytvořen pouze v případě potřeby (například voláním `_wgetenv` nebo `_wputenv` funkce). Při prvním volání `_wputenv`, nebo při prvním volání `_wgetenv` Pokud prostředí MBCS už existuje, vytvoří se odpovídající prostředí řetězce širokého znaku. Prostředí je následně odkázáno pomocí `_wenviron` globální proměnné, což je verze širokého znaku z `_environ` globální proměnné. Dvě kopie prostředí (znaková sada MBCS a Unicode) v tomto okamžiku existovat současně a spravuje za běhu systému po celou dobu životnosti programu.

Podobně pokud program používá **wmain** funkce, širokého znaku prostředí je vytvořen při spuštění programu a odkazuje `_wenviron` globální proměnné. Prostředí MBCS (ASCII) se vytvoří při prvním volání `_putenv` nebo `getenv` a odkazuje `_environ` globální proměnné.

## <a name="see-also"></a>Viz také

[Podpora pro Unicode](../text/support-for-unicode.md)<br/>
[Souhrn programování s kódem Unicode](../text/unicode-programming-summary.md)<br/>
[Funkce WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)