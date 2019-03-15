---
title: /Yu (Použít předkompilovaný hlavičkový soubor)
ms.date: 11/04/2016
f1_keywords:
- /yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: c0dcb045450d6e6eca31b8c76a92726e62400656
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810114"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Použít předkompilovaný hlavičkový soubor)

Instruuje kompilátor, který chcete použít existující soubor předkompilované hlavičky (pch) v aktuální kompilaci.

## <a name="syntax"></a>Syntaxe

```
/Yu[filename]
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Název souboru hlaviček, který je součástí souboru zdroje s použitím **#include** direktiva preprocesoru.

## <a name="remarks"></a>Poznámky

Název vloženého souboru musí být stejný pro **/Yc** možnost, která vytvoří předkompilované hlavičky a všechny následné **/Yu** možnost použití předkompilované hlavičky.

Pro **/Yc**, `filename` Určuje bod, ve které předkompilace zastaví; kompilátor překompiluje celý kód však `filename` a výsledné předkompilované hlavičky pomocí základní název vloženého souboru a přípony názvů z .pch.

Soubor .pch musí být vytvořen pomocí **/Yc**.

Kompilátor považuje veškerý kód, ke kterým došlo před souboru .h jako předkompilované. Přeskočí na právě dalších fázích můžete využít **#include** směrnice, které jsou přidružené k souboru .h, názvu souboru používá kód obsažený v souboru .pch a pak zkompiluje veškerý kód po `filename`.

Na příkazovém řádku je povolen žádný prostor mezi **/Yu** a `filename`.

Pokud zadáte **/Yu** možnost bez názvu souboru, zdrojový program musí obsahovat [#pragma hdrstop](../../preprocessor/hdrstop.md) – Direktiva pragma, který určuje název souboru předkompilované hlavičky souboru .pch. V tomto případě kompilátor použije předkompilované hlavičky (souboru .pch) s názvem podle [/Fp (název. Soubor pch)](fp-name-dot-pch-file.md). Kompilátor přeskočí na umístění této direktivy pragma, obnoví zkompilovaný stav ze souboru předkompilované hlavičky zadaného pomocí direktivy pragma a poté kompiluje pouze kód, který následuje direktivu pragma. Pokud **#pragma hdrstop** neurčuje název souboru, hledá kompilátor soubor s názvem odvozené ze základní název zdrojového souboru s příponou .pch. Můžete také použít **/FP** můžete určit soubor .pch jiný.

Pokud zadáte **/Yu** možnost bez názvu souboru a nepovedlo se určit **hdrstop** – Direktiva pragma, je vygenerována chybová zpráva a kompilace neproběhne úspěšně.

Pokud **/Yc** `filename` a **/Yu** `filename` možnosti, ke kterým dochází na stejném příkazovém řádku a oba odkazují na stejný název souboru **/Yc** `filename` trvá Priorita, až předkompilace veškerý kód a včetně uvedeného souboru. Tato funkce zjednodušuje psaní soubory pravidel.

Protože soubory .pch obsahují informace o prostředí počítače a paměti adresu informace o programu, byste měli používat jenom soubor pch na počítači, kde se vytvořila.

Další informace o předkompilovaných hlaviček naleznete v tématu:

- [/Y (předkompilované hlavičky)](y-precompiled-headers.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Zadejte [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](yc-create-precompiled-header-file.md) v souboru s příponou .cpp v projektu.

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **předkompilované hlavičky** stránku vlastností.

1. Upravit **vytvořit/použít PCH prostřednictvím souboru** vlastnost nebo **vytvoření a použití předkompilovaných hlaviček** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="examples"></a>Příklady

Pokud následující kód:

```
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

je zkompilován s příkazovým řádkem `CL /YuMYAPP.H PROG.CPP`, kompilátor nezpracovává tři obsahují příkazy, ale používá předkompilovaný kód z MYAPP.pch, a tím ukládání čas potřebný při předběžném zpracování všechny tři soubory (a všechny soubory, které mohou zahrnovat).

Můžete použít [/Fp (název. Soubor pch)](fp-name-dot-pch-file.md) spolu s možností **/Yu** můžete zadat název souboru .pch, pokud je název liší od obou argument názvu souboru do **/Yc** nebo základní název zdrojového souboru, jako v následující:

```
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

Tento příkaz určuje předkompilovaného hlavičkového souboru s názvem MYPCH.pch. Kompilátor používá k obnovení předkompilované stavu všech včetně MYAPP.h a soubory hlaviček až do jeho obsah. Kompilátor poté kompiluje kód, nacházející se MYAPP.h **zahrnují** příkazu.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
