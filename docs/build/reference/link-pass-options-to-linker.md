---
title: /link (předání možností linkeru)
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 37743e855c933b6236b5e7a837db257f332a3037
ms.sourcegitcommit: bbaf65f8ed1af12828b38f8eacd24f934ac0e538
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2019
ms.locfileid: "67155783"
---
# <a name="link-pass-options-to-linker"></a>/link (předání možností linkeru)

Jedna nebo více možností linkeru předá linkeru.

## <a name="syntax"></a>Syntaxe

> **/ link** *možnosti linkeru*

## <a name="arguments"></a>Arguments

*linker-options*<br/>
– Možnost linkeru nebo možnosti linkeru předány.

## <a name="remarks"></a>Poznámky

**/Link** a jeho možnosti linkeru musí vyskytovat za všechny názvy souborů a možností CL. Mezera mezi vyžádáním **/link** a možnosti linkeru. Další informace najdete v tématu [MSVC linkeru odkaz](linking.md).

## <a name="example"></a>Příklad

Tento ukázkový příkaz zkompiluje *hello.cpp* a odkazuje na existující soubor objektu *there.obj*. Poté předá Další **/Version** příkaz linkeru:

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

Rozhraní IDE obvykle posílá samostatných příkazů zkompilovat a propojit kód. Na stránkách vlastností projektu můžete nastavit možnosti linkeru.

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** složky.

1. Upravte jednu nebo více vlastností. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
