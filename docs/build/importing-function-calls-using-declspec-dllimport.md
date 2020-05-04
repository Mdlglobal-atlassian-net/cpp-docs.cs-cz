---
title: Import volání funkcí pomocí deklarace __declspec(dllimport)
description: Jak a proč použít __declspec (dllimport) při volání dat a funkcí knihovny DLL.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765718"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Import volání funkcí pomocí`__declspec(dllimport)`

Zadávání poznámek k **`__declspec(dllimport)`** voláním pomocí může být rychlejší. **`__declspec(dllimport)`** je vždy vyžadován pro přístup k exportovaným datům knihovny DLL.

## <a name="import-a-function-from-a-dll"></a>Import funkce z knihovny DLL

Následující příklad kódu ukazuje, jak použít **`__declspec(dllimport)`** pro import volání funkcí z knihovny DLL do aplikace. Předpokládejme, `func1` že je funkce, která je v knihovně DLL, oddělená od spustitelného souboru, který obsahuje funkci **Main** .

Bez **`__declspec(dllimport)`** daného kódu:

```C
int main(void)
{
   func1();
}
```

Kompilátor generuje kód, který vypadá takto:

```asm
call func1
```

a linker překládá volání do podobného:

```asm
call 0x4000000         ; The address of 'func1'.
```

Pokud `func1` existuje v jiné knihovně DLL, linker nemůže tuto adresu přeložit přímo, protože nemá žádný způsob, jak znát adresu `func1` . V 32 bitové a 64 prostředí linker generuje převod na známou adresu. V 32 bitovém prostředí může převod kódu vypadat jako:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Tady `__imp_func1` je adresa `func1` slotu v tabulce importovaná adresa spustitelného souboru. Všechny tyto adresy jsou známy linkeru. Zavaděč musí aktualizovat tabulku importovaných adres pro spustitelný soubor v době načítání, aby vše fungovalo správně.

To je důvod, **`__declspec(dllimport)`** proč použití je lepší: protože linker negeneruje převod na více, pokud není požadován. Převodní rutiny zvětšit kód (v systémech RISC může to být několik pokynů) a může snížit výkon mezipaměti. Pokud kompilátor říkáte, že je funkce v knihovně DLL, může pro vás vygenerovat nepřímou hovor.

Takže teď tento kód:

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

vygeneruje tuto instrukci:

```asm
call DWORD PTR __imp_func1
```

Není k dispozici žádný převod `jmp` ani žádná instrukce, takže kód je menší a rychlejší. Stejný efekt můžete také získat bez **`__declspec(dllimport)`** použití celé optimalizace programu. Další informace naleznete v tématu [/GL (celá optimalizace programu)](reference/gl-whole-program-optimization.md).

Pro volání funkcí v rámci knihovny DLL nechcete použít nepřímé volání. Linker již zná adresu funkce. Před nepřímým voláním vybere dodatečné časy a místo pro načtení a uložení adresy funkce. Přímé volání je vždy rychlejší a menší. Chcete použít **`__declspec(dllimport)`** pouze při volání funkcí knihovny DLL mimo samotné knihovny DLL. Nepoužívejte **`__declspec(dllimport)`** pro funkce v knihovně DLL při sestavování této knihovny DLL.

## <a name="see-also"></a>Viz také

[Import do aplikace](importing-into-an-application.md)
