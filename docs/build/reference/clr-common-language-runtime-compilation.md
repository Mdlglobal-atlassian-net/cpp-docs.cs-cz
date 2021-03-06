---
title: /clr (Common Language Runtime)
ms.date: 05/16/2019
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: fa2be3d3ce17df104cda121e4869c975ec6dd440
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837312"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Common Language Runtime)

Umožňuje aplikací a komponent, pokud chcete používat funkce z common language runtime (CLR).

## <a name="syntax"></a>Syntaxe

> **/ CLR**[**:**_možnosti_]

## <a name="arguments"></a>Arguments

*Možnosti*<br/>
Jeden nebo více z následujících parametrů oddělených čárkou.

- žádná

   Bez jakýchkoli možností **/CLR** vytvoří metadata pro aplikaci. Metadata mohou využívat jiné aplikace modulu CLR a umožňuje aplikaci využívala typy a data v metadatech jiných součástí modulu CLR. Další informace najdete v tématu [smíšený (nativní a spravovaná) sestavení](../../dotnet/mixed-native-and-managed-assemblies.md).

- **pure**

   **/ CLR: pure zastaralé**. V sadě Visual Studio 2017 nebo novější, odebere se možnost. Doporučujeme vám, že port kód, který musí být prázdné MSIL do jazyka C#.

- **safe**

   **zastaralé/CLR: safe**. V sadě Visual Studio 2017 nebo novější, odebere se možnost. Doporučujeme vám, že port kód, který musí být bezpečné jazyka MSIL do jazyka C#.

- **noAssembly**

   **zastaralé /CLR:noAssembly**. Použití [/LN (vytvoření modulu MSIL)](ln-create-msil-module.md) místo.

   Určuje, že manifest sestavení by neměly být vložen do výstupního souboru. Ve výchozím nastavení **noAssembly** možnost není platná.

   Spravované program, který nemá v manifestu sestavení metadata se označuje jako *modulu*. **NoAssembly** možnost jde použít jenom k vytvoření modulu. Pokud kompilujete pomocí [/c](c-compile-without-linking.md) a **/clr:noAssembly**, zadejte [parametr/noassembly](noassembly-create-a-msil-module.md) možnost ve fázi linker vytvořit modul.

   Před Visual Studio 2005 **/clr:noAssembly** požadované **/LD**. **/LD** je teď implicitní při zadání **/clr:noAssembly**.

- **initialAppDomain**

   Umožňuje aplikaci Visual C++ pro spuštění v modulu CLR verze 1.  Aplikace, která je zkompilován s použitím **initialAppDomain** by se nemělo používat aplikaci, která používá ASP.NET, protože není podporovaná ve verzi 1 modulu CLR.

- **nostdlib**

   Dává pokyn kompilátoru ignorovat výchozí adresář \clr. Kompilátor generuje chyby, pokud jsou včetně více verzí knihovny DLL jako například System.dll. Tato možnost umožňuje zadat konkrétní verzi rozhraní framework pro použití během kompilace.

## <a name="remarks"></a>Poznámky

Spravovaný kód je kód, který je možné ho zkontrolovat a spravovat pomocí modulu CLR. Spravovaný kód může přistupovat k spravovaných objektů. Další informace najdete v tématu [/CLR – omezení](clr-restrictions.md).

Informace o tom, jak vyvíjet aplikace, které definice a používání spravovaných typů najdete v tématu [přípony komponent pro platformy běhového prostředí](../../extensions/component-extensions-for-runtime-platforms.md).

Aplikace kompilované pomocí **/CLR** může nebo nemusí obsahovat spravovaná data.

Chcete-li povolit ladění na spravované aplikace, přečtěte si téma [/assemblydebug (přidání atributu DebuggableAttribute)](assemblydebug-add-debuggableattribute.md).

Pouze typy CLR bude vytvořena na haldě uvolňování. Další informace najdete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md). Chcete-li zkompilovat funkci do nativního kódu, použijte `unmanaged` direktivy pragma. Další informace najdete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md).

Ve výchozím nastavení **/CLR** není platná. Když **/CLR** je ve skutečnosti **/MD** platí také. Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](md-mt-ld-use-run-time-library.md). **/ MD** zajistí, že jsou vybrány dynamicky propojené s více vlákny verze rutin modulu runtime ze souborů standardní záhlaví (.h). Multithreading je požadovaná u spravovaného programování, protože CLR systému uvolňování paměti spustí finalizační metody v pomocné vlákno.

Pokud kompilujete pomocí **/c**, můžete zadat typ CLR výsledného výstupního souboru s [/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md).

**/ CLR** znamená **/EHa**a žádné jiné **/EH** možnosti jsou podporovány pro **/CLR**. Další informace najdete v tématu [/EH (Model zpracování výjimek)](eh-exception-handling-model.md).

Informace o tom, jak určit typ bitové kopie CLR souboru najdete v tématu [/CLRHEADER](clrheader.md).

Všechny moduly předané danému vyvolání linkeru musí být zkompilován pomocí stejného kompilátoru možnost knihovny run-time (**/MD** nebo **/LD**).

Použití [narozdíl od](assemblyresource-embed-a-managed-resource.md) – možnost linkeru na prostředek pro vložení do sestavení. [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md), [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md), a [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) možnosti linkeru také umožňují přizpůsobit, jak se vytvoří sestavení.

Když **/CLR** se používá, `_MANAGED` je definován symbol, musí být 1. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).

Globální proměnné v souboru nativní objekt je inicializován první (během zpracování funkce DllMain, pokud je spustitelný soubor knihovny DLL) a globálních proměnných v části spravované jsou inicializovány (dříve, než se spouštět spravovaný kód). `#pragma` [init_seg –](../../preprocessor/init-seg.md) ovlivní pouze pořadí inicializace kategorií spravovaných a nespravovaných.

## <a name="metadata-and-unnamed-classes"></a>Metadata a nepojmenované třídy

Nepojmenované třídy se zobrazí v metadat s názvem následujícím způsobem: `$UnnamedClass$` *crc z aktuální název souboru-*`$`*index*`$`, kde *index*je sekvenční počet nepojmenované třídy v sestavení. Například následující ukázka kódu generuje Nepojmenovaná třída v metadatech.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Umožňuje zobrazit metadata ildasm.exe.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
