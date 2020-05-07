---
title: Volání funkcí knihovny DLL z aplikací jazyka Visual Basic
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221193"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Volání funkcí knihovny DLL z aplikací jazyka Visual Basic

Pro aplikace Visual Basic (nebo aplikací v jiných jazycích, jako je Pascal nebo FORTRAN) volání funkcí v knihovně DLL jazyka C/C++, je nutné tyto funkce exportovat pomocí správné konvence volání bez jakýchkoli názvů, které provádí kompilátor.

`__stdcall`Vytvoří správnou konvenci volání funkce (volaná funkce vyčistí zásobník a parametry jsou předány zprava doleva), ale upraví název funkce odlišně. Takže při použití **__declspec (dllexport)** pro exportovanou funkci v knihovně DLL, je upravený název exportován.

Dekorování `__stdcall` názvů má předponu názvu symbolu podtržítkem ( **\_** ) a připojí symbol pomocí znaku ' symbol ' (**\@**) následovaný počtem bajtů v seznamu argumentů (požadované místo v zásobníku). V důsledku toho je funkce deklarována jako:

```C
int __stdcall func (int a, double b)
```

je upraven jako `_func@12` ve výstupu.

Konvence volání jazyka C`__cdecl`() upraví název jako `_func`.

Chcete-li získat dekorovaný název, použijte [/map](reference/map-generate-mapfile.md). Použití **__declspec (dllexport)** provede následující:

- Pokud je funkce exportována pomocí konvence volání jazyka C`__cdecl`(), obchází úvodní podtržítko ( **\_** ), pokud je název exportován.

- Pokud funkce, která je exportována, nepoužívá konvenci volání jazyka C ( `__stdcall`například), exportuje upravený název.

Vzhledem k tomu, že neexistuje žádný způsob, jak přepsat, kde dojde k vyčištění `__stdcall`zásobníku, je nutné použít. Chcete-li Neupravovat názvy pomocí `__stdcall`, je nutné je zadat pomocí aliasů v části EXPORTS v souboru. def. To je znázorněno následovně pro následující deklaraci funkce:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

V. DEF soubor:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Aby byly knihovny DLL volány programy napsanými v Visual Basic, je v souboru. def nutná metoda aliasů uvedená v tomto tématu. Pokud se alias provádí v Visual Basic programu, není nutné použít aliasing v souboru. def. Lze ji provést v programu Visual Basic přidáním klauzule alias do příkazu [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) .

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Export z knihovny DLL](exporting-from-a-dll.md)

- [Export z knihovny DLL pomocí. Soubory DEF](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Dekorované názvy](reference/decorated-names.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
