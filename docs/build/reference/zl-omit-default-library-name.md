---
title: /Zl (vypuštění názvu výchozí knihovny)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: cb8083d874abe17add1d27096ebce143d03a04cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809584"
---
# <a name="zl-omit-default-library-name"></a>/Zl (vypuštění názvu výchozí knihovny)

Výchozí název knihovny prostředí runtime C ze souboru .obj vynechá. Ve výchozím nastavení kompilátor vloží název tohoto knihovny do souboru .obj pro přesměrování linkeru, aby je správná knihovna.

## <a name="syntax"></a>Syntaxe

```
/Zl
```

## <a name="remarks"></a>Poznámky

Další informace ve výchozí knihovně najdete v tématu [použití knihovny Run-Time](md-mt-ld-use-run-time-library.md).

Můžete použít **/Zl** zkompilovat soubory .obj, které chcete umístit do knihovny. I když vynechání knihovnu s názvem uloží pouze malé množství místa pro soubor .obj jeden, celkového místa ušetřeného je důležité v knihovně, která obsahuje mnoho modulů objektu.

Tato možnost je upřesňující možnosti. Nastavení této možnosti odebere určité podpora knihovny C Runtime, který může být potřeba vaší aplikace, výsledkem propojování chyby, pokud je aplikace závislá na tato podpora. Pokud použijete tuto možnost, je nutné zadat požadované součásti jiným způsobem.

Použití [: / NODEFAULTLIB (ignorování knihoven)](nodefaultlib-ignore-libraries.md). pro přesměrování propojovací program ignorovat knihovny odkazuje ve všech souborech .obj.

Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

Při kompilaci s **/Zl**, `_VC_NODEFAULTLIB` je definována.  Příklad:

```
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **vynechat výchozí názvy knihoven** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
