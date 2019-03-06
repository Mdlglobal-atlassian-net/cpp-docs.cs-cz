---
title: Import volání funkcí pomocí deklarace __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 055edf4efc066695abb60a09b84cb1b13302af9c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423960"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Import volání funkcí pomocí deklarace __declspec(dllimport)

Následující příklad kódu ukazuje, jak používat **_declspec(dllimport)** Import volání funkcí z knihovny DLL do aplikace. Předpokládejme, že `func1` je funkce, která se nachází v knihovně DLL nezávisle na soubor .exe, který obsahuje **hlavní** funkce.

Bez **__declspec(dllimport)**, daný tento kód:

```
int main(void)
{
   func1();
}
```

kompilátor generuje kód, který vypadá takto:

```
call func1
```

a propojovací program překládá volání do vypadat přibližně takto:

```
call 0x4000000         ; The address of 'func1'.
```

Pokud `func1` existuje v jiné knihovně DLL linkeru nelze vyřešit přímo protože nemá žádný způsob jak zjistit, jaká je adresa `func1` je. V prostředích s 16 bitů přidá linker adresu tohoto kódu do seznamu v souboru .exe, který by zavaděč za běhu se správnou adresou. V 32bitové a 64bitové prostředí linker generuje převodní rutina z nich ví, že adresu. V prostředí s 32-bit převodní rutině vypadá jako:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Tady `imp_func1` následuje adresa pro `func1` místo v tabulky importních adres souboru .exe. Všechny adresy jsou proto známé linkeru. Zavaděč má pouze k aktualizaci tabulky importních adres soubor .exe v okamžiku načtení pro všechno, co fungovat správně.

Proto pomocí **__declspec(dllimport)** je lepší, protože linkeru negeneruje převodní rutinou, pokud se nevyžaduje. Převodní rutiny zvětšit kód (v systémech RISC, může být několik pokyny) a může snížit výkon mezipaměti. Pokud dáte kompilátor, že je funkce v knihovně DLL, může vygenerovat nepřímé volání za vás.

Takže teď tento kód:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

generuje tento pokyn:

```
call DWORD PTR __imp_func1
```

Neexistuje žádný převodní rutina a ne `jmp` instrukce, takže kód je menší a rychlejší.

Na druhé straně pro volání funkce uvnitř knihovny DLL, nechcete k použít nepřímé volání. Adresa funkce už znáte. Protože jsou náročné na načítají a ukládají adresu funkce před nepřímé volání na čas a prostor, přímého volání je vždy menší a rychlejší. Chcete použít **__declspec(dllimport)** při volání funkcí knihovny DLL mimo samotná knihovna DLL. Nepoužívejte **__declspec(dllimport)** ve funkcích uvnitř knihovny DLL při vytváření této knihovny DLL.

## <a name="see-also"></a>Viz také:

[Import do aplikace](../build/importing-into-an-application.md)
