---
title: -await (povolení podpory korutiny) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5da401f940a39c135ba0b64571b6330a42fed796
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725498"
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

2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **příkazového řádku** stránku vlastností.

3. Zadejte **/ await** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)