---
title: 'Postupy: migrace na - clr | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5d7dafdc377723e33372529af1b8f125561366e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-to-clr"></a>Postupy: Migrace do prostředí /clr
Toto téma popisuje problémy, které se vynoří během kompilace nativního kódu s **/CLR** (viz [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) informace). **/ CLR** umožňuje modulům Visual C++ pro vyvolání a jde volat z sestavení .NET a přitom zachovat kompatibilitu s nespravovanými moduly. V tématu [Mixed (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a interoperabilitě .NET](../dotnet/native-and-dotnet-interoperability.md) Další informace o výhodách kompilace s **/CLR**.  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>Známé problémy kompilace projektů knihovny s volbou/CLR  
 Visual Studio obsahuje některé známé problémy při kompilaci projektů knihovny s **/CLR**:  
  
-   Váš kód může dotazovat typy za běhu s [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Ale pokud je typ v MSIL .dll (Kompilovat s **/CLR**), volání `FromName` může selhat, pokud se vyskytuje před spuštěním statických konstruktorů ve spravované knihovně DLL (neuvidíte tento problém případě že FromName volání po kód spustit v spravované .dll). Chcete-li tento problém obejít, můžete vynutit konstrukce spravované statického konstruktoru definováním funkci ve spravované knihovně DLL, export ho a volání z nativní aplikace MFC. Příklad:  
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>Kompilace v jazyce Visual C++  
 Před použitím **/CLR** na libovolném modulu ve vašem projektu, první kompilace a propojení projektu nativní sadou Visual Studio 2010.  
  
 Následující kroky, a potom v pořadí, poskytují nejjednodušší cesta k **/CLR** kompilace. Je důležité pro zkompilování a spuštění projektu po každém z těchto kroků.  
  
### <a name="versions-prior-to-visual-c-2003"></a>Verze starší než Visual C++ 2003  
 Pokud provádíte upgrade na sadu Visual Studio 2010 z verze před jazykem Visual C++ 2003, mohou se objevit chyby při kompilaci vztahující se k vylepšením standardního jazyka C++ v jazyce Visual C++ 2003.  
  
### <a name="upgrading-from-visual-c-2003"></a>Upgrade z aplikace Visual C++ 2003  
 Předchozí projekty vytvořené pomocí Visual C++ 2003 musí být nejprve kompilovány bez **/CLR** jako Visual Studio teď má vyšší ANSI/ISO dodržování předpisů a některé dodatečné změny. Změna, která bude pravděpodobně vyžadovat největší pozornost je [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md). Kód, který používá CRT je velmi pravděpodobně produkuje odmítání upozornění. Tato upozornění mohou být potlačena, ale přenesení do nového [verze funkcí CRT Security-Enhanced](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) je preferovaná, protože poskytuje lepší zabezpečení a může odhalit problémy se zabezpečením v kódu.  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>Upgradování ze spravovaných rozšíření pro C++  
 Od verze Visual Studio 2005, v části nebude zkompilovat kód zapisovaný s spravovaných rozšíření pro C++ **/CLR**.  
  
## <a name="convert-c-code-to-c"></a>Převést C – kód jazyka C++  
 I když Visual Studio zkompiluje soubory C, je nutné je převést na C++ pro **/CLR** kompilace. Skutečný název souboru nemá změnit; můžete použít **/Tp** (viz [/Tc, /Tp /TC, /TP (zadejte zdrojový soubor typu)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Všimněte si, že i když jsou požadovány pro soubory zdrojového kódu C++ **/CLR**, není nutné používat objektově orientované vzorů kódu.  
  
 C – kód je velmi pravděpodobně vyžadovat změny při kompilaci jako soubor jazyka C++. Zabezpečení typů pravidel C++ jsou striktní, takže převody typu musí být explicitní přetypování. Malloc – například vrací neplatný ukazatel, ale lze přiřadit k ukazatel na všech typů v jazyce C přetypování:  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 Ukazatele na funkce jsou také výhradně zajišťující bezpečnost typů v jazyce C++, takže následující kód C vyžaduje úpravu. V jazyce C++ je nejlepší vytvořit `typedef` , definuje typ ukazatele funkce a potom k přetypování ukazatelů na funkce pomocí typu:  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C++ také vyžaduje, aby funkce buď deklaraci nebo plně definované před jejich odkazuje nebo vyvolána.  
  
 Identifikátory používané v kódu jazyka C, které mají být klíčová slova v jazyce C++ (například `virtual`, `new`, `delete`, `bool`, `true`, `false`atd) musí být přejmenován. Obecně to lze provést pomocí jednoduché operace hledání a nahrazování.  
  
 Nakonec zatímco volání COM stylu jazyka C vyžaduje explicitní použití tabulky v a `this` ukazatele, C++ nepodporuje:  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>Znovu nakonfigurujte nastavení projektu  
 Po projektu kompilaci a spuštění v sadě Visual Studio 2010 měli vytvořit nové konfigurace projektu pro **/CLR** místo změnu výchozí konfigurace. **/ CLR** není kompatibilní s možnostmi kompilátoru a umožňuje vytvoření samostatné konfigurace sestavení projektu jako nativní nebo spravovaný. Když **/CLR** je vybraný v vlastnost stránky dialogového okna, nastavení projektu není kompatibilní s **/CLR** jsou zakázány (a neaktivní možnosti nejsou obnoveny automaticky, pokud **/CLR** je následně nezaškrtnuté).  
  
### <a name="create-new-project-configurations"></a>Vytvořit nové konfigurace projektu  
 Můžete použít **Kopírovat nastavení z** možnost [nový projekt dialogové okno Konfigurace](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) pro vytvoření konfigurace projektu na základě vaší stávající nastavení projektu. K tomu jednou pro konfiguraci ladění a jednou pro konfigurace verze. Další změny, které mohou být použity pak k **/CLR** -pouze konkrétní konfigurace ponechá původní konfigurace projektu beze změn.  
  
 Projekty, které používají vlastní pravidla sestavení mohou vyžadovat zvláštní pozornost.  
  
 Tento krok obsahuje různé důsledky pro projekty, které používají soubory pravidel. V tomto případě lze nakonfigurovat samostatné cíl sestavení nebo verze, které jsou specifické pro **/CLR** kompilace lze vytvořit z kopie původní.  
  
### <a name="change-project-settings"></a>Změna nastavení projektu  
 **/ CLR** lze vybrat ve vývojovém prostředí podle pokynů v [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Jak je uvedeno nahoře, tento krok automaticky zakáže konfliktní nastavení projektu.  
  
> [!NOTE]
>  Při upgradu spravované knihovny nebo projektu webové služby z Visual C++ 2003 **/Zl** možnost kompilátoru bude přidána do **příkazového řádku** stránku vlastností. To způsobí, že LNK2001. Odebrat **/Zl** z **příkazového řádku** stránka vlastností řešení. V tématu [/Zl (vypuštění název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) a [práce s vlastnostmi projektu](../ide/working-with-project-properties.md) Další informace. Nebo přidat msvcrt.lib a msvcmrt.lib linkeru **Další závislosti** vlastnost.  
  
 Pro projekty vytvořené pomocí soubory pravidel, nekompatibilní možnosti kompilátoru musí být zakázána ruční **/CLR** je přidána. V tématu nebo[/CLR – omezení](../build/reference/clr-restrictions.md) informace o možnostech kompilátoru, která nejsou kompatibilní s **/CLR**.  
  
### <a name="precompiled-headers"></a>Předkompilované hlavičky  
 Předkompilované hlavičky jsou podporovány v rámci **/CLR**. Ale pokud pouze zkompilujete některé ze souborů CPP s **/CLR** (kompilování zbytku jako nativní) některé změny se bude vyžadovat protože předkompilovaných hlaviček vygeneroval s **/CLR** nejsou kompatibilní s těmi, generuje bez **/CLR**. Tato nekompatibilita je vzhledem k tomu, že **/CLR** generuje a vyžaduje metadata. Kompilované moduly **/CLR** proto nelze použít předkompilovaných hlaviček, které neobsahují metadata a to bez **/CLR** moduly nemůžete použít soubory předkompilovaných hlaviček, které neobsahují metadata.  
  
 Nejjednodušší způsob, jak sestavení projektu, kde jsou některé moduly zkompilovány **/CLR** je zcela zakázat předkompilovaných hlaviček. (V dialogovém okně stránky vlastností projektu, otevřete uzel C/C++ a zvolte předkompilované hlavičky. Změňte vlastnost vytvoření/použití předkompilovaných hlaviček na "Není použití předkompilovaných hlaviček".)  
  
 Ale hlavně pro velké projekty předkompilovaných hlaviček poskytovat mnohem lepší rychlost kompilace, takže zakázáním této funkce není žádoucí. V takovém případě je nejlepší konfigurovat **/CLR** a **/CLR** pro použití předkompilovaných hlaviček samostatné souborů. To lze provést v jednom kroku pomocí vyberete víc modulů, které mají být zkompilovány, do **/CLR** pomocí Průzkumníku řešení pravým tlačítkem myši na skupinu a vyberte možnost Vlastnosti. Vytvořit nebo použít PCH prostřednictvím soubor i předkompilovaný hlavičkový soubor vlastnosti na používání jiné záhlaví název souboru a soubor PCH potom změňte.  
  
## <a name="fixing-errors"></a>Opravy chyb  
 Kompilování pomocí **/CLR** může vést k chybám kompilátoru, linkeru nebo modul runtime. Tato část popisuje nejběžnější problémy.  
  
### <a name="metadata-merge"></a>Metadat sloučení  
 Různé verze typů dat může způsobit linkeru se nezdařila, protože metadata vygenerované dva typy neodpovídá. (To je obvykle způsobeno při členy typu jsou podmíněně definovány, ale podmínky nejsou stejné pro všechny soubory CPP, které používají typ.) V takovém případě linkeru selže, vytváření sestav jenom názvu symbolu a název souboru druhý OBJ, kde byl typ definovaný. Často je užitečné otočit pořadí, že soubory OBJ jsou odesílány linkeru o zjištění polohy verze datového typu.  
  
### <a name="loader-lock-deadlock"></a>Načítání vzájemného zablokování  
 V sadě Visual Studio 2010 a novější, "načítání vzájemného zablokování" stále může dojít k jako ve starších verzích, ale je deterministická a je zjištěn a uvedeno za běhu. V tématu [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md) pro podrobné pozadí, pokyny a řešení.  
  
### <a name="data-exports"></a>Export dat  
 Export knihoven DLL dat je k chybám a nedoporučuje se. Je to proto, že není zaručeno, že část dat knihovny DLL inicializace dokud provedl některé spravovaných část knihovny DLL. Metadata odkaz s [#using – direktiva](../preprocessor/hash-using-directive-cpp.md).  
  
### <a name="type-visibility"></a>Viditelnost typů  
 Nativní typy jsou ve výchozím nastavení soukromá. To může způsobit v nativním typu nebude viditelné mimo knihovnu DLL. Tuto chybu vyřešit přidáním `public` na tyto typy.  
  
### <a name="floating-point-and-alignment-issues"></a>Plovoucí desetinná čárka a přidružené problémy.  
 `__controlfp` není podporována na modul common language runtime (viz [_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) Další informace). Modul CLR také nerespektuje [zarovnat](../cpp/align-cpp.md).  
  
### <a name="com-initialization"></a>Inicializace modulu COM  
 Modul Common Language Runtime Automatická inicializace při inicializaci modulu (když je automaticky inicializován COM je provedeno tak v modelu MTA). V důsledku toho explicitně inicializace COM vytváří návratové kódy označující, že COM již je inicializován. Probíhá pokus o inicializaci výslovně COM s jeden model vláken při modulu CLR byla inicializována COM již pro jiný model vláken může způsobit selhání aplikace.  
  
 Modul common language runtime spustí COM v modelu MTA ve výchozím nastavení; použít [/CLRTHREADATTRIBUTE (nastavit CLR vláken atribut)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) tuto možnost lze upravit.  
  
### <a name="performance-issues"></a>Problémy s výkonem  
 Mohou se zobrazit snížený výkon, pokud nativní C++ metody generována do MSIL jsou volány nepřímo (virtuální funkce volání nebo pomocí ukazatele na funkce). Další informace o tom najdete v tématu [dvojitý převod adres](../dotnet/double-thunking-cpp.md).  
  
 Při přesouvání z nativní na MSIL, si všimnete zvýšit velikost pracovní sady. Je to proto, že modul common language runtime poskytuje množství funkcí, které Ujistěte se, že programy běží správně. Pokud vaše **/CLR** aplikace není spuštěna správně, můžete chtít povolit C4793 (ve výchozím nastavení vypnuté), najdete v části [upozornění kompilátoru (úroveň 1 a 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) Další informace.  
  
### <a name="program-crashes-on-shutdown"></a>Chyba programu během vypnutí  
 V některých případech modulu CLR může vypnutí před dokončením spravovaného kódu systémem. Pomocí `std::set_terminate` a `SIGTERM` může způsobit to. V tématu [signal – konstanty](../c-runtime-library/signal-constants.md) a [set_terminate –](../c-runtime-library/abnormal-termination.md) Další informace.  
  
## <a name="using-new-visual-c-features"></a>Použití nových funkcí Visual C++  
 Po aplikaci zkompiluje, odkazy a běží, můžete začít používat funkce rozhraní .NET v jakémkoliv kompilovaném modulu s **/CLR**. Další informace najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).  
  
 Pokud jste použili spravovaných rozšíření jazyka C++, můžete převést kód a použít nové syntaxe. Podrobnosti o převodu spravovaných rozšíření pro C++ najdete v tématu [C + +/ CLI migrace Úvod do](../dotnet/cpp-cli-migration-primer.md).  
  
 Informace o programování v jazyce Visual C++ .NET najdete v části:  
  
-   [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)