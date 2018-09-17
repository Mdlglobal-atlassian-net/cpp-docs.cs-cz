---
title: -homeparams (kopírování parametrů registru do zásobníku) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6c51c5e6062f4d7b793e3adb6e9f22e03a65c11
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699833"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopírovat parametry registru do zásobníku)

Přinutí parametry předané do registrů k zápisu do jejich umístění v zásobníku při vstupu funkce.

## <a name="syntax"></a>Syntaxe

```
/homeparams
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru je pouze pro x64 kompilátory (nativní a křížové kompilování).

Předání parametrů v x x64 kompilace, konvence volání vyžadují stackspace parametrů, dokonce i pro parametry předány v registrech. Další informace najdete v tématu [předávání parametru](../../build/parameter-passing.md). Ale ve výchozím nastavení v sestavení pro vydání, parametry registru nebudou zapsány do zásobníku, do místa, která je již k dispozici pro parametry. To ztěžuje ladění sestavení pro optimalizované (vydání) vašeho programu.

U sestavení pro vydání, použijte **/homeparams** zajistit, že můžete ladit svoji aplikaci. **/ homeparams** vyjadřuje výkon nevýhodu, protože vyžaduje cyklus načíst parametry registru do zásobníku.

V sestavení pro ladění je vždy naplněný zásobníku s parametry předány v registrech.

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