---
title: -Oi (Generovat vnitřní funkce) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f28051f5d7aaaa4606fffa4d4c94fb2086031419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375838"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Generovat vnitřní funkce)
Nahradí některé funkce volá s formuláři vnitřního nebo jinak speciální funkce, které pomáhají aplikace pracovat rychleji.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Oi[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Programy, které používají vnitřní funkce jsou rychlejší, protože nemají režii volání funkce, ale může být způsobeno další kód vytvořený větší.  
  
 V tématu [vnitřní](../../preprocessor/intrinsic.md) Další informace, na kterém funkce mají vnitřní formulářů.  
  
 **/OI** pouze žádost kompilátoru nahradit některé funkce volání vnitřní funkce; kompilátor může volat funkci (a není nahraďte volání funkce vnitřní) Pokud je výsledkem je lepší výkon.  
  
 **x86 konkrétní**  
  
 Vnitřní funkce plovoucí desetinné čárky žádné speciální kontroly na vstupní hodnoty a tak fungovat s omezeným přístupem rozsahy vstupu a mají různé výjimek a podmínky hranice než rutiny knihovny se stejným názvem. Pomocí formulářů, vnitřní true znamená ztrátě IEEE výjimek a ztrátě `_matherr` a `errno` funkce; k tomu znamená ztrátě ANSI – shoda. Ale vnitřní formuláře může výrazně urychlit floating point náročné programy a pro mnoho programů, jsou problémy shoda málo praktické hodnoty.  
  
 Můžete použít [Za](../../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru potlačit generování true možnosti vnitřní s plovoucí desetinnou čárkou. V tomto případě jsou funkce generovány jako rutiny knihoven, které předávají argumenty přímo do čipu plovoucí desetinné čárky namísto jejich ukládání do zásobníku programu.  
  
 **END x86 konkrétní**  
  
 Můžete také použít [vnitřní](../../preprocessor/intrinsic.md) vytvořit vnitřní funkce, nebo [– funkce (C/C++)](../../preprocessor/function-c-cpp.md) explicitně vynutit volání funkce.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **optimalizace** stránku vlastností.  
  
4.  Změnit **povolit vnitřní funkce** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md)