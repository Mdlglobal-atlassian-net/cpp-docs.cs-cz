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
ms.openlocfilehash: 1bcb90dbf071253dc0561845e3bd713dc42d5aef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988550"
---
# <a name="zl-omit-default-library-name"></a>/Zl (vypuštění názvu výchozí knihovny)

Vynechá výchozí název běhové knihovny jazyka C ze souboru. obj. Ve výchozím nastavení kompilátor umístí do souboru. obj název knihovny a nasměruje linker do správné knihovny.

## <a name="syntax"></a>Syntaxe

```
/Zl
```

## <a name="remarks"></a>Poznámky

Další informace o výchozí knihovně najdete v tématu [použití knihovny run-time](md-mt-ld-use-run-time-library.md).

**/Zl** můžete použít ke kompilaci souborů. obj, které chcete umístit do knihovny. I když je vynechán název knihovny, ukládá pouze malé množství prostoru pro jeden soubor. obj. celkové uložené místo je v knihovně, která obsahuje mnoho modulů objektů, významné.

Tato možnost je pokročilá možnost. Nastavení této možnosti odstraní určitou podporu knihovny modulu runtime jazyka C, kterou může vaše aplikace vyžadovat, což vede k chybám při propojování, pokud vaše aplikace závisí na této podpoře. Pokud použijete tuto možnost, musíte k tomu zadat požadované komponenty jiným způsobem.

Použijte [/NODEFAULTLIB (Ignorovat knihovny)](nodefaultlib-ignore-libraries.md). pro přesměrování linkeru tak, aby ignoroval odkazy knihovny ve všech souborech. obj.

Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

Při kompilaci s **/zl**je definována `_VC_NODEFAULTLIB`.  Příklad:

```cpp
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

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku **Upřesnit** vlastnosti.

1. Změňte vlastnost **vynechat výchozí názvy knihoven** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
