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
ms.openlocfilehash: aebd4800ad8d653d532708784ef0a5333211d46b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857655"
---
# <a name="argument-definitions"></a>Definice argumentů

Argumenty v prototypu

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

umožňují pohodlnou analýzu argumentů příkazového řádku a v případě potřeby přístup k proměnným prostředí. Definice argumentů jsou následující:

*argc*<br/>
Celé číslo, které obsahuje počet argumentů, které následují v *argv*. Parametr *argc* je vždycky větší nebo roven 1.

*argv*<br/>
Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` je příkaz, se kterým se program vyvolá, `argv[1]` je první argument příkazového řádku a tak dále, dokud `argv[argc]`, což je vždycky NULL. Informace o potlačení zpracování příkazového řádku naleznete v tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) .

První argument příkazového řádku je vždycky `argv[1]` a poslední z nich je `argv[argc - 1]`.

> [!NOTE]
> Podle konvence `argv[0]` je příkaz, se kterým se program vyvolá.  Je ale možné vytvořit proces pomocí funkce [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) a pokud použijete první i druhý argument (*lpApplicationName* a *lpCommandLine*) `argv[0]`, nesmí být název spustitelného souboru. pomocí [GetModuleFileName –](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) načtěte název spustitelného souboru a jeho plně kvalifikovanou cestu.

**Specifické pro společnost Microsoft**

*envp*<br/>
Pole *envp* , což je společné rozšíření v mnoha systémech UNIX, se používá v Microsoftu C++. Je to pole řetězců, které představují proměnné nastavené v uživatelském prostředí. Toto pole je ukončeno prvkem NULL. Dá se deklarovat jako pole ukazatelů na **char** (`char *envp[]`) nebo jako ukazatel na ukazatele na **char** (`char **envp`). Pokud program používá `wmain` místo `main`, použijte **wchar_t** datový typ místo **char**. Blok prostředí předaný `main` a `wmain` je "zmrazená" kopie aktuálního prostředí. Pokud následně změníte prostředí prostřednictvím volání `putenv` nebo `_wputenv`, bude se změnit aktuální prostředí (vrácené `getenv` nebo `_wgetenv` a proměnná `_environ` nebo `_wenviron`), ale blok, na který envp odkazuje, se nezmění. Informace o potlačení zpracování prostředí naleznete v tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) . Tento argument je kompatibilní se standardem ANSI v jazyce C, ale ne v jazyce C++.

**Specifické pro konec Microsoftu**

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít argumenty *argc*, *argv*a *envp* k `main`:

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