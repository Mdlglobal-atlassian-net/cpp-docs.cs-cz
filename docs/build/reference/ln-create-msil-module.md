---
title: /LN (Vytvořit modul MSIL)
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: 7c1d7149865a2558ac2b9ee70dac4bbcf8f37b63
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424207"
---
# <a name="ln-create-msil-module"></a>/LN (Vytvořit modul MSIL)

Určuje, že manifest sestavení by neměly být vložen do výstupního souboru.

## <a name="syntax"></a>Syntaxe

```
/LN
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **/LN** není platná (manifest sestavení je vložen do výstupního souboru).

Když **/LN** se používá jednu z [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnosti musí být rovněž použita.

Modul se nazývá spravovaný program, který nemá metadat sestavení v manifestu. Pokud kompilujete s [/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md) a **/LN**, zadejte [parametr/noassembly (vytvoření modulu MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru se vytvořit výstupní soubor.

Můžete vytvářet moduly, pokud budete chtít využít k vytváření sestavení s přístupem založených na komponentách.  Můžete tedy vytvářet typy a je zkompilovat do modulů.  Potom můžete generovat sestavení z jednoho nebo více modulů.  Další informace o vytvoření sestavení z modulů, naleznete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md) nebo [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker).

Výchozí přípona souboru pro modul je .netmodule.

Ve verzích Visual C++ před Visual C++ 2005, modul byl vytvořen s **/clr:noAssembly**.

Linkeru jazyka Visual C++ přijímá soubory .netmodule jako vstup a výstup souboru vytvořený pomocí linkeru bude sestavení nebo modul .NET s za běhu závislost na některý z modulů .NET, které byly vstup do linkeru.  Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

- Zadejte [parametr/noassembly (vytvoření modulu MSIL)](../../build/reference/noassembly-create-a-msil-module.md) ve fázi linkeru se vytvořit výstupní soubor.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Tato možnost kompilátoru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
