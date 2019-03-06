---
title: /c (kompilovat bez propojení)
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: cdce86f9ba74b2541529d922c580d6393a93f775
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416456"
---
# <a name="c-compile-without-linking"></a>/c (kompilovat bez propojení)

Brání automatické volání odkaz.

## <a name="syntax"></a>Syntaxe

```
/c
```

## <a name="remarks"></a>Poznámky

Kompilace s **/c** vytvoří pouze soubory .obj. ODKAZ musí explicitně volat s správné soubory a možnosti pro propojení fáze buildu.

Všechny interní projekt vytvořili ve vývojovém prostředí používá **/c** možnost ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

- Tato možnost není k dispozici v rámci vývojového prostředí.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.

## <a name="example"></a>Příklad

Následující příkaz vytvoří soubory objektů FIRST.obj a SECOND.obj. THIRD.obj se ignoruje.

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

Pro vytvoření spustitelného souboru, je nutné vyvolat odkaz:

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
