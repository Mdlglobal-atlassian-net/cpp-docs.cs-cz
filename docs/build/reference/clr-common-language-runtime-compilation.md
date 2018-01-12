---
title: -clr (kompilace Common Language Runtime) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: "72"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a867203585a66bd07eb9f95e289557e82e0553a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Common Language Runtime)
Umožňuje aplikací a součástí, které chcete používat funkce z common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>Arguments  
 `options`  
 Jeden nebo více z následujících parametrů, oddělených čárkami.  
  
 **/ CLR**  
 Vytvoří metadata pro aplikaci. Metadata mohou být spotřebovávána jiné aplikace CLR a umožňuje aplikaci používat typy a data v metadatech součásti CLR.  
  
 Další informace naleznete v tématu  
  
 [Smíšená (nativní a spravovaná) sestavení](../../dotnet/mixed-native-and-managed-assemblies.md) a  
  
 [Postupy: přechod na/CLR](../../dotnet/how-to-migrate-to-clr.md).  
  
 **/ CLR: pure**  
 Vytvoří zprostředkující jazyka Microsoft (MSIL) – jenom výstupního souboru, který nemá žádné nativní spustitelný kód. Může ale obsahovat nativní typy zkompilovány do MSIL.  
  
 Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 / CLR: pure je zastaralý. V budoucích verzích kompilátor nemusí podporovat tuto možnost. Doporučujeme vám, že je port kód, který musí být čistá MSIL jazyka C#.  
  
 **/ CLR: safe**  
 Vytvoří MSIL jen (žádné nativní spustitelný kód), ověřitelný výstupní soubor. **/ CLR: safe** umožňuje ověření diagnostiky ([Nástroj PEVerify (Peverify.exe)](/dotnet/framework/tools/peverify-exe-peverify-tool)).  
  

 / CLR: safe je zastaralý. V budoucích verzích kompilátor nemusí podporovat tuto možnost. Doporučujeme vám, že je port kód, který musí být čistá, ověřitelný MSIL jazyka C#.  
  
 **/CLR:noAssembly**  
 Určuje, že manifest sestavení by neměly být vložen do výstupního souboru. Ve výchozím nastavení **noAssembly** možnost není platný.  
  
 **NoAssembly** parametr se již nepoužívá. Použití [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md) místo.  
  
 Spravovaný program, který nemá metadata sestavení v manifestu se označuje jako *modulu*. **NoAssembly** možnost lze použít pouze k vytvoření modulu. Pokud zkompilujete pomocí [/c](../../build/reference/c-compile-without-linking.md) a **/clr:noAssembly**, zadejte [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) možnost ve fázi linkeru Vytvořte modul.  
  
 Před Visual C++ 2005 **/clr:noAssembly** požadované **/LD**. **/LD** je nyní zahrnuta, když zadáte **/clr:noAssembly**.  
  
 **/ CLR: initialAppDomain**  
 Umožňuje [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] spuštění aplikace v 1 verzi modulu CLR. Pokud používáte **initialAppDomain**, pak může v některé z problémů, které jsou popsané v tématu [chyb: AppDomainUnloaded výjimka při použití spravovaná rozšíření pro Visual C++ součásti](http://go.microsoft.com/fwlink/p/?linkid=169465) na Microsoft Web podpory.  
  
 Aplikace, který se zkompiluje pomocí **initialAppDomain** by se nemělo používat aplikaci, která používá technologii ASP.NET, protože není podporována v 1 verzi modulu CLR.  
  
 **/CLR:nostdlib**  
 Dá pokyn kompilátoru ignorovat \clr výchozí adresář. Kompilátor vytváří chyby, pokud jsou včetně několik verzí knihovny DLL, jako je například System.dll. Pomocí této možnosti můžete zadat konkrétní framework pro použití během kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Spravovaný kód je kód, který může být prověřovány a spravuje modulu CLR. Spravovaný kód k přístup spravovaných objektů. Další informace najdete v tématu [/CLR – omezení](../../build/reference/clr-restrictions.md).  
  
 Informace o tom, jak vyvíjet aplikace, které definice a používání spravované typy najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Aplikace, kompilovat s použitím **/CLR** může nebo nemusí obsahovat spravovaná data.  
  
 Pokud chcete povolit ladění na spravované aplikace, najdete v části [/ASSEMBLYDEBUG (přidat atribut DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).  
  
 Bude vytvořena instance pouze typy v haldě uvolňování paměti. Další informace najdete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md). Kompilace funkce, která se nativního kódu, použijte `unmanaged` – Direktiva pragma. Další informace najdete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md).  
  
 Ve výchozím nastavení **/CLR** není funkční. Když **/CLR** je v platnosti **/MD** platí také. Další informace najdete v tématu [/MD, / MT, /LD (použít běhovou knihovnu)](../../build/reference/md-mt-ld-use-run-time-library.md). **/MD** zajistí, že jsou vybrány dynamicky propojené s více vlákny verzích rutiny modulu runtime ze souborů standardní hlavičky (). Multithreading je vyžadována spravované programování vzhledem k tomu má systém uvolňování CLR běží finalizační metody v pomocného podprocesu.  
  
 Pokud zkompilujete pomocí **/c**, můžete zadat typ CLR (IJW, sejfu nebo používáte čistý) výsledný výstupní soubor s [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **/ CLR** znamená **/EHa**a ne dalších **/EH** možnosti jsou podporovány pro **/CLR**. Další informace najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md).  
  
 Informace o tom, jak určit typ obrázku CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).  
  
 Předaný dané vyvolání linkeru všechny moduly musí být zkompilovány pomocí stejné knihovna RTL – možnost kompilátoru (**/MD** nebo **/LD**).  
  
 Použití [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) – možnost linkeru pro vložení do sestavení prostředku. [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md), a [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) možnosti linkeru vám také umožní přizpůsobit vytváření sestavení.  
  
 Když **/CLR** se používá, `_MANAGED` symbol je definována musí být 1. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).  
  
 Globální proměnné v souboru nativní objekt se inicializují první (během zpracování funkce DllMain Pokud spustitelný soubor knihovny DLL) a globální proměnné v části spravované se inicializují (před spouští spravovaný kód). `#pragma`[init_seg –](../../preprocessor/init-seg.md) ovlivňuje pouze pořadí inicializace spravovanými a nespravovanými kategorií.  
  
 Kompilování pomocí **/CLR: safe** je podobná kompilace pomocí [/platform:anycpu](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option) v jazyků, například C#.  
  
## <a name="safe-and-pure-images"></a>Bezpečnost a čistý bitové kopie  
 Čistý image používá verze CLR knihovny C Runtime (CRT). CRT však není ověřitelný, a proto CRT nelze použít, když zkompilujete pomocí **/CLR: safe**. Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
 Příklady nativního kódu, který nelze vložit do bitové kopie čistá sestavení inline assemblerem [setjmp](../../c-runtime-library/reference/setjmp.md), a [longjmp](../../c-runtime-library/reference/longjmp.md).  
  
 Každý vstupní bod čistý nebo sejfu bitové kopie je spravovaný. Když zkompilujete pomocí **/CLR**, vstupní bod je nativní. Další informace najdete v tématu [__clrcall](../../cpp/clrcall.md).  
  
 Když zkompilujete pomocí **/CLR: safe**, ve výchozím nastavení, proměnné jsou [appdomain](../../cpp/appdomain.md) a nemůže být na proces. Pro **/CLR: pure**, i když **appdomain** je výchozí nastavení, můžete použít [proces](../../cpp/process.md) proměnné.  
  
 Při spuštění souboru .exe 32-bit, které bylo kompilováno s použitím **/CLR** nebo **/CLR: pure** na 64bitový operační systém, bude aplikace spuštěna pod WOW64, která umožňuje 32bitová aplikace ke spuštění na 32-bit CLR na 64bitový operační systém. Ve výchozím nastavení soubor .exe, který se zkompiluje pomocí **/CLR: safe** se spustí na 64-bit CLR v počítači, který běží 64bitový operační systém. (V 32bitové verzi operačního systému, stejný soubor .exe běžet na 32bitová verze modulu CLR.) Bezpečné aplikace však může načíst součást 32-bit. V takovém případě bitovou kopii bezpečné spuštění v rámci podpory 64bitová verze operačního systému se nezdaří, když načte 32bitová aplikace (BadFormatException). Aby se zajistilo, že bezpečné bitové kopie i nadále spouštět, když ho načte 32bitovou kopii na 64bitový operační systém, musíte použít [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md) změnit metadata (.corflags) a označte ji spustit WOW64. Následující příkazový řádek je příklad. (Nahraďte vlastní symbol vstupního.)  
  
 **cl/CLR: safe t.cpp/Link /clrimagetype: pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 Informace o tom, jak získat upravený název najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md). Další informace o 64-bit cíle najdete v tématu [konfigurace Visual C++ pro 64bitové, x64 cíle](../../build/configuring-programs-for-64-bit-visual-cpp.md). Informace o používání čistý kód CLR najdete v tématu [postupy: přechod na/CLR: pure (C + +/ CLI)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) a [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="metadata-and-unnamed-classes"></a>Metadata a nepojmenované třídy  
 Nepojmenované třídy se zobrazí v metadatech s názvem následujícím způsobem: `$UnnamedClass$` *crc z – aktuální názvu souboru*`$`*index*`$`, kde *index*je sekvenční počet nepojmenované třídy v kompilace. Například následující ukázka kódu vygeneruje třídu nepojmenované v metadatech.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Použijte ildasm.exe pro metadata.  
  
## <a name="managed-extensions-for-c"></a>spravovaná rozšíření pro C++  
 Visual C++ již nepodporuje **/clr:oldsyntax** možnost. Tato možnost se považovat za zastaralou v sadě Visual Studio 2005. Je podporované syntaxe pro vytvoření spravovaného kódu v jazyce C++ C + +/ CLI. Další informace najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Pokud máte kód, který používá spravovaných rozšíření jazyka C++, doporučujeme portu ho na použití C + +/ CLI syntaxe. Informace o tom, jak portu kódu najdete v tématu [C + +/ CLI migrace Úvod do](../../dotnet/cpp-cli-migration-primer.md).  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti** otevřete projekt **stránky vlastností** dialogové okno.  
  
2.  Vyberte **vlastnosti konfigurace** složky.  
  
3.  Na **Obecné** vlastností stránky, upravte **podpory Common Language Runtime** vlastnost.  
  
    > [!NOTE]
    >  Když **/CLR** je povolena v **stránky vlastností** dialogové okno, vlastnosti – možnost kompilátoru, která nejsou kompatibilní s **/CLR** jsou rovněž upraveny, podle potřeby. Například pokud **/RTC** nastavena a poté **/CLR** je povoleno, **/RTC** se vypne.  
    >   
    >  Také při ladění **/CLR** aplikace, nastavte **ladicí program typu** vlastnost **Mixed** nebo **spravovat pouze**. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).  
  
     Informace, jak vytvořit modul, najdete v části [/NOASSEMBLY (vytvořit modul MSIL)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)