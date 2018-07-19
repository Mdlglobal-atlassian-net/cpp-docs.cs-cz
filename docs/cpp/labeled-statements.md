---
title: Příkazy s popiskem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54eb2757f4f58acd0339a058c8bee999b4c8b7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947490"
---
# <a name="labeled-statements"></a>Příkaz s popiskem
Popisky lze převést řízení programu přímo na zadaný příkaz.  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 Rozsah popisku je celou funkci, ve kterém je deklarována.  
  
## <a name="remarks"></a>Poznámky  
 Existují tři typy příkazů s popisky. Všechny používají k oddělení nějakého typu popisku od příkazu dvojtečku. Popisky case a default jsou specifické pro příkazy case.  
  
```cpp  
#include <iostream>   
using namespace std;   
  
void test_label(int x) {  
  
    if (x == 1){  
        goto label1;  
    }  
    goto label2;  
  
label1:  
    cout << "in label1" << endl;  
    return;  
  
label2:  
    cout << "in label2" << endl;  
    return;  
}  
  
int main() {  
    test_label(1);  // in label1   
    test_label(2);  // in label2  
}  
  
```  
  
 **Goto – příkaz**  
  
 Vzhled *identifikátor* popisek ve zdrojovém programu deklaruje popisek. Pouze [goto](../cpp/goto-statement-cpp.md) příkaz může přenést řízení k *identifikátor* popisek. Následující fragment kódu ukazuje použití **goto** příkazu a *identifikátor* popisku:  
  
 Popisek se nemůže objevit samostatně, ale musí být vždy připojen k příkazu. Pokud je potřebný samotný popisek, umístěte za tento popisek příkaz null.  
  
 Popisek má rozsah funkce a v rámci této funkce jej nelze opětovně deklarovat. Stejný název lze však použít jako popisek v jiných funkcích.  
  
```cpp 
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
}  
  
//Output: At Test2 label.  
```  
  
 **Case – příkaz**  
  
 Popisky, které se zobrazí po **případ** – klíčové slovo nemohou zobrazit také mimo **přepnout** příkazu. (Toto omezení platí také pro **výchozí** – klíčové slovo.) Následující fragment kódu ukazuje správné použití **případ** popisků:  
  
```cpp 
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );   
      EndPaint( hWnd, &ps );  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-case-statement"></a>Popisky case – příkaz  
 Popisky, které se zobrazí po **případ** – klíčové slovo nemohou zobrazit také mimo **přepnout** příkazu. (Toto omezení platí také pro **výchozí** – klíčové slovo.) Následující fragment kódu ukazuje správné použití **případ** popisků:  
  
```cpp 
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      // Obtain a handle to the device context.  
      // BeginPaint will send WM_ERASEBKGND if appropriate.  
  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );  
  
      // Inform Windows that painting is complete.  
  
      EndPaint( hWnd, &ps );  
      break;  
  
   case WM_CLOSE:  
      // Close this window and all child windows.  
  
      KillTimer( hWnd, TIMER1 );  
      DestroyWindow( hWnd );  
      if ( hWnd == hWndMain )  
         PostQuitMessage( 0 );  // Quit the application.  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-goto-statement"></a>Popisků v příkazu goto  
 Vzhled *identifikátor* popisek ve zdrojovém programu deklaruje popisek. Pouze [goto](../cpp/goto-statement-cpp.md) příkaz může přenést řízení k *identifikátor* popisek. Následující fragment kódu ukazuje použití **goto** příkazu a *identifikátor* popisku:  
  
 Popisek se nemůže objevit samostatně, ale musí být vždy připojen k příkazu. Pokud je potřebný samotný popisek, umístěte za tento popisek příkaz null.  
  
 Popisek má rozsah funkce a v rámci této funkce jej nelze opětovně deklarovat. Stejný název lze však použít jako popisek v jiných funkcích.  
  
```cpp 
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
// At Test2 label.  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)   
 [switch – příkaz (C++)](../cpp/switch-statement-cpp.md)