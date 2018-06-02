---
title: __clrcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __clrcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4012eac44f376ccdeeb57227e562c672f6ba7ffe
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704578"
---
# <a name="clrcall"></a>__clrcall

**Konkrétní Microsoft**

Určuje, že funkci lze volat pouze ze spravovaného kódu.  Použití `__clrcall` pro všechny virtuální funkce, které bude možné volat jedině z spravovaného kódu. Tato konvence volání však nelze použít pro funkce, které bude volána z nativního kódu.

Použití `__clrcall` ke zlepšení výkonu při volání z spravované funkce, která se virtuální spravované funkce nebo ze spravovaného funkce spravované funkce prostřednictvím ukazatele.

Vstupní body jsou samostatný, generované kompilátorem funkce. Pokud funkce, která má oba nativní a spravovaná vstupní body, jeden z nich bude funkce skutečného s implementací funkce. Další funkce bude samostatné funkce (převodu), která volá do funkce skutečného a umožňuje provádět PInvoke modul common language runtime. Při označování funkce jako `__clrcall`, znamenat implementace funkce musí být MSIL a že se nevygeneruje funkce nativní vstupního bodu.

Když se vezme adresy nativní funkce, pokud `__clrcall` není zadán, kompilátor použije nativní vstupní bod. `__clrcall` Označuje, že funkce je spravovaný a je potřeba projít přechod z spravované na nativní. V takovém případě kompilátor použije spravované vstupní bod.

Při **/CLR** (není **/CLR: pure** nebo **/CLR: safe**) se používá a `__clrcall` se nepoužívá, trvá adresu funkce vždy vrátí adresu nativní položky funkce bodu. Když `__clrcall` se používá, funkce nativní vstupního bodu není vytvořena, takže získat adresu spravovaná funkce není funkci převodu vstupního bodu. Další informace najdete v tématu [dvojitý převod adres](../dotnet/double-thunking-cpp.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

[/ CLR (kompilace common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) znamená, že jsou všechny funkce a ukazatelů na funkce `__clrcall` a kompilátor nebude povolit funkci uvnitř kompilace nic označen jiné než `__clrcall`. Když **/CLR: pure** se používá, `__clrcall` lze zadat pouze na ukazatele na funkce a externí deklarace.

Můžete volat přímo `__clrcall` funkce z existujícího kódu C++, který byl kompilován s použitím **/CLR** tak dlouho, dokud této funkce má MSIL implementace. `__clrcall` funkce nelze volat přímo z funkcí, které mají vložené asm a volání intrinisics specifické pro procesor, například i v případě, že tyto funkce jsou kompilovat s **/CLR**.

`__clrcall` ukazatele na funkce jsou určeny pouze pro použití v doméně aplikace, v jakém byly vytvořeny.  Místo předávání `__clrcall` funkce ukazatele napříč doménami aplikací, použijte <xref:System.CrossAppDomainDelegate>. Další informace najdete v tématu [domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Příklad

Upozorňujeme, že pokud je funkce deklarovat s `__clrcall`, v případě potřeby se budou generovat kód; například když je volána funkce.

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

Následující příklad ukazuje, že můžete definovat ukazatel na funkci tak, že je deklarovat, že ukazatel funkce bude volat jenom ze spravovaného kódu. To umožňuje kompilátoru volat přímo spravovaných funkce a zamezit tak nativní vstupní bod (dvojité převodu problém).

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

- [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
- [Klíčová slova](../cpp/keywords-cpp.md)
