---
title: 'Postupy: Migrace do prostředí -clr'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 337dc69b60537fba8484837981fc6be0971c69cb
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711134"
---
# <a name="how-to-migrate-to-clr"></a>Postupy: Migrovat na/CLR

Toto téma popisuje problémy, které vznikají při kompilování nativního kódu s **/CLR** (Další informace naleznete v tématu věnovaném [kompilaci/clr (Common Language Runtime))](../build/reference/clr-common-language-runtime-compilation.md) . **/CLR** umožňuje vyvolání C++ nativního kódu a jeho vyvolání ze sestavení .NET spolu s jiným nativním C++ kódem. Další informace o výhodách kompilace s možností **/CLR**naleznete v tématu [smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní interoperabilita rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md) .

## <a name="known-issues-compiling-library-projects-with-clr"></a>Známé problémy při kompilování projektů knihoven s/CLR

Visual Studio obsahuje některé známé problémy při kompilování projektů knihoven s **/CLR**:

- Váš kód může dotazovat typy za běhu pomocí [CRuntimeClass:: from](../mfc/reference/cruntimeclass-structure.md#fromname). Pokud je však typ v jazyce MSIL. dll (kompilováno s možností **/CLR**), volání `FromName` může selhat, pokud k němu dojde před spuštěním statických konstruktorů ve spravované knihovně DLL (Tento problém neuvidíte, pokud se k volání metody from dojde poté, co byl kód proveden ve spravovaném objektu. DLL). Chcete-li tento problém obejít, můžete vynutit konstrukci spravovaného statického konstruktoru definováním funkce ve spravované knihovně DLL, jejím exportem a jejím vyvoláním z nativní aplikace MFC. Příklad:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompilace v jazyce Visual C++

Před použitím **/CLR** na jakémkoli modulu v projektu nejdříve zkompilujte a propojte svůj nativní projekt se sadou Visual Studio 2010.

Následující kroky, následované v pořadí, poskytují nejjednodušší cestu k kompilaci **/CLR** . Je důležité zkompilovat a spustit projekt po každém z těchto kroků.

### <a name="versions-prior-to-visual-studio-2003"></a>Verze předcházející verzi Visual Studio 2003

Pokud provádíte upgrade na Visual Studio 2010 z verze před Visual Studio 2003, mohou se zobrazit chyby kompilátoru týkající se vylepšeného C++ standardu shody v aplikaci visual Studio 2003.

### <a name="upgrading-from-visual-studio-2003"></a>Upgrade ze sady Visual Studio 2003

Projekty, které byly dříve sestaveny pomocí sady Visual Studio 2003, by měly být také nejprve kompilovány bez možnosti **/CLR** , protože Visual Studio nyní zvýšilo kompatibilitu ANSI/ISO a některé zásadní změny. Změna, která bude pravděpodobně vyžadovat největší pozornost, je [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md). Kód, který používá CRT, má velmi pravděpodobně za následek vyřazení upozornění na zastarání. Tato upozornění se dají potlačit, ale migrace na nové [verze funkcí CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) s rozšířeným zabezpečením je upřednostňovaná, protože poskytují lepší zabezpečení a můžou odhalit problémy zabezpečení ve vašem kódu.

### <a name="upgrading-from-managed-extensions-for-c"></a>Upgrade ze spravovaných rozšíření proC++

Počínaje sadou Visual Studio 2005 kód napsaný pomocí spravovaných rozšíření C++ pro nebude zkompilován v rámci **/CLR**.

## <a name="convert-c-code-to-c"></a>Převést kód jazyka C naC++

I když Visual Studio bude kompilovat soubory jazyka C, je nutné je převést na C++ pro kompilaci **/CLR** . Skutečný název souboru není nutné změnit. můžete použít **/TP** (viz [/TC,/TP,/TC,/TP (určení typu zdrojového souboru)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Ačkoliv C++ soubory zdrojového kódu jsou požadovány pro **/CLR**, není nutné znovu faktorovat kód pro použití objektově orientovaných paradigma.

Kód jazyka C má velmi pravděpodobně vyžadovat změny při kompilování jako C++ soubor. Pravidla C++ zabezpečení typu jsou striktní, takže převody typu musí být provedeny explicitně pomocí přetypování. Například funkce obsazení vrátí ukazatel void, ale dá se přiřadit k ukazateli na libovolný typ v C s přetypováním:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Ukazatele na funkce jsou také striktně typově bezpečné v C++, takže následující kód jazyka C vyžaduje změnu. C++ Je nejvhodnější vytvořit `typedef` , který definuje typ ukazatele na funkci, a pak použít tento typ k přetypování ukazatelů na funkce:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++také vyžaduje, aby funkce byly prototypem nebo zcela definovány, než mohou být odkazovány nebo vyvolány.

Identifikátory používané v kódu jazyka C, které se vyskytují v C++ klíčových slovech (například **Virtual**, **New**, **Delete**, **bool**, **true**, **false**atd.), musí být přejmenovány. To se dá obecně udělat pomocí jednoduchých operací vyhledávání a nahrazování.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Překonfigurovat nastavení projektu

Po zkompilování a spuštění projektu v aplikaci Visual Studio 2010 byste měli vytvořit nové konfigurace projektu pro **/CLR** místo úprav výchozích konfigurací. **/CLR** je nekompatibilní s některými možnostmi kompilátoru a vytváření samostatných konfigurací umožňuje sestavit projekt jako nativní nebo spravovaný. Je-li v dialogovém okně stránky vlastností vybrána možnost **/CLR** , nastavení projektu není kompatibilní s možností **/CLR** je zakázáno (a pokud je vlastnost **/CLR** následně Nevybraná, nejsou automaticky obnoveny možnosti, které jsou zakázány).

### <a name="create-new-project-configurations"></a>Vytvořit nové konfigurace projektu

V **dialogovém okně Nový projekt konfigurace** můžete použít možnost **Kopírovat nastavení z** (**vytvořit** > **Configuration Manager** > **aktivní řešení konfigurace** > **nové**). pro vytvoření konfigurace projektu na základě vašeho existujícího nastavení projektu. Provedete to jednou pro konfiguraci ladění a jednou pro konfiguraci vydaných verzí. Následné změny se pak dají použít jenom pro konfigurace specifické pro **/CLR** , takže původní konfigurace projektu zůstanou beze změny.

Projekty, které používají vlastní pravidla sestavení, mohou vyžadovat dodatečnou pozornost.

Tento krok má různé důsledky pro projekty, které používají soubory pravidel. V takovém případě lze nakonfigurovat samostatný cíl sestavení nebo může být vytvořena verze specifická pro kompilaci **/CLR** z kopie původní.

### <a name="change-project-settings"></a>Změnit nastavení projektu

**/CLR** lze vybrat ve vývojovém prostředí podle pokynů v tématu [/CLR (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Jak bylo zmíněno dříve, tento krok automaticky zakáže konfliktní nastavení projektu.

> [!NOTE]
>  Při upgradu spravované knihovny nebo projektu webové služby ze sady Visual Studio 2003 se možnost kompilátoru **/zl** přidá do stránky vlastností **příkazového řádku** . Tato akce způsobí LINKERŮ LNK2001. Odstraňte **/zl** ze stránky vlastností **příkazového řádku** , která se má vyřešit. Další informace naleznete v tématu [/zl (vynechání názvu výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) a [nastavení kompilátoru a vlastností buildu](../build/working-with-project-properties.md) . Nebo přidejte Msvcrt. lib a msvcmrt. lib do vlastnosti **doplňkové závislosti** linkeru.

Pro projekty sestavené pomocí souborů pravidel musí být nekompatibilní možnosti kompilátoru zakázané ručně po přidání **/CLR** . Zobrazit/[/clr omezení](../build/reference/clr-restrictions.md) pro informace o možnostech kompilátoru, které nejsou kompatibilní s **/CLR**.

### <a name="precompiled-headers"></a>Předkompilované hlavičky

Předkompilované hlavičky jsou podporovány v rámci **/CLR**. Nicméně pokud kompilujete pouze některé soubory CPP s možností **/CLR** (kompilace REST jako nativní), budou vyžadovány některé změny, protože předkompilované hlavičky vygenerované pomocí **/CLR** nejsou kompatibilní s generovanými bez **/CLR**. Tato nekompatibilita je způsobena faktem, že **/CLR** generuje a vyžaduje metadata. Moduly zkompilované s možností **/CLR** mohou proto nepoužívat předkompilované hlavičky, které neobsahují metadata, a ne/CLR moduly nemohou použít předkompilované hlavičkové soubory, které obsahují meta data.

Nejjednodušší způsob, jak zkompilovat projekt, kde jsou některé moduly kompilovány **/CLR** , je zcela zakázat předkompilované hlavičky. (V dialogovém okně stránky vlastností projektu otevřete C/C++ uzel a vyberte předkompilované hlavičky. Pak změňte vlastnost Předkompilovaná Headers na "Nepoužívat předkompilované hlavičky".)

Nicméně, zejména u velkých projektů, předkompilovaných hlaviček poskytuje mnohem lepší rychlost kompilace, takže zakázání této funkce není žádoucí. V tomto případě je nejvhodnější nakonfigurovat soubory **/CLR** a non **/CLR** na použití oddělených předkompilovaných hlaviček. To lze provést v jednom kroku vícenásobným výběrem modulů, které mají být zkompilovány **/CLR** pomocí **Průzkumník řešení**, klikněte pravým tlačítkem na skupinu a vyberte možnost Vlastnosti. Pak změňte název souboru Create/use PCH prostřednictvím souborových a předkompilovaných vlastností hlavičkového souboru tak, aby v uvedeném pořadí používal jiný název hlavičkového souboru a soubor PCH.

## <a name="fixing-errors"></a>Oprava chyb

Kompilace s **/CLR** může vést k chybám kompilátoru, linkeru nebo běhu. Tato část popisuje nejběžnější problémy.

### <a name="metadata-merge"></a>Sloučení metadat

Rozdílné verze datových typů mohou způsobit selhání linkeru, protože metadata vygenerovaná pro tyto dva typy se neshodují. (To je obvykle způsobeno podmínkou definování členů typu, ale podmínky nejsou stejné pro všechny soubory CPP, které používají typ.) V tomto případě se linker nezdařil, hlásí pouze název symbolu a název druhého souboru OBJ, kde byl typ definován. Je často vhodné otočit pořadí, které soubory OBJ odesílají do linkeru, aby bylo možné zjistit umístění jiné verze datového typu.

### <a name="loader-lock-deadlock"></a>Zablokování zámku zavaděče

"Zablokování zámku zavaděče" může nastat, ale je deterministické a je zjištěno a hlášeno za běhu. Podrobné informace o pozadí, pokynech a řešeních naleznete v tématu [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md) .

### <a name="data-exports"></a>Exporty dat

Export dat knihovny DLL je náchylný k chybám a nedoporučuje se. Důvodem je, že není zaručeno inicializovat oddíl dat knihovny DLL, dokud není provedena určitá spravovaná část knihovny DLL. Odkazuje na metadata pomocí [direktivy #using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Viditelnost typů

Nativní typy jsou ve výchozím nastavení privátní. To může mít za následek, že nativní typ není viditelný vně knihovny DLL. Tuto chybu můžete vyřešit přidáním `public` do těchto typů.

### <a name="floating-point-and-alignment-issues"></a>Problémy s plovoucí desetinnou čárkou a zarovnáním

`__controlfp`není podporován v modulu CLR (Common Language Runtime) (Další informace naleznete v tématu [_control87, _controlfp \_, _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) ). CLR taky nebude respektovat [Zarovnání](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicializace modelu COM

Modul CLR (Common Language Runtime) inicializuje automaticky COM při inicializaci modulu (když je model COM inicializován automaticky, je proveden jako MTA). V důsledku toho explicitní inicializace modelu COM vrátí návratové kódy indikující, že je model COM již inicializován. Pokus o explicitní inicializaci modelu COM s jedním modelem vláken, když CLR již inicializoval model COM do jiného modelu vláken, může způsobit selhání vaší aplikace.

Modul CLR (Common Language Runtime) spouští ve výchozím nastavení COM jako MTA. pro úpravu použijte [/CLRTHREADATTRIBUTE (nastavení atributu vlákna modulu CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) .

### <a name="performance-issues"></a>Problémy s výkonem

V případě, že nativní C++ metody generované do jazyka MSIL jsou volány nepřímo (volání virtuálních funkcí nebo použití ukazatelů na funkce), může dojít ke snížení výkonu. Další informace najdete v tématu [Double dvojitý](../dotnet/double-thunking-cpp.md).

Při přesunu z nativního na MSIL si všimnete zvýšení velikosti pracovní sady. Důvodem je, že modul CLR (Common Language Runtime) poskytuje mnoho funkcí, které zajistí správné fungování programů. Pokud vaše aplikace **/CLR** neběží správně, možná budete chtít povolit C4793 (ve výchozím nastavení vypnuté), další informace najdete v tématu [Upozornění kompilátoru (úroveň 1 a 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) .

### <a name="program-crashes-on-shutdown"></a>Chyba programu při vypnutí

V některých případech může být modul CLR před spuštěním spravovaného kódu ukončen. Použití `std::set_terminate` a`SIGTERM` může to způsobit. Další [](../c-runtime-library/signal-constants.md) informace najdete v tématu konstanty signálů a [set_terminate](../c-runtime-library/abnormal-termination.md) .

## <a name="using-new-visual-c-features"></a>Používání nových vizuálních C++ funkcí

Po kompilaci, propojení a spuštění vaší aplikace můžete začít používat funkce .NET v jakémkoli modulu zkompilovaném pomocí **/CLR**. Další informace najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md).

Informace o programování .NET v vizuálu C++ najdete v tématech:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
