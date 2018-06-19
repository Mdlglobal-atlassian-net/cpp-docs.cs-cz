---
title: -DEBUG (generování ladicích informací) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f93c47a0f96cf0b75b453bcea97212d4ab2fd6d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375724"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generovat ladicí informace)
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>Poznámky  

**/DEBUG** možnost vytvoří ladicí informace pro spustitelný soubor.    
  
Linkeru umístí informace o ladění do souboru databáze (PDB) programu. Aktualizuje PDB během následných sestavení programu.  
  
Spustitelný soubor (soubor .exe nebo knihovny DLL) vytvořen pro ladění obsahuje název a cesta odpovídající PDB. Ladicí program přečte embedded název a používá PDB při ladění programu. Linkeru používá základní název programu a rozšíření PDB název databáze programu a vloží cestu, kde se vytvořila. Chcete-li přepsat toto výchozí nastavení, nastavte [/PDB](../../build/reference/pdb-use-program-database.md) a zadejte jiný název souboru.  

**/DEBUG:FASTLINK** možnost opustí informací o privátní symbolu v produktech jednotlivých kompilace sloužící k vytvoření spustitelného souboru. Vygeneruje omezené PDB, která indexuje do informace o ladění do objektu soubory a knihovny sloužící k vytvoření spustitelného souboru místo provedení úplné kopie. Tato možnost může propojit ze dvou k čtyřikrát tak rychlý jako úplné PDB generování a se doporučuje, když jsou místně ladění a máte k dispozici sestavení produkty. Tato omezená PDB nelze použít pro ladění, pokud tyto produkty požadované sestavení nejsou k dispozici, například při nasazení spustitelný soubor na jiném počítači. V příkazovém řádku vývojáře můžete nástroj mspdbcmf.exe generovat úplné PDB z této omezené PDB. V sadě Visual Studio použijte pro generování celého souboru PDB k vytvoření úplné PDB pro projekt nebo řešení položky nabídky projektu nebo sestavení.  
  
**/DEBUG:FULL** možnost přesune všechny privátní symbol informace z produktů jednotlivých kompilace (objekt soubory a knihovny) do jedné PDB a může být nejvíce zdlouhavý součástí odkaz. Ale úplné PDB slouží k ladění spustitelného souboru, když žádné jiné produkty sestavení jsou k dispozici, například při nasazení spustitelný soubor.  
  
**/DEBUG: žádné** možnost negeneruje PDB.  
  
Pokud zadáte **/DEBUG** s žádné další možnosti linkeru výchozí **/DEBUG:FULL** pro příkazový řádek a sestavení souboru pravidel pro verzi sestavení v prostředí Visual Studio IDE a pro ladění a vydání sestavení v sadě Visual Studio 2015 a starší verze. Od verze Visual Studio 2017, systém sestavení v prostředí IDE výchozí **/DEBUG:FASTLINK** Pokud zadáte **/DEBUG** možnost pro ladění. Ostatní výchozí hodnoty jsou beze změny pro zachování zpětné kompatibility.  
  
Kompilátoru [kompatibilní s C7](../../build/reference/z7-zi-zi-debug-information-format.md) (/ Z7) způsobí, že kompilátor opustit ladicí informace v souborech obj. Můžete také [databázi programu](../../build/reference/z7-zi-zi-debug-information-format.md) – možnost kompilátoru (/Zi) Chcete-li uložit informace o ladění do souboru PDB souboru .obj. Linkeru hledá objektu PDB nejprve absolutní cesta napsané v souboru .obj, a pak v adresáři, který obsahuje souboru .obj. Nelze zadat název souboru PDB nebo umístění pro linkeru objektu.  
  
[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md) je zahrnuta, když je zadán/Debug.  
  
/ DEBUG změní výchozí hodnoty [/OPT](../../build/reference/opt-optimizations.md) možnost z REF z bránou Firewall a NOREF NOICF, takže pokud chcete původní výchozí hodnoty, je nutné explicitně zadat /OPT:REF nebo /OPT:ICF.  
  
Není možné vytvořit s příponou .exe nebo .dll, který obsahuje informace o ladění. Ladění informace vždy umístěny v souboru .obj nebo pdb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **ladění** stránku vlastností.  
  
4.  Změnit **Generovat ladicí informace** vlastnost Povolit generování PDB. To umožňuje /DEBUG:FASTLINK ve výchozím nastavení v Visual Studio 2017.  
  
4.  Změnit **generovat celého souboru databáze programu** vlastnost umožňující /DEBUG:FULL úplné PDB vygenerovat pro každý přírůstkové sestavení.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)
