---
title: -ZW (kompilace Windows Runtime) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbaa6d708cf882d3f396cc2a68159a520a017f8d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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