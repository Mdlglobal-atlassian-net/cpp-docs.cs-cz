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
ms.openlocfilehash: c0d5110615f66dcf4f7dc170d89ee58c2e8fa5cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316532"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Povolit diagnostiku online)

Další informace se připojí k chybě nebo upozornění.

## <a name="syntax"></a>Syntaxe

```
/WL
```

## <a name="remarks"></a>Poznámky

Chybové zprávy a upozornění z kompilátoru jazyka C++ může být následován Další informace, které se zobrazí ve výchozím nastavení, na nový řádek. Při kompilaci z příkazového řádku, řádku další informace lze připojit k chybě nebo upozornění. To může být žádoucí, pokud zachytit výstup sestavení do souboru protokolu a následně zpracovat tento protokol a vyhledejte všechny chyby a upozornění. Středník se oddělení chyby nebo upozornění od další řádek.

Ne všechny chybové zprávy a upozornění mají další řádek informace. Následující kód vygeneruje chybu, která má další řádek informace; To vám umožní testování účinků při použití **/WL**.

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
