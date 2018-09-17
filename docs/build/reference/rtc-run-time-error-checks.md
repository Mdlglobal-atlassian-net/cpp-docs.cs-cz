---
title: -RTC (Kontrola chyb za běhu) | Dokumentace Microsoftu
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
ms.openlocfilehash: 29fd7e3ec71b38aec187f60548ce7cededd01c2b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709395"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (kontrola chyb za běhu)

Umožňuje povolit nebo zakázat funkci kontroly chyb za běhu ve spojení s [runtime_checks –](../../preprocessor/runtime-checks.md) direktivy pragma.

## <a name="syntax"></a>Syntaxe

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Arguments

**1**<br/>
Ekvivalent **/RTC**`su`.

**c**<br/>
Oznámí, že hodnota je přiřazená menší datový typ a má za následek ztrátu dat. Například, pokud hodnota typu `short 0x101` je přiřazen proměnné typu `char`.

Tato možnost sestavy situací, ve kterých chcete zkrátit, například pokud chcete, aby prvních 8 bitů `int` vrácena jako `char`. Protože **/RTC** `c` způsobí chybu za běhu při přiřazení ke ztrátě veškeré informace může zastínit vypnout informace, které potřebujete, aby se zabránilo chyb za běhu kvůli **/RTC** `c`. Příklad:

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

**s**<br/>
Umožňuje zásobníku rámce běhové kontroly chyb, následujícím způsobem:

- Inicializace lokálních proměnných na nenulovou hodnotu. To pomáhá identifikovat chyby, které nejsou zobrazeny při spuštění v režimu ladění. Je větší pravděpodobnost, že proměnné zásobníku stále bude nula v sestavení pro ladění ve srovnání s sestavení pro vydání z důvodu optimalizace kompilátoru proměnných zásobníku v sestavení pro vydání. Jakmile program použil oblast svůj zásobník, se nikdy nastaven na hodnotu 0 kompilátorem. Zásobník následné, neinicializované proměnné, které dojde k použití stejné oblasti zásobníku proto může vrátit hodnoty, které zbyly z předchozího použití této paměti zásobníku.

- Detekce přetečení a underruns lokálních proměnných, například pole. **/ RTC** `s` nerozpozná přetečení při přístupu k paměti, která je výsledkem kompilátoru odsazení v rámci struktury. Odsazení může dojít k pomocí [zarovnat](../../cpp/align-cpp.md), [/Zp (zarovnání členů struktury)](../../build/reference/zp-struct-member-alignment.md), nebo [pack](../../preprocessor/pack.md), nebo pokud uspořádat prvky struktury tak, že to vyžaduje kompilátor, aby přidat odsazení.

- Ověřování ukazatel zásobníku, které detekuje poškození ukazatel zásobníku. Poškození ukazatel zásobníku může být způsobeno neshodou konvence volání. Například pomocí ukazatele na funkci, volání funkce v knihovně DLL, který je exportován jako [__stdcall](../../cpp/stdcall.md) deklarovat ukazatel na funkci, ale [__cdecl](../../cpp/cdecl.md).

**u**<br/>
Oznámí, pokud se nějaká proměnná použije bez inicializace. Například instrukce, která generuje `C4701` může také generovat chyb za běhu v rámci **/RTC**`u`. Všechny instrukce, který generuje [upozornění kompilátoru (úroveň 1 a 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) vygeneruje Chyba za běhu v rámci **/RTC**`u`.

Nicméně zvažte následující fragment kódu:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Pokud by byl inicializován proměnnou, nebudou ohlášena v době běhu **/RTC**`u`. Například po proměnná je zaveden alias přes ukazatel, kompilátor nebude sledovat proměnné a sestavy neinicializované používá. V důsledku toho můžete inicializovat proměnnou tak převzetí jeho adresy. & – Operátor funguje jako operátor přiřazení v této situaci.

## <a name="remarks"></a>Poznámky

Kontrola chyb za běhu jsou způsob, jak můžete najít problémy v kódu spuštěného; Další informace najdete v tématu [postupy: použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks).

Pokud kompilujete aplikace příkazového řádku pomocí kteréhokoli z **/RTC** – možnosti kompilátoru, všechny – Direktiva pragma [optimalizovat](../../preprocessor/optimize.md) podle pokynů v kódu se bez upozornění nepodaří. Je to proto, že nejsou platné v sestavení pro vydání (optimalizované) Kontrola chyb za běhu.

Měli byste použít **/RTC** pro vývoj sestavení; **/RTC** nemělo používat pro sestavení prodejní verze. **/ RTC** nelze použít s optimalizace kompilátoru ([/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)). Sestavován bitové kopie programu **/RTC** širší a o něco pomalejší než image vytvořené pomocí **/Od** (až o 5 procent pomalejší než **/Od** sestavení).

Direktivy preprocesoru __MSVC_RUNTIME_CHECKS bude definovat, když použijete některou **/RTC** možnost nebo [/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Změnit jedno nebo obě z následujících vlastností: **Basic Runtime Checks** nebo **menší kontrolu**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> vlastnosti.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Postupy: Použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks)