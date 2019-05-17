---
title: /DEBUG (Generovat ladicí informace)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837148"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generovat ladicí informace)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>Poznámky

**/DEBUG** možnost vytvoří ladicí informace pro spustitelný soubor.

Linker vloží informace o ladění do souboru databáze (PDB) programu. Během následujících sestaveních programu aktualizuje soubor PDB.

Spustitelný soubor (soubor .exe nebo knihovny DLL) vytvořené pro ladění obsahuje název a cesta odpovídající souboru PDB. Ladicí program načte vložený název a použije soubor PDB při ladění programu. Propojovací program používá základní název programu a příponou PDB pro název databáze programu a vloží cestu, kde byl vytvořen. Chcete-li přepsat toto výchozí nastavení, nastavte [/PDB](pdb-use-program-database.md) a zadejte jiný název souboru.

**/Debug: fastlink** možnost je k dispozici v sadě Visual Studio 2017 a novější. Tato možnost ponechá informace o privátních symbolů v jednotlivých kompilace produkty sloužící k sestavení spustitelného souboru. Generuje omezené, která indexuje do informací o ladění do souborů objektů a knihoven sloužící k sestavení spustitelného souboru místo vytvoření úplné kopie souboru PDB. Tuto možnost můžete propojit dvě pro čtyřikrát nejrychleji Úplné generování souborů PDB a doporučuje se při místním ladění a máte k dispozici sestavení produkty. Tato omezená PDB nelze použít pro ladění, když produkty požadované sestavení nejsou k dispozici, například když nasazená spustitelného souboru v jiném počítači. V příkazovém řádku pro vývojáře můžete použít nástroj mspdbcmf.exe Generovat úplný soubor PDB z této omezené PDB. V sadě Visual Studio použijte ke generování úplný soubor PDB vytvořit úplný soubor PDB pro projekt nebo řešení položky nabídky projekt nebo sestavení.

**/Debug: Full** možnost přesune všechny informace o privátních symbolů z kompilace jednotlivých produktů (souborů objektů a knihoven) do jednoho souboru PDB a může být nejvíce časově náročná část odkazu. Úplný soubor PDB však lze použít k ladění spustitelného souboru, když žádné jiné produkty sestavení jsou k dispozici, například při nasazení spustitelný soubor.

**/DEBUG: žádný** možnost negeneruje souboru PDB.

Pokud zadáte **/DEBUG** bez jakýchkoli dalších možností linkeru výchozí hodnota je **/Debug: Full** příkazového řádku a soubor pravidel sestavení pro vydání verze sestavení v integrovaném vývojovém prostředí sady Visual Studio a pro ladění a vydání sestavení v sadě Visual Studio 2015 a starší verze. Od v sadě Visual Studio 2017, systém sestavení v integrovaném vývojovém prostředí standardně **/Debug: fastlink** při zadání **/DEBUG** možnost pro sestavení pro ladění. Pro zachování zpětné kompatibility jsou beze změny jiných výchozích hodnot.

Kompilátoru [kompatibilní s C7](z7-zi-zi-debug-information-format.md) (/ Z7) možnost způsobí, že kompilátor v souborech .obj opustit ladicí informace. Můžete také použít [databázi programu](z7-zi-zi-debug-information-format.md) (/Zi) – možnost kompilátoru ukládat informace o ladění v souboru .obj souboru PDB. Propojovací program hledá PDB objektu nejprve absolutní cesta napsané v souboru .obj, a pak v adresáři, který obsahuje soubor .obj. Nelze zadat název souboru PDB nebo umístění do propojovacího programu objektu.

[/ INCREMENTAL](incremental-link-incrementally.md) je zahrnuta, když je zadán/Debug.

/ DEBUG změní výchozí hodnoty [/OPT](opt-optimizations.md) možnost z REF NOREF a ze brána NOICF, takže pokud chcete původní výchozí hodnoty, je nutné explicitně zadat OPT nebo /OPT:ICF.

Není možné vytvořit s příponou .exe nebo .dll, který obsahuje informace o ladění. Ladit informace vždy umístěny v souboru .obj nebo .pdb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **Generovat ladicí informace** vlastností pro povolení generování PDB. Ve výchozím nastavení v sadě Visual Studio 2017 nebo novější díky tomu/Debug: fastlink.

1. Upravit **Generovat úplný soubor databáze programu** vlastností pro povolení/Debug: full pro úplné generování souborů PDB pro každé přírůstkové sestavení.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
