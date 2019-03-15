---
title: /GT (Podpora místního optického úložiště se zabezpečenými vlákny)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 417ac00a446f773a424553e42478a4f0cf58efc6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822513"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Podpora místního optického úložiště se zabezpečenými vlákny)

Podporuje bezpečnost vlákna pro data Alokovaná pomocí statického úložiště lokálního vlákna, to znamená, že data Alokovaná pomocí `__declspec(thread)`.

## <a name="syntax"></a>Syntaxe

```
/GT
```

## <a name="remarks"></a>Poznámky

Data deklarovaná s `__declspec(thread)` se odkazuje prostřednictvím pole úložiště thread local (TLS). Protokol TLS pole je pole adres, které systém udržuje pro každé vlákno. Každou adresu v tomto poli poskytuje umístění úložiště thread-local data.

Vlákno je zjednodušený objekt, který se skládá ze zásobníku a zaregistrujte kontextu a je možné naplánovat v různých vláknech. Vlákno můžete spustit v libovolném vlákně. Vzhledem k tomu, že vlákno může získat automaticky a restartuje později na jiném vlákně, adresa pole TLS nesmí uložit do mezipaměti nebo optimalizovat jako běžné dílčí výraz napříč volání funkce (viz [/Og (globální optimalizace)](og-global-optimizations.md) možnost Podrobnosti). **/GT** brání tyto optimalizace.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **povolit optimalizace bezpečné pro Vlákénka** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
