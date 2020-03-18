---
title: Import volání funkcí pomocí deklarace __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442521"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Import volání funkcí pomocí deklarace __declspec(dllimport)

Následující příklad kódu ukazuje, jak použít **_declspec (dllimport)** pro import volání funkcí z knihovny DLL do aplikace. Předpokládejme, že `func1` je funkce, která se nachází v knihovně DLL oddělené od souboru. exe, který obsahuje funkci **Main** .

Bez **__declspec (dllimport)** , s ohledem na tento kód:

```
int main(void)
{
   func1();
}
```

Kompilátor generuje kód, který vypadá takto:

```
call func1
```

a linker překládá volání do podobného:

```
call 0x4000000         ; The address of 'func1'.
```

Pokud `func1` existuje v jiné knihovně DLL, linker nemůže tento problém přímo vyřešit, protože nemá žádný způsob, jak zjistit, co je adresa `func1`. V 16bitovém prostředí linker přidá tuto adresu kódu do seznamu v souboru. exe, který zavaděč by v době běhu zavolal správnou adresu. V 32 bitové a 64 prostředí linker vygeneruje převolání, jehož adresa zná. V 32 bitovém prostředí může převod kódu vypadat jako:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Tady `imp_func1` je adresa `func1` pozice v tabulce Import adres souboru. exe. Všechny adresy jsou tedy pro linker známé. Zavaděč musí aktualizovat tabulku importovaných adres souboru. exe v době načítání, aby vše správně fungovalo.

Proto je použití **__declspec (dllimport)** lepší, protože linker negeneruje převod na více adres, pokud není požadován. Převodní rutiny zvětšit kód (v systémech RISC může to být několik pokynů) a může snížit výkon mezipaměti. Pokud kompilátor říkáte, že je funkce v knihovně DLL, může pro vás vygenerovat nepřímou hovor.

Takže teď tento kód:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

vygeneruje tuto instrukci:

```
call DWORD PTR __imp_func1
```

Není k dispozici žádný příkaz k převolání a žádné `jmp` instrukci, takže kód je menší a rychlejší.

Na druhé straně pro volání funkcí v rámci knihovny DLL nechcete použít nepřímé volání. Adresu funkce už znáte. Vzhledem k tomu, že k načtení a uložení adresy funkce před nepřímým voláním je nutné zadat čas a prostor, je přímé volání vždy rychlejší a menší. Chcete použít **__declspec (dllimport)** při volání funkcí DLL mimo samotný soubor DLL. Nepoužívejte **__declspec (dllimport)** na funkcích v knihovně DLL při sestavování této knihovny DLL.

## <a name="see-also"></a>Viz také

[Import do aplikace](importing-into-an-application.md)
