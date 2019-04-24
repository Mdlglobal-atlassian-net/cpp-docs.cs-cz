---
title: Definice argumentů
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: 92e213b5accbf8fd5f48ac2111a169e585d82a1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184438"
---
# <a name="argument-definitions"></a>Definice argumentů

Argumenty v prototypu

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

umožňují pohodlnou analýzu argumentů příkazového řádku a v případě potřeby přístup k proměnným prostředí. Definice argumentů jsou následující:

*argc*<br/>
Celé číslo obsahující počet argumentů, které následují v *argv*. *Argc* parametr je vždy větší nebo rovna 1.

*argv*<br/>
Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` příkaz, kterým je program vyvolán, `argv[1]` je první argument příkazového řádku a tak dále, dokud `argv[argc]`, což je vždy hodnotu NULL. Zobrazit [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) Další informace o potlačení zpracování příkazového řádku.

První argument příkazového řádku je vždy `argv[1]` a poslední je `argv[argc - 1]`.

> [!NOTE]
> Podle konvence `argv[0]` příkaz, kterým je vyvolán program.  Nicméně je možné vytvořit podřízený proces pomocí [CreateProcess](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) a pokud používáte první a druhý argument (*lpApplicationName* a *lpCommandLine*), `argv[0]` nemusí být název spustitelného souboru; použít [GetModuleFileName –](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) k načtení názvu spustitelného souboru a jeho plně kvalifikovanou cestu.

## <a name="microsoft-specific"></a>Specifické pro Microsoft

*envp*<br/>
*Envp* pole, které je běžným rozšířením mnoha systémů UNIX, se používá v Microsoft C++. Je to pole řetězců, které představují proměnné nastavené v uživatelském prostředí. Toto pole je ukončeno prvkem položku NULL. Mohou být deklarovány jako pole ukazatelů na **char** (`char *envp[]`) nebo jako ukazatel na ukazatele na **char** (`char **envp`). Pokud program používá `wmain` místo `main`, použijte **wchar_t** datový typ místo **char**. Blok prostředí předaný `main` a `wmain` je "zmrazená" kopie aktuálního prostředí. Pokud později změníte prostředí prostřednictvím volání `putenv` nebo `_wputenv`, aktuální prostředí (vrácené `getenv` nebo `_wgetenv` a `_environ` nebo `_wenviron` proměnná) se změní, ale blok odkazovaný parametrem envp se nezmění. Zobrazit [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) Další informace o potlačení zpracování prostředí. Tento argument je kompatibilní se standardem ANSI v jazyce C, ale ne v jazyce C++.

**Specifické pro END Microsoft**

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití *argc*, *argv*, a *envp* argumenty `main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)