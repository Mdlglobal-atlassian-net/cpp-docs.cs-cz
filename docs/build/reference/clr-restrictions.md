---
title: -clr omezení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 697e2a50e8c63928a52bd1d960dcdefad0fe87bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="clr-restrictions"></a>/clr – omezení
Všimněte si následujících omezení pro použití **/CLR**:  
  
-   Obslužná rutina strukturovaného výjimek, existují omezení používání `_alloca` při kompilaci s **/CLR**. Další informace najdete v tématu [_alloca –](../../c-runtime-library/reference/alloca.md).  
  
-   Použití Kontrola chyb za běhu není platný s **/CLR**. Další informace najdete v tématu [postupy: použití nativního Run-Time kontroluje](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
-   Když **/CLR** se používá ke kompilaci program, který používá jenom standardní C++ syntaxe, platí následující pokyny pro použití vloženého sestavení:  
  
    -   Kód vnořeného sestavení, která předpokládá znalost rozložení nativní zásobníku, konvence mimo aktuální funkce nebo další nízké úrovně informace o počítači volání může selhat v případě použitý znalostní báze na rámec zásobníku pro spravované funkce. Funkce obsahující kódu vnořeného sestavení jsou generovány jako nespravované funkce, jako kdyby byly umístěny v samostatný modul, který se zkompiluje bez **/CLR**.  
  
    -   Kód vnořeného sestavení v funkce, které předat parametry kopie vytvořená funkce není podporována.  
  
-   [Vprintf – funkce](../../c-runtime-library/vprintf-functions.md) nelze volat z programu kompilovat s **/CLR**.  
  
-   [Holé](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) Modifikátor je ignorován v/CLR.  
  
-   Funkce překladač nastavena [_set_se_translator –](../../c-runtime-library/reference/set-se-translator.md) ovlivní pouze úlovky v nespravovaném kódu. V tématu [zpracování výjimek](../../windows/exception-handling-cpp-component-extensions.md) Další informace.  
  
-   Porovnání ukazatelů na funkce není povolena v rámci **/CLR**.  
  
-   V části není povoleno použití funkce, které nejsou plně deklaraci **/CLR**.  
  
-   Nejsou podporovány následující možnosti kompilátoru s **/CLR**:  
  
    -   **/ EHsc** a **/EHs** (**/CLR** znamená **/EHa** (viz [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md))  
  
    -   **/FP: striktní** a **/fp: kromě** (viz [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md))  
  
    -   [/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **/ZI**  
  
-   Kombinace `_STATIC_CPPLIB` definování preprocesoru (`/D_STATIC_CPPLIB`) a **/CLR** – možnost kompilátoru není podporován. Je to tak proto definici by způsobit, že aplikace pro propojení statické vícevláknové standardní knihovna C++, což není podporováno. Další informace najdete v tématu [/MD, / MT, /LD (použít běhovou knihovnu)](../../build/reference/md-mt-ld-use-run-time-library.md) tématu.  
  
-   Při použití **/Zi** s **/CLR**, existují ovlivnit výkon. Další informace najdete v tématu [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
-   Předání široká znaková rozhraní .NET Framework výstup rutiny bez zadání také [/Zc:](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) nebo bez přetypování znak, který má `__wchar_t` způsobí, že výstup zobrazovat jako `unsigned short int`. Příklad:  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [/GS](../../build/reference/gs-buffer-security-check.md) se ignoruje při kompilaci s **/CLR**, pokud je funkce pod `#pragma` [nespravované](../../preprocessor/managed-unmanaged.md) nebo pokud funkce musí být zkompilovány v nativním režimu, v takovém případě bude generovat kompilátoru upozornění C4793, který je ve výchozím nastavení vypnutá.  
  
-   V tématu [/Entry](../../build/reference/entry-entry-point-symbol.md) požadavky podpis funkce spravované aplikace.  
  
-   Aplikace, kompilovat s **/OpenMP** a **/CLR** lze spustit pouze v jednom objektu třídy appdomain procesu.  V tématu [/OpenMP (povolit podporu OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md) Další informace.  
  
-   Jako nativní funkce se budou generovat funkcí, které přijímají proměnný počet argumentů (vararg). Všechny spravované datové typy argumentů s proměnnou pozici zařazeno pro nativní typy. Všimněte si, že <xref:System.String?displayProperty=fullName> typy jsou ve skutečnosti široká charakterová řetězce, ale jsou zařazené do znakovou řetězců. Proto pokud specifikátor printf %S (wchar_t *), ji budou zařazování na řetězec %s místo.  
  
-   Pokud používáte va_arg – makro, můžete obdržet neočekávané výsledky, když kompilujete s **/CLR: pure**.  Další informace najdete v tématu [va_arg –, va_copy –, va_end –, va_start –](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md).  
  
-   Neměli volat ze spravovaného kódu, všechny funkce, které provede zásobníku se získat informace o parametrech (argumenty funkce); vrstva P/Invoke způsobí, že tyto informace dále dolů v zásobníku.  Například nejde kompilovat proxy/stub s **/CLR**.  
  
-   Funkce se zkompiluje do spravovaného kódu, pokud je to možné, ale ne všechny konstrukce C++ by bylo možné převést do spravovaného kódu.  Toto rozhodnutí se provádí na základě pomocí funkcí. Pokud libovolná součást funkce nelze převést do spravovaného kódu, celý funkce bude převedena místo toho do nativního kódu. V následujících případech zabránit kompilátor generování spravovaného kódu.  
  
    -   Generované kompilátorem převody nebo pomocných funkcí. Nativní převody jsou generovány žádné volání funkce prostřednictvím ukazatel na funkci, včetně virtuální funkce volání.  
  
    -   Toto volání funkce `setjmp` nebo `longjmp`.  
  
    -   Funkce, které přímo pracovat s prostředky počítače pomocí určitých vnitřní rutiny. Například použití `__enable` a `__disable`, `_ReturnAddress` a `_AddressOfReturnAddress`, nebo multimédií vnitřní funkce budou všechny výsledek v nativním kódu.  
  
    -   Funkce následujících `#pragma unmanaged` – direktiva. (Všimněte si, že inverzní, `#pragma managed`, je také podporována.)  
  
    -   Funkci, která obsahuje odkazy na zarovnán typů, který je typy deklarováno s použitím `__declspec(align(...))`.  
  
## <a name="see-also"></a>Viz také  
 [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)