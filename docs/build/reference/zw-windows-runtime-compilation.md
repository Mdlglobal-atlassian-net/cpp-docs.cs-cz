---
title: -ZW (kompilace Windows Runtime) | Microsoft Docs
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
ms.openlocfilehash: fce6c6825ed4ae715a2f4cde6b0e1ffa8b3b6733
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380063"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (kompilace Windows Runtime)
Zkompiluje zdrojový kód pro podporu [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) pro vytváření aplikací pro univerzální platformu Windows (UWP).  
  
 Při použití **/ZW** zkompilovat, vždycky zadat **/EHsc** také.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>Arguments  
 nostdlib  
 Označuje, že Platform.winmd, Windows.Foundation.winmd a ostatní výchozí soubory metadat (.winmd) systému Windows nejsou automaticky součástí kompilace. Místo toho musíte použít [/FU (vynuceným názvem #using souboru)](../../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru k explicitnímu zadání soubory metadat Windows.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte **/ZW** možnost kompilátor podporuje tyto funkce:  
  
-   Požadovaná metadata souborů, obory názvů, datové typy a funkce, které vaše aplikace vyžaduje provést v prostředí Windows Runtime.  
  
-   Automatické počítání odkazů objektů prostředí Windows Runtime a jsou automatické zahození objektu při jeho počet odkazů přejde na hodnotu nula.  
  
 Protože přírůstkové linkeru nepodporuje metadat Windows součástí soubory .obj pomocí **/ZW** možnost, [/Gm (povolit minimální sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) možnost není kompatibilní s **/ZW** .  
  
 Další informace najdete v tématu [referenční příručka jazyka Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)