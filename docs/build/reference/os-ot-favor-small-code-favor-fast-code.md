---
title: /Os, /Ot (Upřednostnit malý kód, upřednostnit rychlý kód)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336178"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Upřednostnit malý kód, upřednostnit rychlý kód)

Minimalizuje nebo maximalizuje velikost exes a knihovny DLL.

## <a name="syntax"></a>Syntaxe

```
/Os
/Ot
```

## <a name="remarks"></a>Poznámky

**/Os** (Favor Small Code) minimalizuje velikost EXEs a DLL tím, že dává kompilátoru pokyn, aby upřednostňoval velikost před rychlostí. Kompilátor může snížit mnoho C a C++ konstrukce funkčně podobné sekvence strojového kódu. Občas tyto rozdíly nabízejí kompromisy velikosti versus rychlost. Možnosti **/Os** a **/Ot** umožňují určit předvolbu pro jeden před druhým:

**/Ot** (Favor Fast Code) maximalizuje rychlost EXEs a DLL instruováním kompilátoru, aby upřednostňoval rychlost nad velikostí. (Toto je výchozí nastavení.) Kompilátor může snížit mnoho C a C++ konstrukce funkčně podobné sekvence strojového kódu. Občas tyto rozdíly nabízejí kompromisy velikosti versus rychlost. Možnost **/Ot** je implikována volbou Maximalizovat rychlost ([/O2).](o1-o2-minimize-size-maximize-speed.md) Možnost **/O2** kombinuje několik možností pro vytvoření velmi rychlého kódu.

Pokud používáte **/Os** nebo **/Ot**, pak je nutné také zadat [/Og](og-global-optimizations.md) pro optimalizaci kódu.

> [!NOTE]
> Informace shromážděné z profilování testovacích běhů přepíší optimalizace, které by jinak byly platné, pokud zadáte **/Ob**, **/Os**nebo **/Ot**. Další informace, [optimalizace s asistencí profilu](../profile-guided-optimizations.md).

**x86 Specifické**

Následující ukázkový kód ukazuje rozdíl mezi možnostmi Favor Small Code (**/Os**) a možností Favor Fast Code (**/Ot**) :

> [!NOTE]
> Následující popisuje očekávané chování při použití **/Os** nebo **/Ot**. Chování kompilátoru od vydání do vydání však může mít za následek různé optimalizace pro níže uvedený kód.

```
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

Jak je znázorněno v fragmentu strojového kódu níže, když differ.c je kompilován pro velikost (**/Os**), kompilátor implementuje multiply výraz v příkazu return explicitně jako násobit k vytvoření krátké, ale pomalejší sekvence kódu:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternativně při DIFFER.c je kompilován pro rychlost (**/Ot**), kompilátor implementuje `LEA` multiply výraz v příkazu return jako řadu shift a pokyny k vytvoření rychlé, ale delší posloupnost kódu:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**SPECIFICKÉ PRO END x86**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klikněte na stránku **vlastností Optimalizace.**

1. Upravte vlastnost **Velikost nebo rychlost laskavosti.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
