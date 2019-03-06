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
ms.openlocfilehash: f5e57a19f337653cdab6f66404b9458e1e7fed0d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412832"
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

**/Link** a jeho možnosti linkeru musí vyskytovat za všechny názvy souborů a možností CL. Mezera mezi vyžádáním **/link** a `linkeroptions`. Další informace najdete v tématu [nastavení možností Linkeru](../../build/reference/setting-linker-options.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na stránky vlastností linkeru.

1. Upravte jednu nebo více vlastností.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
