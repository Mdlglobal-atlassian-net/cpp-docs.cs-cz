---
title: -Za, - Ze (zakázání jazykových rozšíření) | Dokumentace Microsoftu
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
ms.openlocfilehash: 7e30fb37be6738b7100b84a1898c02ab4230c41b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597570"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Zakázat jazyková rozšíření)
**/Za** – možnost kompilátoru generuje chybu pro konstruktory jazyka, které nejsou kompatibilní s ANSI C89 nebo ISO C ++ 11. **/Ze** – možnost kompilátoru, která je ve výchozím, umožňuje rozšíření společnosti Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  **/Ze** možnost je zastaralá, protože její chování je ve výchozím. Doporučujeme použít [/Zc (shoda)](../../build/reference/zc-conformance.md) – možnosti kompilátoru k ovládání funkcí na rozšíření konkrétní jazyk. Seznam možností kompilátoru zastaralé, najdete v článku **zastaralé a odebrat možnosti kompilátoru** tématu [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Kompilátor Visual C++ nabízí celou řadu funkcí překračuje zadaný v standardy ANSI C89, ISO C99 nebo ISO C++. Tyto funkce se souhrnně označují jako rozšíření společnosti Microsoft pro C a C++. Tato rozšíření jsou k dispozici ve výchozím nastavení a není k dispozici při **/Za** je zadána možnost. Další informace o konkrétní rozšíření najdete v tématu [Extensions Microsoft pro C a C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Doporučujeme zakázat jazyková rozšíření tak, že zadáte **/Za** Pokud plánujete přenést váš program do jiných prostředí. Když **/Za** není zadán, kompilátor zpracovává Rozšířená klíčová slova jako identifikátory jednoduché společnosti Microsoft, zakáže ostatní rozšíření společnosti Microsoft a automaticky definuje `__STDC__` předdefinované makro pro programy C.  
  
 Další možnosti kompilátoru použít s **/Za** může ovlivnit, jak kompilátor pak zajistí shoda se standardy. Například **/Za** a [/fp (určení chování plovoucí desetinné čárky)](../../build/reference/fp-specify-floating-point-behavior.md) může způsobit chování povýšení typu s plovoucí desetinnou čárkou, které neodpovídá ISO C99 nebo C ++ 11 standardy.  
  
 Způsoby, jak určit nastavení chování konkrétní standardy-splňovala podmínky shody, najdete v článku [/Zc](../../build/reference/zc-conformance.md) – možnost kompilátoru.  
  
 Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně zvolte **vlastnosti konfigurace**, **C/C++**, **jazyka**.  
  
3.  Upravit **zakázat jazyková rozšíření** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Zc (shoda)](../../build/reference/zc-conformance.md)