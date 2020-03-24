---
title: Upozornění linkerů LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1ce410312493b353bb68ea7264fce9cd6a394e0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183108"
---
# <a name="linker-tools-warning-lnk4217"></a>Upozornění linkerů LNK4217

> symbol '*symbol*' definovaný v '*filename_1. obj*' je importován '*filename_2. obj*' ve funkci '*Function*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro symbol, i když je symbol definován v souboru objektu ve stejné imagi. Odeberte modifikátor `__declspec(dllimport)` pro vyřešení tohoto upozornění.

## <a name="remarks"></a>Poznámky

*symbol* je název symbolu, který je definován v rámci obrázku. *funkce* je funkce, která importuje symbol.

Toto upozornění se nezobrazí při kompilaci pomocí možnosti [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

K LINKERŮ LNK4217 může také dojít, pokud se pokusíte propojit dva moduly dohromady, pokud místo toho byste měli zkompilovat druhý modul s knihovnou importu prvního modulu.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

a potom

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

Při pokusu o zkompilování těchto dvou modulů se zobrazí LINKERŮ LNK4217:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

Chcete-li chybu opravit, po zkompilování dvou souborů předejte TT. obj do knihovny LIB. exe a vytvořte soubor. lib a pak propojte Main. obj pomocí souboru TT. lib, jak je znázorněno zde:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>Viz také

[Linkerů lnk4049 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4049.md)
[LNK4286 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4286.md)
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
