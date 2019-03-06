---
title: /Qfast_transcendentals (Vynutit rychlé transcendentní objekty)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: d96b2c93e9fc8be73ef43f63fc0a6328661df442
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414197"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Vynutit rychlé transcendentní objekty)

generuje kód vloženého Transcendentní funkce.

## <a name="syntax"></a>Syntaxe

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru vynutí Transcendentní funkce pro převod na vložený kód, aby se zvýšila rychlost provádění. Tuto možnost má vliv pouze v případě, že je spárovaná s **/FP: except** nebo **/FP: precise**. Generování vloženého kódu pro Transcendentní funkce už je výchozí chování v rámci **Fast**.

Tato možnost není kompatibilní s **/FP: strict**. Zobrazit [/fp (určení chování plovoucí desetinné čárky)](../../build/reference/fp-specify-floating-point-behavior.md) Další informace o – možnosti kompilátoru bod s plovoucí desetinnou čárkou.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
