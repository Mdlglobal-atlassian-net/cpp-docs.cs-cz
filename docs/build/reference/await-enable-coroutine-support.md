---
title: /await (povolení podpory korutiny)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: eeab3f4a1afc73e341f04222a55c8ce429490742
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078438"
---
# <a name="await-enable-coroutine-support"></a>/await (povolení podpory korutiny)

Pokud chcete povolit podporu kompilátoru pro korutiny, použijte možnost kompilátoru **/await** .

## <a name="syntax"></a>Syntaxe

> /await

## <a name="remarks"></a>Poznámky

Možnost kompilátoru **/await** umožňuje podporu kompilátoru pro C++ korutiny a klíčová slova **co_await**, **co_yield**a **co_return**. Tato možnost je ve výchozím nastavení vypnutá. Informace o podpoře pro korutiny v aplikaci Visual Studio naleznete na [blogu týmu sady Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Další informace o standardním návrhu korutiny najdete v článku [pracovní koncept N4628, technická specifikace pro C++ rozšíření pro korutiny](https://wg21.link/n4628).

Možnost **/await** je k dispozici od začátku v aplikaci Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu.

1. V části **Vlastnosti konfigurace**rozbalte složku **C/C++**  a vyberte stránku vlastností **příkazový řádek** .

1. Do pole **Další možnosti** zadejte možnost kompilátoru **/await** . Změny uložte kliknutím na **OK** nebo **použít** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
