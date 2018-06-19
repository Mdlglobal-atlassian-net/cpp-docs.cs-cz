---
title: -RTC (Kontrola chyb za běhu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a135c9c4e32ea7a54c45719eff503ff99509d3e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378454"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (kontrola chyb za běhu)
Umožňuje povolit nebo zakázat funkci Chyba spuštění kontroly ve spojení s [runtime_checks –](../../preprocessor/runtime-checks.md) – Direktiva pragma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>Arguments  
 `1`  
 Ekvivalentní **/RTC**`su`.  
  
 `c`  
 Sestavy, když je hodnota je přiřazený k menší datový typ a má za následek ztrátu dat. Například, pokud se hodnota typu `short 0x101` je přiřazený k proměnné typu `char`.  
  
 Tato možnost sestavy situace, ve kterých chcete zkrátit, například pokud chcete, aby prvních 8 bitů `int` vrátí jako `char`. Protože **/RTC** `c` Chyba spuštění způsobí, že pokud jsou všechny informace ztraceno v důsledku přiřazení, můžete maskování vypnout informace, které potřebujete, aby se zabránilo Chyba spuštění na základě těchto **/RTC** `c`. Příklad:  
  
```  
#include <crtdbg.h>  
  
char get8bits(int value, int position) {  
   _ASSERT(position < 32);  
   return (char)(value >> position);  
   // Try the following line instead:  
   // return (char)((value >> position) & 0xff);  
}  
  
int main() {  
   get8bits(12341235,3);  
}  
```  
  
 `s`  
 Umožňuje rámce Chyba spuštění, následujícím způsobem ověření zásobníku:  
  
-   Inicializace proměnných místní nenulovou hodnotu. To pomáhá identifikovat chyby, které se nezobrazí při spuštění v režimu ladění. Existuje větší pravděpodobnost zásobníku proměnné budou mít pořád nula v porovnání s sestavení pro vydání z důvodu optimalizace kompilátoru zásobníku proměnných v sestavení pro vydání sestavení ladicí verze. Jakmile program byl použit oblast jeho zásobníku, se nikdy nastaven na hodnotu 0 kompilátorem. Následné, neinicializovaného zásobníku proměnné, které mají používat stejné oblasti zásobníku proto může vrátit hodnoty, které zbyly z předchozího použití tuto paměť zásobníku.  
  
-   Rozpoznání přetečení a underruns lokálních proměnných, jako je například pole. **/ RTC** `s` nerozpozná přetečení při přístupu k paměti, která je výsledkem kompilátoru odsazení v rámci struktury. Odsazení mohlo dojít pomocí [zarovnat](../../cpp/align-cpp.md), [/Zp (zarovnání členů struktury)](../../build/reference/zp-struct-member-alignment.md), nebo [pack](../../preprocessor/pack.md), nebo pokud seřazení elementy struktury v tak, aby vyžadují kompilátoru přidat odsazení.  
  
-   Ověřování ukazatel zásobníku, které zjistí poškození ukazatel zásobníku. Poškození ukazatele zásobníku může být způsobeno volání neshoda názvů. Například pomocí ukazatel na funkci, můžete volat funkci v knihovně DLL, který je exportován jako [__stdcall](../../cpp/stdcall.md) ale deklarovat má ukazatel na funkci jako [__cdecl](../../cpp/cdecl.md).  
  
 `u`  
 Sestavy při proměnná se používá bez nutnosti inicializovány. Například příkaz, který generuje `C4701` může také generovat chybu spuštění pod **/RTC**`u`. Všechny instrukce, který generuje [upozornění kompilátoru (úroveň 1 a 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) vygeneruje Chyba spuštění pod **/RTC**`u`.  
  
 Však zvažte následující fragment kódu:  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 Pokud by byly inicializovány proměnné, nebudou ohlášena v době běhu **/RTC**`u`. Například po proměnné alias prostřednictvím ukazatele, kompilátor nebude sledovat proměnnou a sestavy, neinicializovaného používá. V důsledku toho můžete inicializovat proměnné provedením jeho adresy. & Operátor funguje jako operátor přiřazení v této situaci.  
  
## <a name="remarks"></a>Poznámky  
 Kontrola chyb za běhu jsou způsob, jak je možné vyhledat potíže v spuštěného kódu; Další informace najdete v tématu [postupy: použití nativního Run-Time kontroluje](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Pokud je váš program na příkazovém řádku pomocí kteréhokoli **/RTC** – možnosti kompilátoru, všechny – Direktiva pragma [optimalizovat](../../preprocessor/optimize.md) bez upozornění selže pokyny v kódu. Je to proto, že kontrola chyb za běhu nejsou platné v sestavení pro vydání (optimalizované).  
  
 Měli byste použít **/RTC** pro vývoj sestavení; **/RTC** by se neměla používat pro prodejní sestavení. **/ RTC** nelze použít s optimalizace kompilátoru ([/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)). Vytvořené bitové kopie programu s **/RTC** budou mírně větší a mírně nižší než image vytvořené s **/Od** (až 5 procent nižší než **/Od** sestavení).  
  
 Direktivy preprocesoru __msvc_runtime_checks – budou definovány, když používáte jakoukoli **/RTC** možnost nebo [/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **generování kódu** stránku vlastností.  
  
4.  Změňte jednu nebo obě z následujících vlastností: **základní kontroluje Runtime** nebo **menší zkontrolujte typ**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Postupy: použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks)