---
title: -ZW (kompilace Windows Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97a97158dda886a09fb6ccb00898a8c518d8e250
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602259"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (kompilace Windows Runtime)
Zkompiluje zdrojového kódu, který podporuje rozšíření součásti Visual C++ C + +/ CX pro vytváření aplikací pro univerzální platformu Windows (UPW).  
  
 Při použití **/ZW** ke kompilaci, vždy zadejte **/EHsc** také.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>Arguments  
 nostdlib  
 Označuje, že Platform.winmd, Windows.Foundation.winmd a jiné výchozí soubory metadat (.winmd) Windows nejsou automaticky součástí kompilace. Místo toho je nutné použít [/FU (vynuceným názvem #using souboru)](../../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru k explicitnímu zadání souborů metadat Windows.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte **/ZW** možnost, kompilátor podporuje tyto funkce:  
  
-   Požadovaná metadata soubory, obory názvů, datové typy a funkce, které vaše aplikace vyžaduje ke spuštění v modulu Windows Runtime.  
  
-   Automatické počítání odkazů objektů prostředí Windows Runtime a automatické zrušení objektu při jeho počet odkazů dosáhne nuly.  
  
 Protože přírůstkový linker nepodporuje metadat Windows zahrnuty v souborech .obj pomocí **/ZW** možnost, [/Gm (povolení minimálního opětovného sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) možnost není kompatibilní s **/ZW** .  
  
 Další informace najdete v tématu [referenční dokumentace jazyka Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)