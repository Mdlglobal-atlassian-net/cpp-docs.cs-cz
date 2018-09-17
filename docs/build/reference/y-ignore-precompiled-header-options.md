---
title: -Y-(ignorovat možnosti předkompilovaných hlaviček) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /y-
dev_langs:
- C++
helpviewer_keywords:
- Y- compiler option [C++]
- -Y- compiler option [C++]
- /Y- compiler option [C++]
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99408490874f989a5063aef29d0b0e020f2e08a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719651"
---
# <a name="y--ignore-precompiled-header-options"></a>/Y- (Ignorovat možnosti předkompilovaných hlaviček)

Způsobí, že všechny ostatní `/Y` kompilátoru, které pokud chcete ignorovat (a nemůže sám být přepsáno).

## <a name="syntax"></a>Syntaxe

```
/Y-
```

## <a name="remarks"></a>Poznámky

Další informace o předkompilovaných hlaviček naleznete v tématu:

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)