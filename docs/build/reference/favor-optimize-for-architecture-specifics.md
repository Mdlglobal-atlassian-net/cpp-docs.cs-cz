---
title: -favor (optimalizace pro konkrétní architekturu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /favor
dev_langs:
- C++
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91f91373eef29adcb9a632e80520ed6713d3e39b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376218"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (Optimalizace pro konkrétní architekturu)
**/ favor:** `option` vytvoří kód, který je optimalizován pro konkrétní architekturu nebo pro konkrétní architektur micro AMD a architektury Intel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## <a name="remarks"></a>Poznámky  
 **/favor:Blend**  
 (x86 a x64) vytvoří kód, který je optimalizovaná pro konkrétní architektur micro AMD a architektury Intel. Při **/favor:blend** nemusí poskytuje nejlepší výkon možné na specifické procesory, je účelem poskytuje nejlepší výkon napříč širokým spektrem x86 a x64 procesorů. Ve výchozím nastavení **/favor:blend** je v platnosti.  
  
 **/favor:Atom**  
 (x86 a x64) vytvoří kód, který je optimalizovaná pro konkrétní Intel Atom procesoru a technologií Intel Centrino Atom procesoru. Kód, který je vytvořen pomocí **/favor:ATOM** mohou mít také Intel SSSE3, SSE3, SSE2 a SSE pokyny pro procesory Intel.  
  
 **/favor:amd64**  
 (jenom x64) optimalizuje generovaný kód pro AMD Opteron a Athlon procesorů, které podporují 64bitových aplikací. Optimalizovaný kód můžete spustit na všech x64 kompatibilní platformy. Kód, který je vytvořen pomocí **/favor:AMD64** na procesory Intel, které podporují Intel64, může dojít zhoršení výkonu.  
  
 **/favor:INTEL64**  
 (jenom x64) optimalizuje generovaný kód pro procesory Intel, které podporují Intel64, což obvykle poskytuje lepší výkon pro platformu. Výsledný kód můžete spustit na jakékoli x64 platformy. Kód, který je vytvořen s **/favor:INTEL64** na AMD Opteron a Athlon procesorů, které podporují rozšíření 64-bit, může dojít zhoršení výkonu.  
  
> [!NOTE]
>  Architektura Intel64 se dřív označovala jako rozšířené paměti 64 technologie a odpovídající možnost kompilátoru byl **/favor:EM64T**.  
  
 Informace o tom, jak program [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektuře, najdete v části [x64 softwarové konvence](../../build/x64-software-conventions.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost kompilátoru v **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)