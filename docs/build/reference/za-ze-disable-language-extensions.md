---
title: -Za, - Ze (zakázat jazyková rozšíření) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378142"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Zakázat jazyková rozšíření)
**/Za** – možnost kompilátoru vysílá chybu pro konstruktory jazyka, které nejsou kompatibilní s kompilátorem C89 ANSI nebo ISO C ++ 11. **/Ze** – možnost kompilátoru, která je ve výchozím, umožňuje rozšíření Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  **/Ze** možnost je zastaralý, protože její chování ve výchozím nastavení zapnutý. Doporučujeme použít [/Zc (shoda)](../../build/reference/zc-conformance.md) – možnosti kompilátoru k ovládání funkcí rozšíření konkrétní jazyk. Seznam – možnosti kompilátoru zastaralé, najdete v článku **zastaralé a odebrat – možnosti kompilátoru** kapitoly [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] Kompilátoru nabízí celou řadu funkcí nad rámec těch, zadaný v kompilátorem ANSI C89, ISO C99 nebo ISO C++ standardů. Tyto funkce se souhrnně označují jako rozšíření Microsoft pro C a C++. Tato rozšíření jsou dostupné ve výchozím nastavení a není k dispozici při **/Za** je zadána možnost. Další informace o konkrétní rozšíření najdete v tématu [Extensions Microsoft pro C a C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Doporučujeme zakázat jazyková rozšíření zadáním **/Za** možnost, pokud máte v plánu k portu vaším programem do dalších prostředí. Když **/Za** byl zadán, kompilátor považuje Microsoft rozšířené klíčová slova jako jednoduché identifikátory, zakáže jiné rozšíření pro Microsoft a automaticky definuje `__STDC__` předdefinované makro pro programy C.  
  
 Další možnosti kompilátoru použít s **/Za** může ovlivnit jak kompilátor zajišťuje standardy shoda. Například **/Za** a [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md) může mít za následek s plovoucí desetinnou čárkou typu povýšení chování, které nejsou v souladu s ISO C99 nebo C ++ 11 standardy.  
  
 Způsoby, jak určit nastavení chování konkrétní standardy vyhovující, najdete v článku [/Zc](../../build/reference/zc-conformance.md) – možnost kompilátoru.  
  
 Další informace o problémech shoda s [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)], najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně zvolte **vlastnosti konfigurace**, **C/C++**, **jazyk**.  
  
3.  Změnit **zakázat jazyková rozšíření** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Zc (shoda)](../../build/reference/zc-conformance.md)