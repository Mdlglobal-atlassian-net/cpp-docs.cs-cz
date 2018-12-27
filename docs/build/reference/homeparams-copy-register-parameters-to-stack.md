---
title: /homeparams (Kopírovat parametry registru do zásobníku)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: ffb5ca602feb7a369bb31d0277834786d66ac12a
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627432"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopírovat parametry registru do zásobníku)

Přinutí parametry předané do registrů, které mají rovněž zapsány do jejich umístění v zásobníku při vstupu funkce.

## <a name="syntax"></a>Syntaxe

> **/ homeparams**

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru je k dispozici v nativní a křížové kompilátory, které cílí x64 pouze.

X64 konvence volání vyžaduje místo zásobníku, která bude přidělena pro všechny parametry, i pro parametry předány v registrech. Další informace najdete v tématu [předávání parametru](../../build/x64-calling-convention.md#parameter-passing). Ve výchozím nastavení nejsou zkopírovány parametry registru do prostor zásobníku přidělený pro ně v sestaveních pro vydání. Díky tomu je obtížné ladit sestavení pro vydání optimalizované aplikace.

Pro buildy vydaných verzí, můžete použít **/homeparams** možnost vynutit na kompilátoru ke zkopírování registrovat parametry do zásobníku, k zajištění, že můžete ladit svoji aplikaci. **/ homeparams** vyjadřuje výkon nevýhodu, protože vyžaduje další cyklus načíst parametry registru do zásobníku.

V sestavení ladění je vždy naplněný zásobníku s parametry předány v registrech.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadáním možnosti kompilátoru v **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)