---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857603"
---
# <a name="__clrcall"></a>__clrcall

Určuje, že funkci lze volat pouze ze spravovaného kódu.  Použijte **__clrcall** pro všechny virtuální funkce, které budou volány pouze ze spravovaného kódu. Nicméně tuto konvenci volání nelze použít pro funkce, které budou volány z nativního kódu. Modifikátor **__clrcall** je specifický pro společnost Microsoft.

Pomocí **__clrcall** můžete zvýšit výkon při volání ze spravované funkce do virtuální spravované funkce nebo ze spravované funkce přes ukazatel.

Vstupní body jsou oddělené, funkce generované kompilátorem. Pokud má funkce nativní i spravované vstupní body, jedna z nich bude skutečnou funkcí s implementací funkce. Druhá funkce bude samostatnou funkcí (převodem), která volá do skutečné funkce a umožňuje, aby modul common language runtime prováděl PInvoke. Při označování funkce jako **__clrcall**označíte, že implementace funkce musí být MSIL a že funkce nativního vstupního bodu nebude vygenerována.

Když převezmete adresu nativní funkce, pokud není zadán **__clrcall** , kompilátor použije nativní vstupní bod. **__clrcall** označuje, že je funkce spravovaná a není nutné přecházet mezi přechodem ze spravovaného do nativního. V takovém případě kompilátor používá spravovaný vstupní bod.

Pokud se používá `/clr` (není `/clr:pure` nebo `/clr:safe`) a **__clrcall** se nepoužívá, převzetí adresy funkce vždycky vrátí adresu nativní funkce vstupního bodu. Při použití **__clrcall** není vytvořena funkce nativního vstupního bodu, takže získáte adresu spravované funkce, nikoli funkci převolání vstupní bod. Další informace najdete v tématu [Double dvojitý](../dotnet/double-thunking-cpp.md). Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

[/CLR (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) znamená, že všechny funkce a ukazatele funkcí jsou **__clrcall** a kompilátor nepovoluje, aby byla funkce uvnitř kompilantu označena jako žádná jiná než **__clrcall**. Je-li použita možnost **/clr: Pure** , **__clrcall** lze zadat pouze pro ukazatele na funkce a externí deklarace.

Můžete přímo volat **__clrcall** funkce z existujícího C++ kódu, který byl zkompilován pomocí **/CLR** , pokud má tato funkce implementaci MSIL. funkce **__clrcall** nelze volat přímo z funkcí, které obsahují vložený ASM a volání intrinisics specifických pro procesor, a to i v případě, že jsou tyto funkce kompilovány pomocí `/clr`.

**__clrcall** ukazatelé na funkce jsou určeny pouze k použití v doméně aplikace, ve které byly vytvořeny.  Místo předání ukazatelů **__clrcall** funkcí napříč doménami aplikace použijte <xref:System.CrossAppDomainDelegate>. Další informace najdete v tématu [domény aplikace a vizuál C++ ](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Příklad

Všimněte si, že pokud je funkce deklarována s **__clrcall**, kód bude vygenerován v případě potřeby; například při volání funkce.

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

Následující příklad ukazuje, že můžete definovat ukazatel na funkci, například, deklarujete, že ukazatel na funkci bude vyvolán pouze ze spravovaného kódu. Díky tomu může kompilátor přímo volat spravovanou funkci a vyhnout se nativnímu vstupnímu bodu (problém s dvojitým převodem).

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
