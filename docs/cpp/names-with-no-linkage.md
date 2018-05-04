---
title: Názvy bez propojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], parameters
- typedef names, linkage
- enumerators [C++], linkage
- names [C++], with no linkage
- function parameters [C++]
ms.assetid: 7174c500-12d2-4572-8c16-63c27c758fb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfb37c8fd694c10707efed8bae7ca0e08afdcf41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="names-with-no-linkage"></a>Názvy bez propojení
Jediné názvy, které nemají žádné propojení, jsou:  
  
-   parametry funkce,  
  
-   Obor bloku názvy není deklarován jako `extern` nebo **statické**.  
  
-   enumerátory,  
  
-   názvy deklarované v příkazu `typedef`. Výjimkou je, když je příkaz `typedef` použit k poskytnutí názvu pro nepojmenovaný typ třídy. Název pak může mít vnější propojení, pokud má třída vnější propojení. Následující příklad ukazuje situaci, ve které má název `typedef` vnější propojení:  
  
    ```  
    // names_with_no_linkage.cpp  
    typedef struct  
    {  
       short x;  
       short y;  
    } POINT;  
  
    extern int MoveTo( POINT pt );  
  
    int main()  
    {  
    }  
    ```  
  
     Název `typedef`, `POINT`, se stane názvem třídy pro nepojmenovanou strukturu. Poté je použit k deklarování funkce s vnějším propojením.  
  
 Vzhledem k tomu, že název `typedef` nemá žádné propojení, jejich definice se mezi jednotkami překladu mohou lišit. Vzhledem k tomu, že se kompilace provádí samostatně, neexistuje způsob, jakým by kompilátor zjistil tyto rozdíly. V důsledku toho nejsou chyby tohoto druhu zjištěny do doby propojení. Zvažte následující případ:  
  
```  
// Translation unit 1  
typedef int INT  
  
INT myInt;  
...  
  
// Translation unit 2  
typedef short INT  
  
extern INT myInt;  
...  
```  
  
 Předcházející kód vygeneruje v době spojení chybu „nevyřešené externí“.  
  
## <a name="example"></a>Příklad  
 Funkce jazyka C++ lze definovat pouze v oboru souboru nebo třídy. Následující příklad ukazuje způsob definice funkcí a ukazuje chybnou definici funkce:  
  
```  
// function_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void ShowChar( char ch );    // Declare function ShowChar.  
  
void ShowChar( char ch )     // Define function ShowChar.  
{                            // Function has file scope.  
   cout << ch;  
}  
  
struct Char                  // Define class Char.  
{  
    char Show();             // Declare Show function.  
    char Get();              // Declare Get function.  
    char ch;  
};  
  
char Char::Show()            // Define Show function  
{                            //  with class scope.  
    cout << ch;  
    return ch;  
}  
  
void GoodFuncDef( char ch )  // Define GoodFuncDef  
{                            //  with file scope.  
    int BadFuncDef( int i )  // C2601, Erroneous attempt to  
    {                        //  nest functions.  
        return i * 7;  
    }  
    for( int i = 0; i < BadFuncDef( 2 ); ++i )  
        cout << ch;  
    cout << "\n";  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Program a propojení](../cpp/program-and-linkage-cpp.md)