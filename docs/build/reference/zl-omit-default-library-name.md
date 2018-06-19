---
title: -Zi (vypuštění názvu výchozí knihovny) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs:
- C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c14a3217334c2c43bac7fbcce8b0bfd60a609d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379715"
---
# <a name="zl-omit-default-library-name"></a>/Zl (vypuštění názvu výchozí knihovny)
Název výchozí C runtime knihovny ze souboru .obj vynechá. Ve výchozím nastavení kompilátoru zařadí do souboru .obj směrovat linkeru do správné knihovny název knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zl  
```  
  
## <a name="remarks"></a>Poznámky  
 Další informace o výchozí knihovna najdete v tématu [použití běhové knihovny](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 Můžete použít **/Zl** zkompilovat soubory .obj seskupíte do knihovny. I když vynechání název knihovny uloží jenom malé množství místa pro .obj jeden soubor, v knihovně, který obsahuje mnoho modulů objektu je důležité celkové místo uložit.  
  
 Tato možnost je upřesňující možnost. Nastavení této možnosti odebere určité podpora knihoven C Runtime, která je vyžadována ve vaší aplikaci, což vede k propojování chyby, pokud je aplikace závislá na tato podpora. Pokud použijete tuto možnost je nutné zadat požadované součásti jiným způsobem.  
  
 Použití [/NODEFAULTLIB (Ignorovat knihovny)](../../build/reference/nodefaultlib-ignore-libraries.md). pro přesměrování linkeru ignorovat knihovny odkazuje na všechny soubory .obj.  
  
 Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
 Při kompilaci s **/Zl**, `_VC_NODEFAULTLIB` je definována.  Příklad:  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **vynechejte výchozí názvy knihoven** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)