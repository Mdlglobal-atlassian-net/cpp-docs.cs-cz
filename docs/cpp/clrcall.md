---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: bc44feb97223de47f45734f75777ee040d0ebdd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364568"
---
# <a name="clrcall"></a>__clrcall

**Microsoft Specific**

Určuje, že funkce lze volat pouze ze spravovaného kódu.  Použití **__clrcall** pro všechny virtuální funkce, které bude volat pouze ze spravovaného kódu. Tato konvence volání však nelze použít pro funkce, které budou volat z nativního kódu.

Použití **__clrcall** ke zlepšení výkonu při volání metody ze spravované funkce virtuální spravované funkce nebo ze spravované funkce spravované funkce prostřednictvím ukazatele.

Vstupní body jsou samostatný, vygeneruje kompilátor funkce. Pokud je funkce i nativní a spravovaný vstupní body, jeden z nich bude skutečné funkce s implementací funkce. Další funkce bude o samostatnou funkci (převodní rutina), která volá do skutečné funkce a umožňuje provádět PInvoke modul common language runtime. Při označení funkci tak, aby **__clrcall**, označují implementace funkce musí být jazyk MSIL a nevygeneruje funkci nativní vstupního bodu.

Při převzetí adresy nativní funkce, pokud **__clrcall** není zadán, kompilátor používá nativní vstupní bod. **výraz __clrcall** označuje, že spravované funkce a je nutné absolvovat přechod ze spravované na nativní. V takovém případě kompilátor používá spravovaný vstupní bod.

Když `/clr` (ne `/clr:pure` nebo `/clr:safe`) se používá a **__clrcall** je nepoužívá, převzetí adresy funkce vždy vrátí adresu funkce nativní vstupní bod. Když **__clrcall** se používá, funkci nativní vstupního bodu není vytvořen, takže získáte adresy spravované funkce, nikoli funkci převodní rutina vstupního bodu. Další informace najdete v tématu [dvojitému](../dotnet/double-thunking-cpp.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

[/ CLR (kompilace common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) znamená, že jsou všechny funkce a ukazatelů na funkce **__clrcall** a kompilátor nebude povolit funkci uvnitř kompilantu nic jiného než Označit **__clrcall**. Když **/CLR: pure** se používá, **__clrcall** lze zadat pouze na ukazatele na funkce a externí deklarace.

Můžete volat přímo **__clrcall** funkce z již existujících C++ kód, který byl zkompilován pomocí **/CLR** za předpokladu, tato funkce je implementace jazyka MSIL. **výraz __clrcall** funkce nelze volat přímo z funkcí, které mají vloženého kódu asm a volání intrinisics specifické pro procesor, například i v případě, že tyto funkce jsou kompilovány pomocí `/clr`.

**výraz __clrcall** ukazatelů na funkce jsou určeny pouze pro použití v aplikační doméně, ve kterém byly vytvořeny.  Namísto předání **__clrcall** ukazatele funkcí napříč doménami aplikace, použijte <xref:System.CrossAppDomainDelegate>. Další informace najdete v tématu [aplikačních doménách a Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Příklad

Upozorňujeme, že pokud je funkce deklarovaná pomocí **__clrcall**, kód bude vytvořen, pokud je nepotřebujete, například když je volána funkce.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, že ukazatel na funkci, můžete definovat tak, že je deklarovat, že ukazatel funkce bude volat pouze ze spravovaného kódu. To umožňuje kompilátoru přímo volat funkci spravovaný a nativní vstupní bod (double převodní rutina problém).

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
