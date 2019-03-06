---
title: /ZW (kompilace Windows Runtime)
ms.date: 11/04/2016
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
ms.openlocfilehash: 944d66de3c029d9731a225281b4e592c477806e9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417980"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (kompilace Windows Runtime)

Zkompiluje zdrojového kódu, který podporuje rozšíření součásti Visual C++ C + +/ CX pro vytváření aplikací pro univerzální platformu Windows (UPW).

Při použití **/ZW** ke kompilaci, vždy zadejte **/EHsc** také.

## <a name="syntax"></a>Syntaxe

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Arguments

**nostdlib**<br/>
Označuje, že Platform.winmd, Windows.Foundation.winmd a jiné výchozí soubory metadat (.winmd) Windows nejsou automaticky součástí kompilace. Místo toho je nutné použít [/FU (vynuceným názvem #using souboru)](../../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru k explicitnímu zadání souborů metadat Windows.

## <a name="remarks"></a>Poznámky

Pokud zadáte **/ZW** možnost, kompilátor podporuje tyto funkce:

- Požadovaná metadata soubory, obory názvů, datové typy a funkce, které vaše aplikace vyžaduje ke spuštění v modulu Windows Runtime.

- Automatické počítání odkazů objektů prostředí Windows Runtime a automatické zrušení objektu při jeho počet odkazů dosáhne nuly.

Protože přírůstkový linker nepodporuje metadat Windows zahrnuty v souborech .obj pomocí **/ZW** možnost, [/Gm (povolení minimálního opětovného sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) možnost není kompatibilní s **/ZW** .

Další informace najdete v tématu [referenční dokumentace jazyka Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
