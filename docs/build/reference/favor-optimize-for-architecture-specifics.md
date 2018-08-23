---
title: -favor (optimalizace pro konkrétní architekturu) | Dokumentace Microsoftu
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
ms.openlocfilehash: 75081c3a2e8918bfe8abf43373d755ca258f2595
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464535"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (Optimalizace pro konkrétní architekturu)
**/ favor:** `option` vytvoří kód, který je optimalizovaný pro konkrétní architekturu nebo pro konkrétní micro architektury AMD a architektury Intel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## <a name="remarks"></a>Poznámky  
 **/favor:Blend**  
 (x86 a x64) vytvoří kód, který je optimalizovaný pro konkrétní micro architektury AMD a architektury Intel. Zatímco **/favor:blend** nemusí poskytnout co nejlepšího výkonu na konkrétním procesoru je to možné, je určen poskytuje nejlepší výkon napříč celou řadu x86 a x64 procesory. Ve výchozím nastavení **/favor:blend** je v platnosti.  
  
 **/favor:Atom**  
 (x86 a x64) vytvoří kód, který je optimalizovaný pro konkrétní procesor Intel Atom a technologii Intel Centrino Atom. Kód, který je generován pomocí **/favor:ATOM** může také vytvořit Intel SSSE3, SSE3, SSE a SSE2 pokyny pro procesory Intel.  
  
 **/favor:amd64**  
 (pouze x64) optimalizuje kód vygenerovaný AMD Opteron a Athlon procesory, které podporují 64bitových aplikací. Optimalizovaný kód můžete spustit na všech x64 kompatibilní platformy. Kód, který je generován pomocí **/favor:AMD64** může způsobit horší výkon na procesorech Intel, které podporují Intel64.  
  
 **/favor:INTEL64**  
 (pouze x64) optimalizuje kód generovaný pro procesory Intel, které podporují Intel64, což obvykle poskytuje lepší výkon pro danou platformu. Výsledný kód lze spustit na libovolné x64 platformy. Kód, který je vytvořen s **/favor:INTEL64** může způsobit horší výkon na AMD Opteron a Athlon procesory, které podporují 64bitových aplikací.  
  
> [!NOTE]
>  Intel64 architektury se dřív označovalo jako Extended Memory 64 Technology a byla odpovídající možnost kompilátoru **/favor:EM64T**.  
  
 Informace o tom, jak programovat pro x64 architektury, najdete v článku [x64 softwarové konvence](../../build/x64-software-conventions.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Zadáním možnosti kompilátoru v **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)