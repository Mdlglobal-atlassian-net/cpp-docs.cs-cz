---
title: /WL (Povolit diagnostiku online)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: b1ded1cd18eb75ed47b76c1353ad82a7fa497ba9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988575"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Povolit diagnostiku online)

Připojí další informace k chybě nebo varovné zprávě.

## <a name="syntax"></a>Syntaxe

```
/WL
```

## <a name="remarks"></a>Poznámky

Pro chybové zprávy a upozornění z C++ kompilátoru mohou následovat další informace, které se ve výchozím nastavení zobrazí na novém řádku. Při kompilaci z příkazového řádku lze do chybové zprávy nebo upozornění přidat další řádek informací. To může být žádoucí, Pokud zachytíte výstup sestavení do souboru protokolu a potom tento protokol zpracujete a zjistíte všechny chyby a upozornění. Středníky oddělí zprávu o chybě nebo upozornění z dalšího řádku.

Ne všechny chybové zprávy a upozornění obsahují další řádek informací. Následující kód vygeneruje chybu, která obsahuje další řádek informací; umožní vám otestovat efekt při použití **/WL**.

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku vlastností **příkazový řádek** .

1. Zadejte možnost kompilátoru do pole **Další možnosti** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
