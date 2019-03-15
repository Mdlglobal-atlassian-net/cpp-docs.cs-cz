---
title: / await (povolení podpory korutiny)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: c0c8c0183c356900ba8f95d39e427d56eb1ec96b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809519"
---
# <a name="await-enable-coroutine-support"></a>/ await (povolení podpory korutiny)

Použití **/ await** – možnost kompilátoru povolení podpory korutiny kompilátoru.

## <a name="syntax"></a>Syntaxe

> / await

## <a name="remarks"></a>Poznámky

**/ Await** – možnost kompilátoru podporuje kompilátor C++ korutin a klíčová slova **co_await**, **co_yield**, a **co_return**. Tato možnost je ve výchozím nastavení vypnuta. Informace týkající se podpory korutiny v sadě Visual Studio, najdete v článku [blogu týmu Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Další informace o návrhu standardní korutiny, naleznete v tématu [N4628 práce koncept, technické specifikace pro rozšíření C++ pro Korutin](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).

**/ Await** možnost je k dispozici od verze Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete svůj projekt **stránky vlastností** dialogové okno.

1. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **příkazového řádku** stránku vlastností.

1. Zadejte **/ await** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
