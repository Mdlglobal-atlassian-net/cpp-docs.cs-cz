---
title: "-Z7,. - Zi, - ZI (formát ladicích informací) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b80339192a7d335b0989ac8a67446c0f5716a76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (formát ladicích informací)
Vyberte typ ladění informace, které jsou vytvořené pro vaši aplikaci a zda tyto informace jsou uchovávány v souborech objektu (.obj) nebo v databázi programu (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto možnosti jsou popsány v následující tabulce.  
  
 Žádné  
 Vytvoří žádné informace o ladění, takže kompilace je rychlejší.  
  
 **/ Z7**  
 Vytvoří soubor .obj obsahující úplné symbolické ladicí informace pro použití s ladicím programem. Symbolické ladicí informace obsahuje názvy a typy proměnných, a také funkce a čísla řádků. Žádný soubor .pdb vytváří.  
  
 Pro distributorů knihoven jiných výrobců je výhodné nemá soubor .pdb. Soubory .obj pro předkompilované hlavičky jsou však nutné během fáze odkaz a ladění. Pokud je pouze soubory objektu zadejte informace (a žádný kód), budete také muset kompilovat s [/Yl (Vložit referenci PCH knihovny ladění)](../../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
 **/Zi**  
 Vytvoří databázi programu (PDB), který obsahuje informace o typu a symbolické ladicí informace pro použití s ladicím programem. Symbolické ladicí informace obsahuje názvy a typy proměnných, a také funkce a čísla řádků.  
  
 **/Zi** nemá vliv na optimalizace. Ale **/Zi** implikují **/debug**; najdete v části [/Debug (Generovat ladicí informace)](../../build/reference/debug-generate-debug-info.md) Další informace.  
  
 Informace o typu je umístěn v souboru PDB a ne v souboru .obj.  
  
 Můžete použít [/Gm (povolit minimální sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) s **/Zi**, zatímco **/Gm** není k dispozici, když kompilujete s **/Z7**.  
  
 Při kompilaci s **/Zi** a **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atribut nebude uskutečňován v metadatech sestavení; je třeba zadat ji ve zdrojovém kódu, pokud ho chcete. Tento atribut může ovlivnit výkon modulu runtime aplikace. Další informace o tom, jak Debuggable atribut ovlivňuje výkon a jak je možné upravit dopad na výkon, najdete v části [snadněji bitové kopie pro ladění](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).  
  
 **/ZI**  
 Vytvoří databáze programu, jak je popsáno výše, ve formátu, který podporuje funkce upravit a pokračovat. Pokud chcete použít, úpravy a pokračujete v ladění, musíte použít tuto možnost. Protože většina optimalizace nejsou kompatibilní s upravit a pokračovat, pomocí **/ZI** zakáže všechny `#pragma optimize` příkazů v kódu.  
  
 **/ZI** způsobí, že [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md) a [/FC (úplná cesta z souboru zdrojového kódu v diagnostice)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) pro použití v kompilaci.  
  
 **/ZI** není kompatibilní s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  **/ZI** je dostupný jenom v kompilátory cílení x86 a x64 procesory; tato možnost kompilátoru není k dispozici v kompilátory cílení procesory ARM.  
  
 Kompilátor názvy databáze programu *projektu*pdb. Pokud kompilaci souboru bez projektu kompilátor vytvoří databáze s názvem VC*x*0.pdb., kde *x* je hlavní verzi [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] používán. Kompilátor vloží název PDB do každého souboru .obj vytvořené pomocí této možnosti odkazující na umístění informací symbolický a číslo řádku ladicího programu. Pokud použijete tuto možnost, bude vaše soubory .obj menší, protože ladicí informace jsou uloženy v souboru PDB místo soubory .obj.  
  
 Pokud objekty, které byly zkompilovány použití této možnosti vytvoříte knihovny, musí být na soubor .pdb přidružené k dispozici knihovny propojen s program. Proto pokud distribuujete knihovny, je nutné distribuovat PDB.  
  
 Pokud chcete vytvořit knihovnu, která obsahuje informace o ladění bez použití soubory PDB, je nutné vybrat do kompilátoru jazyka C kompatibilní 7.0 (**/Z7**) možnost. Pokud použijete možnosti předkompilovaných hlaviček, ladicí informace pro předkompilované hlavičky a zbytek zdrojový kód je umístěn v PDB. **/Yd** možnost je ignorována, pokud je zadána možnost databáze programu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Obecné** stránku vlastností.  
  
4.  Změnit **Debug Information Format** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)