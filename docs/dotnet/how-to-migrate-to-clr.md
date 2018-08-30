---
title: 'Postupy: přechod na / clr | Dokumentace Microsoftu'
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
ms.openlocfilehash: 47914999a48b4d5924a25ad1688ee83c533398f3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218895"
---
# <a name="how-to-migrate-to-clr"></a>Postupy: Migrace do prostředí /clr
Toto téma popisuje problémy, které vznikají při kompilace nativního kódu s **/CLR** (viz [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) Další informace). **/ CLR** umožňuje moduly Visual C++ pro vyvolání a vyvolat z .NET sestavení při zachování kompatibility s nespravovanými moduly. Zobrazit [smíšený (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md) a [nativní a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md) Další informace o výhodách kompilace s **/CLR**.  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>Známé problémy kompilace projektů knihovny s parametrem/CLR  
 Visual Studio obsahuje některé známé problémy při kompilaci projektů knihovny s **/CLR**:  
  
-   Váš kód může dotazovat typů za běhu s [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Ale pokud je typ v DLL jazyk MSIL (zkompilovaná **/CLR**), volání `FromName` může selhat, pokud se vyskytuje před spuštěním statické konstruktory ve spravované knihovně DLL (nezobrazí tento problém v případě, že FromName volání se stane po kódu Spustí se ve spravované knihovně DLL). Chcete-li tento problém vyřešit, můžete vynutit konstrukce spravované statický konstruktor definující funkci ve spravované knihovně DLL, se exportováním a volání z nativní aplikace knihovny MFC. Příklad:  
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>Kompilace v jazyce Visual C++  
 Před použitím **/CLR** pro libovolný modul ve vašem projektu nejprve zkompilujte a propojte svůj nativní projekt pomocí sady Visual Studio 2010.  
  
 Následující kroky v pořadí, a potom zadejte nejsnadnější způsob, jak **/CLR** kompilace. Je důležité ke kompilaci a spuštění projektu po každé z těchto kroků.  
  
### <a name="versions-prior-to-visual-c-2003"></a>Verze starší než Visual C++ 2003  
 Pokud provádíte upgrade na sadu Visual Studio 2010 z verze před jazykem Visual C++ 2003, mohou se objevit chyby při kompilaci vztahující se k vylepšením standardního jazyka C++ v jazyce Visual C++ 2003.  
  
### <a name="upgrading-from-visual-c-2003"></a>Upgrade z Visual C++ 2003  
 Předchozí projekty sestavené pomocí jazyka Visual C++ 2003 by měl být nejprve zkompilován bez **/CLR** jako Visual Studio nyní vylepšuje shodu ANSI/ISO a odstraňuje některé narušující změny. Změna, která by mohla vyžadovat pozornost nejvíce [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md). Kód, který používá CRT je velmi pravděpodobné k vytvoření upozornění na zastarání. Tato upozornění může být potlačena, ale migrace na nový [verze funkcí CRT Security-Enhanced](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) je upřednostňována, protože poskytuje lepší zabezpečení a může odhalit problémy se zabezpečením ve vašem kódu.  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>Upgradování ze spravovaných rozšíření pro C++  
 Od verze Visual Studio 2005, v části nebude kompilovat kód napsaný se spravovaných rozšíření jazyka C++ **/CLR**.  
  
## <a name="convert-c-code-to-c"></a>Převést kód jazyka C do C++  
 Přestože sada Visual Studio zkompiluje soubory jazyka C, je nutné je převést na C++ pro **/CLR** kompilace. Skutečný název souboru nemusí být se změnily. můžete použít **/Tp** (viz [/Tc /Tp /TC, /TP (určení typu zdrojového souboru)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Všimněte si, že i když jsou požadovány pro zdrojové soubory C++ **/CLR**, není nutné kód Refaktorovat pro použití objektově orientovaných paradigmat.  
  
 Kód jazyka C je velmi pravděpodobně vyžadovat změny při kompilaci jako soubor jazyka C++. Bezpečnost typů pravidel C++ jsou striktní, takže převody typů musí být explicitní přetypování. Malloc – například vrátí ukazatel void, ale je možné přiřadit na ukazatel na libovolný typ v jazyce C přetypování:  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 Ukazatele na funkce jsou také výhradně zajišťující bezpečnost typů v jazyce C++, takže následující kód jazyka C vyžaduje změny. V jazyce C++ je nejlepší vytvořit `typedef` , který definuje typ ukazatele na funkci a pak pomocí tohoto typu přetypování ukazatele na funkce:  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C++ také vyžaduje, aby funkce buď prototypem nebo plně definovaná před jejich odkazované nebo vyvolána.  
  
 Identifikátory použitými v kódu jazyka C, které budou klíčová slova v jazyce C++ (například `virtual`, `new`, `delete`, `bool`, `true`, `false`atd) musí být přejmenován. Obecně to provést pomocí jednoduché operace hledání a nahrazování.  
  
 A konečně že explicitní použití atributu v tabulce vyžadují volání modelu COM ve stylu jazyka C a `this` ukazatele, C++ nepodporuje:  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>Překonfigurujte nastavení projektu  
 Jakmile se projekt zkompiluje a spustí v sadě Visual Studio 2010 měli vytvořit nové konfigurace projektu pro **/CLR** spíše než změnit výchozí konfigurace. **/ CLR** není kompatibilní s možnostmi kompilátoru a umožňuje vytvářet samostatné konfigurace sestavení projektu jako nativní nebo spravovaný. Když **/CLR** výběru v poli dialogové okno vlastností stránky, nastavení projektu není kompatibilní s **/CLR** jsou zakázány (a pokud nebudou automaticky obnovovat neaktivní možnosti   **/CLR** je následně nevybrané).  
  
### <a name="create-new-project-configurations"></a>Vytvořit nové konfigurace projektu  
 Můžete použít **Kopírovat nastavení z** možnost [nový projekt dialogové okno Konfigurace](https://msdn.microsoft.com/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) pro vytvoření konfigurace projektu na základě vaší stávající nastavení projektu. Proveďte jednou pro konfiguraci ladění a jednou pro konfiguraci vydané verze. Následné změny mohou být použijí se **/CLR** – pouze konkrétní konfigurace uživatele zůstanou nedotčena původní konfigurace projektu.  
  
 Projekty, které používají vlastní pravidla sestavení může vyžadovat pozornost.  
  
 Tento krok má vliv jiné projekty, které používají soubory pravidel. V tomto případě lze nakonfigurovat samostatnou cíl sestavení nebo verze, které jsou specifické pro **/CLR** kompilace lze vytvořit z kopii původní.  
  
### <a name="change-project-settings"></a>Změna nastavení projektu  
 **/ CLR** lze vybrat ve vývojovém prostředí pomocí pokynů v [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Jak už bylo zmíněno dříve, tento krok automaticky vypnout konfliktní nastavení projektu.  
  
> [!NOTE]
>  Při upgradu spravované knihovny nebo projektu webové služby z jazyka Visual C++ 2003, **/Zl** možnost kompilátoru bude přidána do **příkazového řádku** stránku vlastností. To způsobí, že LNK2001. Odebrat **/Zl** z **příkazového řádku** stránka vlastností řešení. Zobrazit [/Zl (vynechat název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) a [práce s vlastnostmi projektu](../ide/working-with-project-properties.md) Další informace. Nebo přidejte msvcrt.lib a msvcmrt.lib v linkeru **Další závislosti** vlastnost.  
  
 Pro projekty vytvořené pomocí souborů pravidel, nekompatibilní možnosti kompilátoru musí být zakázána ruční **/CLR** je přidána. Zobrazit /[/CLR – omezení](../build/reference/clr-restrictions.md) o – možnosti kompilátoru, které nejsou kompatibilní s **/CLR**.  
  
### <a name="precompiled-headers"></a>Předkompilované hlavičky  
 Předkompilované hlavičky jsou podporovány v rámci **/CLR**. Ale pokud pouze kompilovat některé z vašich souborů CPP s **/CLR** (zbytek jako nativní kompilace) některé změny se bude vyžadovat protože předkompilované hlavičky generuje s použitím **/CLR** nejsou kompatibilní s těmi vygeneruje bez **/CLR**. K této nekompatibilitě je vzhledem k tomu, že **/CLR** generuje a vyžaduje metadat. Moduly zkompilované **/CLR** proto nelze použít předkompilovaných hlaviček, které neobsahují metadata a to bez **/CLR** moduly nelze použít soubory předkompilovaných hlaviček, které neobsahují metadata.  
  
 Nejjednodušší způsob, jak sestavení projektu, kde jsou zkompilovány některé moduly **/CLR** je zcela zakázat předkompilovaných hlaviček. (V dialogovém okně stránky vlastností projektu, otevřete uzel jazyka C/C++ a vyberte předkompilované hlavičky. Změňte vlastnost vytvořit/použít předkompilovaných hlaviček na "Ne pomocí předkompilovaných hlaviček".)  
  
 Ale hlavně pro velké projekty, předkompilovaných hlaviček poskytuje mnohem lepší rychlost kompilace, takže zakázáním této funkce není žádoucí. V tomto případě je vhodné nakonfigurovat **/CLR** a jiných **/CLR** soubory používají samostatné předkompilované hlavičky. To můžete udělat v jednom kroku pomocí vyberete víc moduly se zkompiluje **/CLR** pomocí Průzkumníka řešení, kliknete pravým tlačítkem na skupinu a vybrat vlastnosti. Změňte vlastnosti soubor prostřednictvím PCH vytvořit/použít i předkompilovaný soubor hlaviček pro použití názvu souboru odlišnou hlavičku a soubor PCH.  
  
## <a name="fixing-errors"></a>Opravy chyb  
 Kompilace s **/CLR** může vést k chybám kompilátoru, linkeru nebo modul runtime. Tato část popisuje nejběžnější problémy.  
  
### <a name="metadata-merge"></a>Slučování metadat  
 Různé verze typů dat může způsobit linkeru se nezdařila, protože metadata generovaná pro dva typy neodpovídá. (To je obvykle nastává, když jsou členy typu podmíněně definovány, ale podmínky nejsou stejné pro všechny soubory CPP, které používají typ.) V tomto případě linkeru selže, pouze název symbolu a název druhý soubor OBJ, kde byl definován typ sestavy. Často je užitečné otočit pořadí, že odesílání souborů OBJ linkeru ke zjištění umístění jiné verze datového typu.  
  
### <a name="loader-lock-deadlock"></a>Zablokování zámku zaváděcího programu  
 V sadě Visual Studio 2010 a novější, můžete stále k "zámek zablokování zavaděč" jako v předchozích verzích se ale deterministické a je rozpoznáno a Ohlášeno za běhu. Zobrazit [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md) podrobné na pozadí, pokyny a řešení.  
  
### <a name="data-exports"></a>Export dat  
 Export dat knihovny DLL je náchylný a nedoporučuje se. Je to proto, že část dat knihovny DLL není zaručeno, že mají být inicializovány, dokud se provedla část spravované knihovny DLL. Odkazuje na metadata se [# direktiva using](../preprocessor/hash-using-directive-cpp.md).  
  
### <a name="type-visibility"></a>Viditelnost typů  
 Nativní typy jsou ve výchozím nastavení privátní. Výsledkem může být nativní typ není viditelný mimo knihovnu DLL. Tuto chybu vyřešit přidáním `public` pro tyto typy.  
  
### <a name="floating-point-and-alignment-issues"></a>Plovoucí desetinná čárka a zarovnání problémy  
 `__controlfp` nepodporuje modul common language runtime (viz [_control87 _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) Další informace). CLR také nerespektuje [zarovnat](../cpp/align-cpp.md).  
  
### <a name="com-initialization"></a>Inicializace modulu COM  
 Modul Common Language Runtime inicializuje COM automaticky při inicializaci modulu (když COM je automaticky inicializován dokončení tak jako MTA). Explicitní inicializace modelu COM v důsledku toho provede návratové kódy označující, že COM již byl inicializován. Pokus o explicitně inicializovat subsystém COM s jeden model vláken při CLR již inicializován COM k jinému modelu vláken může způsobit selhání aplikace.  
  
 Modul common language runtime spustí COM CLRTHREADATTRIBUTE ve výchozím nastavení; použít [/CLRTHREADATTRIBUTE (nastavit atribut modulu CLR vlákno)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) ji měnit.  
  
### <a name="performance-issues"></a>Problémy s výkonem  
 Při volání nepřímo nativní metody jazyka C++, které jsou generovány do jazyka MSIL, může se zobrazit sníženým výkonem (volání virtuální funkce nebo pomocí ukazatele na funkce). Další informace o tom najdete v tématu [dvojitému](../dotnet/double-thunking-cpp.md).  
  
 Při přesunu z nativní do jazyka MSIL, si všimnete zvýšení velikost pracovní sady. Je to proto, že modul common language runtime obsahuje mnoho funkcí pro zajištění, že programy běží správně. Pokud vaše **/CLR** aplikace není spuštěna správně, můžete chtít povolit C4793 (ve výchozím nastavení vypnuté), najdete v článku [upozornění kompilátoru (úroveň 1 a 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) Další informace.  
  
### <a name="program-crashes-on-shutdown"></a>Chyby programu při ukončení  
 V některých případech můžete CLR vypnutí před dokončením spravovaný kód spuštěn. Pomocí `std::set_terminate` a `SIGTERM` to může způsobit. Zobrazit [signal – konstanty](../c-runtime-library/signal-constants.md) a [set_terminate](../c-runtime-library/abnormal-termination.md) Další informace.  
  
## <a name="using-new-visual-c-features"></a>Pomocí nové funkce Visual C++  
 Po aplikaci zkompiluje, odkazy a spuštění, můžete začít používat funkce rozhraní .NET v jakékoli Modul zkompilovaný pomocí **/CLR**. Další informace najdete v tématu [přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).  
  
 Pokud jste použili spravovaných rozšíření jazyka C++, můžete převést kód Refaktorovat pro použití nové syntaxe. Podrobnosti o převodu spravovaných rozšíření jazyka C++, naleznete v tématu [C + +/ CLI Základy migrace](../dotnet/cpp-cli-migration-primer.md).  
  
 Informace o programování v jazyce Visual C++ .NET naleznete v tématu:  
  
-   [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)