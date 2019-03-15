---
title: /link (předání možností linkeru)
ms.date: 11/04/2016
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
ms.openlocfilehash: 7f40841b82db9f46019ce2a96a61a1a0f622b6d5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813432"
---
# <a name="link-pass-options-to-linker"></a>/link (předání možností linkeru)

Jedna nebo více možností linkeru předá linkeru.

## <a name="syntax"></a>Syntaxe

```
/link linkeroptions
```

## <a name="arguments"></a>Arguments

*linkeroptions*<br/>
– Možnost linkeru nebo možnosti linkeru předány.

## <a name="remarks"></a>Poznámky

**/Link** a jeho možnosti linkeru musí vyskytovat za všechny názvy souborů a možností CL. Mezera mezi vyžádáním **/link** a `linkeroptions`. Další informace najdete v tématu [MSVC linkeru odkaz](linking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na stránky vlastností linkeru.

1. Upravte jednu nebo více vlastností.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
