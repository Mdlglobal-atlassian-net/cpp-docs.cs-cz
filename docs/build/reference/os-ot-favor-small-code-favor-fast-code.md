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
ms.openlocfilehash: 5bbdda07eacdb003515a40a93a232c0f8626ca89
ms.sourcegitcommit: aed09c9c05e6b031c8a9f87a8d6bbdaf253485e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412246"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Upřednostnit malý kód, upřednostnit rychlý kód)

Minimalizuje nebo maximalizuje velikost souborů exe a DLL.

## <a name="syntax"></a>Syntaxe

```
/Os
/Ot
```

## <a name="remarks"></a>Poznámky

**/OS** (upřednostnit malý kód) minimalizuje velikost souborů exe a DLL tím, že kompilátor, aby velikost upřednostnil před rychlostí. Kompilátor může snížit mnoho konstrukcí jazyka C a C++ funkčně podobné pořadí strojového kódu. Tyto rozdíly občas nabízet kompromisy velikost a rychlost. **/Os** a **/Ot** možností vám umožňují určit předvolby pro některého z nich:

**/Ot** (upřednostnit rychlý kód) maximalizuje rychlost souborů exe a DLL tím, že kompilátor, aby rychlost upřednostnil před velikostí. (Toto je výchozí.) Kompilátor může snížit mnoho konstrukcí jazyka C a C++ funkčně podobné pořadí strojového kódu. Tyto rozdíly v některých případech nabízejí kompromisy velikost a rychlost. **/Ot** předpokládá možnost maximalizovat rychlost ([/O2](o1-o2-minimize-size-maximize-speed.md)) možnost. **/O2** možnost kombinuje několik možností, jak vytvořit velmi rychlý kód.

Pokud používáte **/Os** nebo **/Ot**, pak musíte zadat také [/og](og-global-optimizations.md) optimalizovat kód.

> [!NOTE]
>  Informace shromážděné z testovacích běhů profilování přepíšou optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete [Profile-Guided optimalizace](../profile-guided-optimizations.md).

**x86 konkrétní**

Následující příklad kódu ukazuje rozdíl mezi upřednostnit malý kód ( **/Os**) možnosti a upřednostnit rychlý kód ( **/Ot**) možnost:

> [!NOTE]
>  Následující text popisuje očekávaný chování při použití **/Os** nebo **/Ot**. Nicméně chování kompilátoru jednotlivých verzí může vést k jiné optimalizace pro kód uvedený níže.

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

Jak znázorňuje fragment strojového kódu níže, když DIFFER.c je zkompilován pro velikost ( **/OS**), kompilátor implementuje vynásobit výrazu v příkaz return explicitně jako vícenásobně k vytvoření krátkým, ale nižší pořadí kódu:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternativně, pokud je DIFFER.c zkompiluje pro vyšší rychlost ( **/Ot**), kompilátor implementuje vynásobit výrazu v návratový příkaz jako řadu objektů shift a `LEA` pokyny k vytvoření rychlé, ale delší posloupnost kódu:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**END x86 konkrétní**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **upřednostnit velikost nebo rychlost** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
