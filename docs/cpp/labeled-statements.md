---
title: Příkaz s popiskem
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: d971a0e9864aeada1db5f004ef70577512e78c76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179689"
---
# <a name="labeled-statements"></a>Příkaz s popiskem

Popisky slouží k přenosu řízení programu přímo do zadaného příkazu.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

Rozsah popisku je celá funkce, ve které je deklarována.

## <a name="remarks"></a>Poznámky

Existují tři typy příkazů s popisky. Všechny používají k oddělení nějakého typu popisku od příkazu dvojtečku. Popisky case a Default jsou specifické pro příkazy Case.

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

**Příkaz goto**

Vzhled popisku *identifikátoru* ve zdrojovém programu deklaruje popisek. Pouze příkaz [goto](../cpp/goto-statement-cpp.md) může přenášet řízení na popisek *identifikátoru* . Následující fragment kódu ilustruje použití příkazu **goto** a popisku *identifikátoru* :

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

**Příkaz Case**

Popisky, které se zobrazí po klíčovém slově **case** , se nemohou objevit i vně příkazu **Switch** . (Toto omezení platí také pro klíčové slovo **Default** .) Následující fragment kódu ukazuje správné použití popisků **case** :

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

## <a name="labels-in-the-case-statement"></a>Popisky v příkazu case

Popisky, které se zobrazí po klíčovém slově **case** , se nemohou objevit i vně příkazu **Switch** . (Toto omezení platí také pro klíčové slovo **Default** .) Následující fragment kódu ukazuje správné použití popisků **case** :

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

## <a name="labels-in-the-goto-statement"></a>Popisky v příkazu goto

Vzhled popisku *identifikátoru* ve zdrojovém programu deklaruje popisek. Pouze příkaz [goto](../cpp/goto-statement-cpp.md) může přenášet řízení na popisek *identifikátoru* . Následující fragment kódu ilustruje použití příkazu **goto** a popisku *identifikátoru* :

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

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)<br/>
[switch – příkaz (C++)](../cpp/switch-statement-cpp.md)
