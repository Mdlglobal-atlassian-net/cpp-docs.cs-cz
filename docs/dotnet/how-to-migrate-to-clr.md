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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376069"
---
# <a name="how-to-migrate-to-clr"></a>Postupy: Migrace do prostředí /clr

Toto téma popisuje problémy, které vznikají při kompilaci nativního kódu s **/clr** (viz [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) pro další informace). **/clr** umožňuje nativní kód Jazyka C++ vyvolat a vyvolat z sestavení .NET kromě jiného nativního kódu Jazyka C++. Další informace o výhodách kompilace s **parametrem /clr**naleznete v tématu [Smíšené (nativní a spravované) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) [a nativní a .NET interoperability.](../dotnet/native-and-dotnet-interoperability.md)

## <a name="known-issues-compiling-library-projects-with-clr"></a>Známé problémy kompilace projektů knihovny s /clr

Visual Studio obsahuje některé známé problémy při kompilaci projektů knihovny s **/clr**:

- Váš kód může dotazovat typy za běhu s [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Pokud je však typ v msil .dll (kompilován s `FromName` **/clr**), volání může selhat, pokud dojde před spuštěním statických konstruktorů ve spravované mll (tento problém se nezobrazí, pokud dojde k volání FromName po spuštění kódu ve spravované mll). Chcete-li tento problém vyřešit, můžete vynutit konstrukci spravovaného statického konstruktoru definováním funkce ve spravované knihovně DLL, exportem a vyvoláním z nativní aplikace knihovny MFC. Příklad:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompilace v jazyce Visual C++

Před použitím **/clr** na libovolném modulu v projektu nejprve zkompilujte a propojte nativní projekt s Visual Studio 2010.

Následující kroky, postupujte v pořadí, poskytují nejjednodušší cestu k **/clr** kompilace. Je důležité zkompilovat a spustit projekt po každém z těchto kroků.

### <a name="versions-prior-to-visual-studio-2003"></a>Verze před visual studio 2003

Pokud upgradujete na Visual Studio 2010 z verze před Visual Studio 2003, může se zobrazit chyby kompilátoru související s rozšířenou shody standardu C++ v sadě Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Inovace z aplikace Visual Studio 2003

Projekty předchozí sestavení s Visual Studio 2003 by měl y také nejprve zkompilovat bez **/clr** jako Visual Studio nyní zvýšila ansi/ISO dodržování předpisů a některé změny. Změna, která bude pravděpodobně vyžadovat největší pozornost, je [funkce zabezpečení v crt](../c-runtime-library/security-features-in-the-crt.md). Kód, který používá CRT je velmi pravděpodobné, že k vytvoření upozornění vyřazení. Tato upozornění lze potlačit, ale migrace na nové [verze funkce CRT rozšířené zabezpečení](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) je upřednostňována, protože poskytují lepší zabezpečení a může odhalit problémy se zabezpečením ve vašem kódu.

### <a name="upgrading-from-managed-extensions-for-c"></a>Inovace ze spravovaných rozšíření pro C++

Počínaje Visual Studio 2005, kód napsaný s spravovanými rozšířeními pro C++ nebude kompilovat pod **/clr**.

## <a name="convert-c-code-to-c"></a>Převod kódu C na c++

Přestože Visual Studio bude kompilovat soubory C, je nutné je převést na C++ pro **/clr** kompilace. Skutečný název souboru nemusí být změněn; můžete použít **/Tp** (viz [/Tc, /Tp, /TC, /TP (Zadat typ zdrojového souboru)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Všimněte si, že i když c++ soubory zdrojového kódu jsou požadovány pro **/clr**, není nutné re-faktor váš kód použít objektově orientované paradigmata.

Kód Jazyka C je velmi pravděpodobné, že vyžadují změny při kompilaci jako soubor Jazyka C++. Pravidla zabezpečení typu C++ jsou přísná, takže převody typů musí být explicitní s přetypátky. Například malloc vrátí ukazatel void, ale může být přiřazen k ukazateli libovolného typu v C s přetypátkem:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Ukazatele funkce jsou také přísně typově bezpečné v jazyce C++, takže následující kód C vyžaduje úpravy. V jazyce C++ je `typedef` nejlepší vytvořit a, který definuje typ ukazatele funkce a pak použít tento typ k přetypování ukazatele funkce:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ také vyžaduje, aby funkce byly prototypovány nebo plně definovány předtím, než na ně lze odkazovat nebo vyvolat.

Identifikátory používané v kódu Jazyka C, které jsou náhodou klíčovými slovy v jazyce C++ (například **virtuální**, **nové**, **odstranit**, **bool**, **pravda**, **false**, atd.) musí být přejmenovány. To lze obecně provést pomocí jednoduchých operací vyhledávání a nahrazování.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Změna konfigurace nastavení projektu

Po projektu zkompiluje a spustí v sadě Visual Studio 2010 byste měli vytvořit nové konfigurace projektu pro **/clr** spíše než úpravy výchozí konfigurace. **/clr** není kompatibilní s některými možnostmi kompilátoru a vytváření samostatných konfigurací umožňuje vytvořit projekt jako nativní nebo spravované. Pokud je v dialogovém okně stránky vlastností vybrána možnost **/clr,** nastavení projektu, které není kompatibilní s **parametrem /clr,** je zakázáno (a zakázané možnosti nejsou automaticky obnoveny, pokud není vybrána možnost **/clr).**

### <a name="create-new-project-configurations"></a>Vytvořit nové konfigurace projektu

**Pomocí možnosti Kopírovat nastavení z** v **dialogovém okně Konfigurace nového projektu** **(Sestavení** > konfigurace správce**aktivní** > **New****konfigurace** > nové) můžete vytvořit konfiguraci projektu na základě stávajícího nastavení projektu. Udělejte to jednou pro konfiguraci ladění a jednou pro konfiguraci release. Následné změny pak lze použít pouze pro konfigurace **/clr-specific,** takže původní konfigurace projektu beze změny.

Projekty, které používají vlastní sestavení pravidla může vyžadovat zvláštní pozornost.

Tento krok má různé důsledky pro projekty, které používají makefiles. V tomto případě lze nakonfigurovat samostatný cíl sestavení nebo lze vytvořit verzi specifickou pro kompilaci **/clr** z kopie originálu.

### <a name="change-project-settings"></a>Změna nastavení projektu

**/clr** lze vybrat ve vývojovém prostředí podle pokynů v [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md). Jak již bylo zmíněno dříve, tento krok automaticky zakáže konfliktní nastavení projektu.

> [!NOTE]
> Při inovaci spravované knihovny nebo projektu webové služby z aplikace Visual Studio 2003 bude na stránku vlastností **příkazového řádku** přidána možnost kompilátoru **/Zl.** To způsobí LNK2001. Odeberte **/Zl** ze stránky vlastností **příkazového řádku,** kterou chcete vyřešit. Další informace naleznete [v tématech /Zl (Vynechání výchozího názvu knihovny)](../build/reference/zl-omit-default-library-name.md) a [Nastavení vlastností kompilátoru a sestavení.](../build/working-with-project-properties.md) Nebo přidejte msvcrt.lib a msvcmrt.lib do další **chodproponu** vlastnost.

Pro projekty vytvořené s makefiles, nekompatibilní možnosti kompilátoru musí být zakázány ručně po **/clr** je přidán. Viz /[/clr Omezení](../build/reference/clr-restrictions.md) pro informace o možnostech kompilátoru, které nejsou kompatibilní s **/clr**.

### <a name="precompiled-headers"></a>Předkompilované hlavičky

Předkompilované hlavičky jsou podporovány pod **/clr**. Pokud však zkompilujete pouze některé soubory CPP s **/clr** (kompilace zbytek jako nativní), budou nutné některé změny, protože předkompilované hlavičky generované **/clr** nejsou kompatibilní s těmi, které jsou generovány bez **/clr**. Tato nekompatibilita je způsobena skutečností, že **/clr** generuje a vyžaduje metadata. Moduly zkompilované **/clr** proto nelze použít předkompilované hlavičky, které neobsahují metadata, a non **/clr** moduly nelze použít předkompilované hlavičkové soubory, které obsahují meta data.

Nejjednodušší způsob, jak zkompilovat projekt, kde jsou některé moduly kompilovány **/clr** je zakázat předkompilované hlavičky úplně. (V dialogovém okně Stránky vlastností projektu otevřete uzel C/C++ a vyberte Předkompilovaná záhlaví. Potom změňte vlastnost Vytvořit/použít předkompilované hlavičky na "Nepoužívat předkompilované hlavičky".)

Zejména u velkých projektů však předkompilované hlavičky poskytují mnohem lepší rychlost kompilace, takže zakázání této funkce není žádoucí. V tomto případě je nejlepší nakonfigurovat **soubory /clr** a non **/clr** tak, aby používaly samostatné předkompilované hlavičky. To lze provést v jednom kroku více násobné výběru modulů, které mají být kompilovány **/clr** pomocí **Průzkumníka řešení**, kliknutí pravým tlačítkem myši na skupinu a výběrem vlastnosti. Potom změňte vlastnosti Vytvořit/použít PCH prostřednictvím souboru a Předkompilovaný soubor záhlaví, abyste použili jiný název souboru záhlaví a soubor PCH.

## <a name="fixing-errors"></a>Oprava chyb

Kompilace s **/clr** může mít za následek chyby kompilátoru, propojovacího nebo runtime. Tato část popisuje nejčastější problémy.

### <a name="metadata-merge"></a>Sloučení metadat

Různé verze datových typů může způsobit propojovací ho nezdaře, protože metadata vygenerovaná pro tyto dva typy se neshodují. (To je obvykle způsobeno, když jsou členové typu podmíněně definováni, ale podmínky nejsou stejné pro všechny soubory CPP, které používají typ.) V tomto případě propojovací systém selže, vykazování pouze název symbolu a název druhého souboru OBJ, kde byl definován typ. Často je užitečné otočit pořadí, ve které jsou soubory OBJ odesílány do linkeru, aby bylo možné zjistit umístění jiné verze datového typu.

### <a name="loader-lock-deadlock"></a>Zablokování zámku zavaděče

"Zavaděč zablokování uzamčení" může dojít, ale je deterministický a je zjištěna a hlášena za běhu. Podrobné informace o pozadí, pokyny a řešení najdete [v tématu Inicializace smíšených sestavení.](../dotnet/initialization-of-mixed-assemblies.md)

### <a name="data-exports"></a>Exportdat

Export dat dll je náchylný k chybám a nedoporučuje se. Důvodem je, že část dat dll není zaručeno, že bude inicializována, dokud některé spravované části DLL byla provedena. Referenční metadata s [#using směrnice](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Viditelnost typů

Nativní typy jsou ve výchozím nastavení soukromé. To může mít za následek nativní typ není viditelné mimo DLL. Vyřešit tuto `public` chybu přidáním těchto typů.

### <a name="floating-point-and-alignment-issues"></a>Problémy s plovoucí desetinnou a vyrovnávací pořazovací

`__controlfp`není podporována v modulu runtime společného jazyka (další informace naleznete [v _control87, _controlfp _control87_2). \_](../c-runtime-library/reference/control87-controlfp-control87-2.md) CLR také nebude respektovat [zarovnat](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicializace com

Modul Common Language Runtime inicializuje com automaticky při inicializaci modulu (při automatické inicializaci com se provádí tak, jak MTA). V důsledku toho explicitně inicializace com výnosy návratové kódy označující, že COM je již inicializována. Pokus o explicitní inicializaci modelu COM s jedním modelem podprocesu, když clr již inicializoval com na jiný model podprocesu může způsobit selhání aplikace.

Běžný jazyk runtime spustí COM jako MTA ve výchozím nastavení; použijte [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) k úpravě tohoto.

### <a name="performance-issues"></a>Problémy s výkonem

Může se zobrazit snížený výkon při nativní metody Jazyka C++ generované msil jsou volány nepřímo (volání virtuální funkce nebo pomocí ukazatelů funkce). Další informace naleznete v [tématu Double Thunking](../dotnet/double-thunking-cpp.md).

Při přechodu z nativní do MSIL, všimnete si zvýšení velikosti pracovní sady. Důvodem je, že běžný jazyk runtime poskytuje mnoho funkcí, které zajišťují, že programy běží správně. Pokud vaše **/clr** aplikace není spuštěna správně, můžete chtít povolit C4793 (vypnuto ve výchozím nastavení), naleznete v [tématu upozornění kompilátoru (úroveň 1 a 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) další informace.

### <a name="program-crashes-on-shutdown"></a>Program havaruje při vypnutí

V některých případech clr můžete vypnout před dokončením spuštění spravovaného kódu. Použití `std::set_terminate` `SIGTERM` a může způsobit toto. Další informace naleznete [v tématu Konstanty signálu](../c-runtime-library/signal-constants.md) a [set_terminate.](../c-runtime-library/abnormal-termination.md)

## <a name="using-new-visual-c-features"></a>Použití nových funkcí visual c++

Po kompilaci, propojení a spuštění aplikace můžete začít používat funkce rozhraní .NET v libovolném modulu kompilovaném pomocí **parametru /clr**. Další informace naleznete [v tématu Rozšíření součástí pro platformy runtime](../extensions/component-extensions-for-runtime-platforms.md).

Informace o programování rozhraní .NET ve visual c++ naleznete v tématu:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
