---
title: -c (kompilace bez propojení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de6fe291bde8652b772c7091c1919836f88960fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710343"
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

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)