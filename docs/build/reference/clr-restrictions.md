---
title: /clr – omezení
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294457"
---
# <a name="clr-restrictions"></a>/clr – omezení

Mějte na paměti následující omezení týkající se použití **/CLR**:

- Strukturovanou obslužnou rutinou, existují omezení používání `_alloca` při kompilaci s **/CLR**. Další informace najdete v tématu [_alloca](../../c-runtime-library/reference/alloca.md).

- Použití kontroly chyb za běhu není platná s **/CLR**. Další informace najdete v tématu [jak: Použití nativních kontrol za běhu](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Když **/CLR** se používá ke kompilaci program, který se používá pouze standardní syntaxe jazyka C++, následující pokyny se vztahují na užívání vložené sestavení:

  - Vložený kód sestavení, která předpokládá znalost rozložení nativní zásobníku, mimo aktuální funkci nebo jiné nízké úrovně informace o počítači konvence volání může selhat, pokud použitém znalostní báze pro rámce zásobníku pro spravované funkce. Funkce obsahující vložený kód sestavení jsou generovány jako nespravované funkce, jako kdyby byly umístěny do samostatných modul, který se zkompiloval bez **/CLR**.

  - Vložený kód sestavení funkcí, které předávají parametry vytvořena kopie funkce není podporována.

- [Vprintf – funkce](../../c-runtime-library/vprintf-functions.md) nejde volat z programu kompilovaného s **/CLR**.

- [Naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modifikátor se ignoruje pod parametrem/CLR.

- Funkce translator nastavil [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) ovlivní pouze přetáhněte aktivity catch v nespravovaném kódu. Zobrazit [zpracování výjimek](../../extensions/exception-handling-cpp-component-extensions.md) Další informace.

- Porovnání ukazatelů na funkce není povolená v rámci **/CLR**.

- V části není povoleno použití funkce, které nejsou používat plně prototypované **/CLR**.

- Následující možnosti kompilátoru nepodporuje **/CLR**:

  - **/ EHsc** a **/EHS** (**/CLR** znamená **/EHa** (viz [/EH (Model zpracování výjimek)](eh-exception-handling-model.md))

  - **/ FP: strict** a **/FP: except** (viz [/fp (určení chování plovoucí desetinné čárky)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- Kombinace `_STATIC_CPPLIB` Definice preprocesoru (`/D_STATIC_CPPLIB`) a **/CLR** – možnost kompilátoru není podporován. Důvodem je, že definice by způsobit, že aplikace k propojení s statické s více vlákny standardní knihovny C++, což není podporováno. Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](md-mt-ld-use-run-time-library.md) tématu.

- Při použití **/zi** s **/CLR**, existují vliv na výkon. Další informace najdete v tématu [/zi](z7-zi-zi-debug-information-format.md).

- Široký znak předá do rozhraní .NET Framework výstupu rutiny zároveň neurčí [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) nebo bez přetypování znak, který má `__wchar_t` způsobí, že výstup jako `unsigned short int`. Příklad:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) je ignorována při kompilaci s **/CLR**, pokud je funkce v rámci `#pragma` [nespravované](../../preprocessor/managed-unmanaged.md) nebo pokud funkce musí být zkompilována pro nativní, v takovém případě bude kompilátor generovat upozornění C4793, což je vypnuto ve výchozím nastavení.

- Zobrazit [/Entry](entry-entry-point-symbol.md) pro požadavky na podpis funkce spravované aplikace.

- Zkompilovaná aplikace **/OpenMP** a **/CLR** lze spustit pouze v procesu jedinou doménu appdomain.  Zobrazit [/OpenMP (povolit podporu OpenMP 2.0)](openmp-enable-openmp-2-0-support.md) Další informace.

- Jako nativní funkce se vygeneruje funkcí, které přijímají proměnný počet argumentů (vararg). Všechny spravované datové typy argumentů s proměnnou délkou pozici bude zařazeno do nativních typů. Všimněte si, že <xref:System.String?displayProperty=fullName> typy jsou ve skutečnosti širokoznaké řetězce, ale jsou zařazeny do jednobajtové znakové řetězce. Proto u printf specifikátor %S (wchar_t *) se ho budou zařazování na řetězec %s místo.

- Když pomocí va_arg – makro, může se zobrazit neočekávané výsledky při kompilaci s **/CLR: pure**. Další informace najdete v tématu [va_arg va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Kód, který musí být "čistě" nebo "bezpečné" by měl být přenést do C#.

- Neměli volat ze spravovaného kódu, všechny funkce, které procházení zásobníku, chcete-li získat informace o parametrech (argumenty funkce); P/Invoke vrstvy způsobí, že tyto informace se níže do zásobníku.  Například, nejde zkompilovat proxy nebo zástupné procedury s **/CLR**.

- Funkce bude zkompilována do spravovaného kódu, kdykoli je to možné, ale ne všechny konstruktory jazyka C++ lze přeložit do spravovaného kódu.  Určení se provádí na základě funkce funkce. Pokud žádnou část funkce se nedá převést na spravovaný kód, celou funkci se převedou do nativního kódu místo toho. Následujících případech zabránění kompilátoru generování spravovaného kódu.

  - Převodní rutiny generované kompilátorem nebo pomocné funkce. Nativní převodní rutiny jsou generovány pro každé volání funkce prostřednictvím ukazatele na funkci, včetně volání virtuální funkce.

  - Toto volání funkce `setjmp` nebo `longjmp`.

  - Funkce, které používají určité vnitřní rutiny přímo manipulovat s prostředky počítače. Například použití `__enable` a `__disable`, `_ReturnAddress` a `_AddressOfReturnAddress`, nebo multimediální vnitřní objekty budou všechny výsledek v nativním kódu.

  - Funkce, které následují `#pragma unmanaged` směrnice. (Všimněte si, že inverzní `#pragma managed`, je také podporována.)

  - Funkce, která obsahuje odkazy na zarovnané typy, to znamená, typy deklarované pomocí `__declspec(align(...))`.

## <a name="see-also"></a>Viz také:

- [/clr (kompilace modulu Common Language Runtime)](clr-common-language-runtime-compilation.md)
