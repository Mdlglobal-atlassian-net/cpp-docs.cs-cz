---
title: -clr (kompilace Common Language Runtime) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1284d0300fcea3adc5f2884a7d1eff7862ff2b65
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
 / CLR: pure je zastaralý. V budoucích verzích kompilátor nemusí podporovat tuto možnost. Doporučujeme vám, že je port kód, který musí být čistá MSIL jazyka C#.  
  
 **/ CLR: safe**  
 / CLR: safe je zastaralý. V budoucích verzích kompilátor nemusí podporovat tuto možnost. Doporučujeme vám, že je port kód, který musí být bezpečné MSIL jazyka C#. 
  
 **/CLR:noAssembly**  
 Určuje, že manifest sestavení by neměly být vložen do výstupního souboru. Ve výchozím nastavení **noAssembly** možnost není platný.  
  
 **NoAssembly** parametr se již nepoužívá. Použití [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md) místo.  
  
 Spravovaný program, který nemá metadata sestavení v manifestu se označuje jako *modulu*. **NoAssembly** možnost lze použít pouze k vytvoření modulu. Pokud zkompilujete pomocí [/c](../../build/reference/c-compile-without-linking.md) a **/clr:noAssembly**, zadejte [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) možnost ve fázi linkeru Vytvořte modul.  
  
 Před Visual C++ 2005 **/clr:noAssembly** požadované **/LD**. **/LD** je nyní zahrnuta, když zadáte **/clr:noAssembly**.  
  
 **/clr:initialAppDomain**  
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
  
 Pokud zkompilujete pomocí **/c**, můžete zadat typ CLR výsledný výstupní soubor s [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **/ CLR** znamená **/EHa**a ne dalších **/EH** možnosti jsou podporovány pro **/CLR**. Další informace najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md).  
  
 Informace o tom, jak určit typ obrázku CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).  
  
 Předaný dané vyvolání linkeru všechny moduly musí být zkompilovány pomocí stejné knihovna RTL – možnost kompilátoru (**/MD** nebo **/LD**).  
  
 Použití [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) – možnost linkeru pro vložení do sestavení prostředku. [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md), a [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) možnosti linkeru vám také umožní přizpůsobit vytváření sestavení.  
  
 Když **/CLR** se používá, `_MANAGED` symbol je definována musí být 1. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).  
  
 Globální proměnné v souboru nativní objekt se inicializují první (během zpracování funkce DllMain Pokud spustitelný soubor knihovny DLL) a globální proměnné v části spravované se inicializují (před spouští spravovaný kód). `#pragma`[init_seg –](../../preprocessor/init-seg.md) ovlivňuje pouze pořadí inicializace spravovanými a nespravovanými kategorií.  
  
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