---
title: "Definice argumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd1bc4f017a90bf2f42972831eadc02e77868151
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="argument-definitions"></a>Definice argumentů
Argumenty v prototypu  
  
```  
  
int main( int  
argc[ ,char*argv[] [,char*envp[] ] ] );intwmain(intargc[ ,wchar_t*argv[] [,wchar_t*envp[] ] ] );  
```  
  
 umožňují pohodlnou analýzu argumentů příkazového řádku a v případě potřeby přístup k proměnným prostředí. Definice argumentů jsou následující:  
  
 `argc`  
 Celé číslo obsahující počet argumentů, které následují v parametru `argv`. Parametr `argc` je vždy větší nebo roven 1.  
  
 `argv`  
 Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv` **[0]** je příkaz, se kterým program vyvolání `argv` **[1]** je první argument příkazového řádku a tak dále, dokud `argv`  **[**`argc`**]**, který je vždycky **NULL**. V tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) informace o potlačení zpracování příkazového řádku.  
  
 První argument příkazového řádku je vždy `argv` **[1]** a je poslední `argv` **[** `argc` – 1**]**.  
  
> [!NOTE]
>  Podle konvence `argv` **[0]** je příkaz, ke které je voláno program.  Je však možné vytvořit, využívá proces [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) a pokud používáte první a druhý argument (`lpApplicationName` a `lpCommandLine`), `argv` **[0]** nemusí být název spustitelného souboru; použít [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) načíst název spustitelného souboru a jeho plně kvalifikovanou cestu.  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `envp`  
 Pole `envp`, které je běžným rozšířením mnoha systémů UNIX, je používáno v jazyce C++ společnosti Microsoft. Je to pole řetězců, které představují proměnné nastavené v uživatelském prostředí. Toto pole je ukončena **NULL** položku. Může být deklarována jako pole ukazatele na **char (char** \*[] envp –**)** nebo jako ukazatel na ukazatele na **char (char** \* \* envp –**)**. Pokud váš program používá **wmain** místo **hlavní**, použijte `wchar_t` datový typ místo `char`. Blok prostředí předaný **hlavní** a **wmain** je "ukotvené" kopie aktuálního prostředí. Pokud později změníte prostředí prostřednictvím volání **putenv –** nebo `_wputenv`, aktuální prostředí (jak ho vrátila `getenv` / `_wgetenv` a `_environ` /  `_wenviron` proměnné) změny, ale blok ukazuje envp – se nezmění. V tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) informace o potlačení zpracování prostředí. Tento argument je kompatibilní se standardem ANSI v jazyce C, ale ne v jazyce C++.  
  
**Konkrétní Microsoft END**  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `argc`, `argv`, a `envp` argumenty, které mají **hlavní**:  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)