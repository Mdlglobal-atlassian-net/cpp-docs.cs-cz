---
title: Používání příkazů exit nebo return
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
ms.openlocfilehash: d60084c0d07d3eeb3f49a1fea53de04d150a701b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152719"
---
# <a name="using-exit-or-return"></a>Používání příkazů exit nebo return

Při volání **ukončit** nebo spuštění **vrátit** příkaz z `main`, statické objekty jsou zničeny v obráceném pořadí jejich inicializace. Následující příklad ukazuje, jak taková inicializace a vyčištění funguje.

## <a name="example"></a>Příklad

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

V předchozím příkladu jsou vytvořeny a inicializovány statické objekty `sd1` a `sd2` před vstupem do funkce `main`. Poté, co program ukončen pomocí **vrátit** prohlášení, první `sd2` zničen a potom `sd1`. Destruktor třídy `ShowData` zavře soubory přidružené k těmto statickým objektům.

Jiný způsob psaní tohoto kódu je deklarace objektů `ShowData` s rozsahem bloku, čímž je umožněno jejich zničení, dostanou-li se mimo rozsah:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Viz také:

[Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)