---
title: -clr (kompilace Common Language Runtime) | Dokumentace Microsoftu
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
ms.openlocfilehash: ff46958afea8825f29941d9f3cbead20c533c76c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676982"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Common Language Runtime)
Umožňuje aplikací a komponent, pokud chcete používat funkce z common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>Arguments  
 `options`  
 Jeden nebo více z následujících parametrů oddělených čárkou.  
  
 **/ CLR**  
 Vytvoří metadata pro aplikaci. Metadata mohou využívat jiné aplikace modulu CLR a umožňuje aplikaci využívala typy a data v metadatech jiných součástí modulu CLR.  
  
 Další informace naleznete v tématu  
  
 [Smíšená (nativní a spravovaná) sestavení](../../dotnet/mixed-native-and-managed-assemblies.md) a  
  
 [Postupy: přechod na/CLR](../../dotnet/how-to-migrate-to-clr.md).  
  
 **/ CLR: pure**  
 / CLR: pure je zastaralý. Tuto možnost nemusí podporovat budoucí verze kompilátoru. Doporučujeme vám, že port kód, který musí být prázdné MSIL do jazyka C#.  
  
 **/ CLR: safe**  
 / CLR: safe je zastaralý. Tuto možnost nemusí podporovat budoucí verze kompilátoru. Doporučujeme vám, že port kód, který musí být bezpečné jazyka MSIL do jazyka C#. 
  
 **/CLR:noAssembly**  
 Určuje, že manifest sestavení by neměly být vložen do výstupního souboru. Ve výchozím nastavení **noAssembly** možnost není platná.  
  
 **NoAssembly** možnost je zastaralý. Použití [/LN (vytvoření modulu MSIL)](../../build/reference/ln-create-msil-module.md) místo.  
  
 Spravované program, který nemá v manifestu sestavení metadata se označuje jako *modulu*. **NoAssembly** možnost jde použít jenom k vytvoření modulu. Pokud kompilujete pomocí [/c](../../build/reference/c-compile-without-linking.md) a **/clr:noAssembly**, zadejte [parametr/noassembly](../../build/reference/noassembly-create-a-msil-module.md) možnost ve fázi linker vytvořit modul.  
  
 Před Visual C++ 2005 **/clr:noAssembly** požadované **/LD**. **/LD** je teď implicitní při zadání **/clr:noAssembly**.  
  
 **/clr:initialAppDomain**  
 Umožňuje aplikaci Visual C++ pro spuštění v modulu CLR verze 1.  Aplikace, která je zkompilován s použitím **initialAppDomain** by se nemělo používat aplikaci, která používá ASP.NET, protože není podporovaná ve verzi 1 modulu CLR.  
  
 **nostdlib**  
 Dává pokyn kompilátoru ignorovat výchozí adresář \clr. Kompilátor generuje chyby, pokud jsou včetně více verzí knihovny DLL jako například System.dll. Tato možnost umožňuje zadat konkrétní verzi rozhraní framework pro použití během kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Spravovaný kód je kód, který je možné ho zkontrolovat a spravovat pomocí modulu CLR. Spravovaný kód může přistupovat k spravovaných objektů. Další informace najdete v tématu [/CLR – omezení](../../build/reference/clr-restrictions.md).  
  
 Informace o tom, jak vyvíjet aplikace, které definice a používání spravovaných typů najdete v tématu [přípony komponent pro platformy běhového prostředí](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Aplikace kompilované pomocí **/CLR** může nebo nemusí obsahovat spravovaná data.  
  
 Chcete-li povolit ladění na spravované aplikace, přečtěte si téma [/assemblydebug (přidání atributu DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).  
  
 Pouze typy CLR bude vytvořena na haldě uvolňování. Další informace najdete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md). Chcete-li zkompilovat funkci do nativního kódu, použijte `unmanaged` direktivy pragma. Další informace najdete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md).  
  
 Ve výchozím nastavení **/CLR** není platná. Když **/CLR** je ve skutečnosti **/MD** platí také. Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](../../build/reference/md-mt-ld-use-run-time-library.md). **/ MD** zajistí, že jsou vybrány dynamicky propojené s více vlákny verze rutin modulu runtime ze souborů standardní záhlaví (.h). Multithreading je požadovaná u spravovaného programování, protože CLR systému uvolňování paměti spustí finalizační metody v pomocné vlákno.  
  
 Pokud kompilujete pomocí **/c**, můžete zadat typ CLR výsledného výstupního souboru s [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **/ CLR** znamená **/EHa**a žádné jiné **/EH** možnosti jsou podporovány pro **/CLR**. Další informace najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md).  
  
 Informace o tom, jak určit typ bitové kopie CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).  
  
 Všechny moduly předané danému vyvolání linkeru musí být zkompilován pomocí stejného kompilátoru možnost knihovny run-time (**/MD** nebo **/LD**).  
  
 Použití [narozdíl od](../../build/reference/assemblyresource-embed-a-managed-resource.md) – možnost linkeru na prostředek pro vložení do sestavení. [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md), a [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) možnosti linkeru také umožňují přizpůsobit, jak se vytvoří sestavení.  
  
 Když **/CLR** se používá, `_MANAGED` je definován symbol, musí být 1. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).  
  
 Globální proměnné v souboru nativní objekt je inicializován první (během zpracování funkce DllMain, pokud je spustitelný soubor knihovny DLL) a globálních proměnných v části spravované jsou inicializovány (dříve, než se spouštět spravovaný kód). `#pragma`[init_seg –](../../preprocessor/init-seg.md) ovlivní pouze pořadí inicializace kategorií spravovaných a nespravovaných.  
  
## <a name="metadata-and-unnamed-classes"></a>Metadata a nepojmenované třídy  
 Nepojmenované třídy se zobrazí v metadat s názvem následujícím způsobem: `$UnnamedClass$` *crc z aktuální název souboru-*`$`*index*`$`, kde *index*je sekvenční počet nepojmenované třídy v sestavení. Například následující ukázka kódu generuje Nepojmenovaná třída v metadatech.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Umožňuje zobrazit metadata ildasm.exe.  
  
## <a name="managed-extensions-for-c"></a>spravovaná rozšíření pro C++  
 Visual C++ již nepodporuje zprostředkovatele **oldSyntax** možnost. Tato možnost se přestala nabízet v sadě Visual Studio 2005. Podporované syntaxe pro psaní spravovaného kódu v jazyce C++ je C + +/ CLI. Další informace najdete v tématu [přípony komponent pro platformy běhového prostředí](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Pokud máte kód, který používá spravovaného rozšíření jazyka C++, doporučujeme port používal C + +/ CLI syntaxe. Informace o tom, jak váš kód, naleznete v tématu [C + +/ CLI Základy migrace](../../dotnet/cpp-cli-migration-primer.md).  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti** pro otevření projektu **stránky vlastností** dialogové okno.  
  
2.  Vyberte **vlastnosti konfigurace** složky.  
  
3.  Na **Obecné** vlastnosti stránky, upravte **Common Language Runtime support** vlastnost.  
  
    > [!NOTE]
    >  Když **/CLR** je povolený v **stránky vlastností** dialogovém okně Vlastnosti – možnost kompilátoru, které nejsou kompatibilní s **/CLR** také upravit podle potřeby. Například pokud **/RTC** nastavena a poté **/CLR** je povoleno, **/RTC** se vypne.  
    >   
    >  Navíc při ladění **/CLR** aplikace, nastavte **typ ladicího programu** vlastnost **smíšený** nebo **režim pouze spravovaný**. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).  
  
     Informace, jak vytvořit modul, naleznete v tématu [parametr/noassembly (vytvoření modulu MSIL)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)