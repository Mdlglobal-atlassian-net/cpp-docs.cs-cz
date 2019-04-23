---
title: /ZW (kompilace Windows Runtime)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: 73295866004fd506fd5f06ff25c048d14b821016
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424037"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (kompilace Windows Runtime)

Zkompiluje zdrojový kód pro podporu Visual C++ rozšíření komponent C++/CX pro vytváření aplikací pro univerzální platformu Windows (UPW).

Při použití **/ZW** ke kompilaci, vždy zadejte **/EHsc** také.

## <a name="syntax"></a>Syntaxe

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Arguments

**nostdlib**<br/>
Označuje, že Platform.winmd, Windows.Foundation.winmd a jiné výchozí soubory metadat (.winmd) Windows nejsou automaticky součástí kompilace. Místo toho je nutné použít [/FU (vynuceným názvem #using souboru)](fu-name-forced-hash-using-file.md) – možnost kompilátoru k explicitnímu zadání souborů metadat Windows.

## <a name="remarks"></a>Poznámky

Pokud zadáte **/ZW** možnost, kompilátor podporuje tyto funkce:

- Požadovaná metadata soubory, obory názvů, datové typy a funkce, které vaše aplikace vyžaduje ke spuštění v modulu Windows Runtime.

- Automatické počítání odkazů objektů prostředí Windows Runtime a automatické zrušení objektu při jeho počet odkazů dosáhne nuly.

Protože přírůstkový linker nepodporuje metadat Windows zahrnuty v souborech .obj pomocí **/ZW** možnost, nepoužívané [/Gm (povolení minimálního opětovného sestavení)](gm-enable-minimal-rebuild.md) možnost není kompatibilní s **/ZW**.

Další informace najdete v tématu [referenční dokumentace jazyka Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
