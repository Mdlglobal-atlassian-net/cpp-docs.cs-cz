---
title: Volání funkcí knihovny DLL z aplikací Visual Basic | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47504b7a471dc38f30e4ceb59b5feeffcc53db6d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161829"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Volání funkcí knihovny DLL z aplikací jazyka Visual Basic

Pro aplikace Visual Basic (nebo aplikace v jiných jazycích, jako například Pascal nebo Fortran) pro volání funkce v knihovně DLL jazyka C/C++ funkce musí být exportovány pomocí správné konvence volání bez jakékoli dekorování názvů kompilátorem

`__stdcall` Vytvoří správnou konvenci volání funkce (volaná funkce vyčistí zásobník a parametry jsou předány zprava doleva), ale název funkce upraví odlišně. Ano, v případě **__declspec(dllexport)** se používá na exportované funkce v knihovně DLL, upravený název je exportován.

`__stdcall` Dekorování názvů předpon název symbol podtržítka ( **\_** ) a připojí symbol zavináč (**\@**) následovaný počet počet bajtů v seznamu argumentů (požadované místo v zásobníku). V důsledku toho je funkce deklarovaná jako:

```C
int __stdcall func (int a, double b)
```

je upravena následovně `_func@12` ve výstupu.

Konvence volání jazyka C (`__cdecl`) upraví název jako `_func`.

Chcete-li získat upravený název, použijte [/MAP](../build/reference/map-generate-mapfile.md). Použití **__declspec(dllexport)** provede následující akce:

- Pokud se exportuje funkci s konvencí volání jazyka C (`__cdecl`), odstraní počáteční podtržítko ( **\_** ) při exportu názvu.

- Pokud je funkce exportována nepoužívá konvence volání jazyka C (například `__stdcall`), exportuje upravený název.

Protože neexistuje žádný způsob, jak přepsat, pokud dojde k vymazání zásobníku, je nutné použít `__stdcall`. Rušit úpravu názvu `__stdcall`, je nutné je zadat pomocí aliasů v oddíle EXPORTS v .def souboru. To je ukázáno následujícím způsobem pro následující deklarace funkce:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

V. Soubor DEF:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Knihovny DLL, být volány programy napsanými v jazyce Visual Basic vyžadují v souboru .def techniku "alias" v tomto tématu. Pokud se alias provede v programu Visual Basic, není nutné použití v .def souboru. To můžete udělat v aplikaci Visual Basic, tak, že přidáte klauzuli alias do [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) příkazu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Export z knihovny DLL](../build/exporting-from-a-dll.md)

- [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určení, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Dekorované názvy](../build/reference/decorated-names.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)
