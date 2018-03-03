---
title: "-Os -Ot (upřednostnit malý kód, upřednostnit rychlý kód) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
dev_langs:
- C++
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02ce4b7d5c9617a88450fd90b4ac6c75d41148ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Upřednostnit malý kód, upřednostnit rychlý kód)
Minimalizuje nebo maximalizuje velikosti souborů exe a knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Os  
/Ot  
```  
  
## <a name="remarks"></a>Poznámky  
 **/OS** (upřednostnit malý kód) minimalizuje velikost souborů exe a knihovny DLL pomocí instruující kompilátor upřednostnit velikost před rychlostí. Kompilátor může snížit mnoho konstrukce C a C++ funkčně podobné pořadí zkompilovaný kód. Tyto rozdíly příležitostně nabízejí kompromisy velikost a rychlost. **/Os** a **/Ot** možnosti umožňují určit předvolbu pro jeden z nich:  
  
 **/Ot** (upřednostnit rychlého kód) maximalizuje rychlosti soubory .exe a knihovny DLL tím, že instruující kompilátor upřednostnit rychlost přes velikost. (Toto je výchozí hodnota). Kompilátor může snížit mnoho konstrukce C a C++ funkčně podobné pořadí zkompilovaný kód. Tyto rozdíly v některých případech nabízejí kompromisy velikost a rychlost. Možnost /Ot je zahrnuto v maximalizovat rychlost ([/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) možnost. **/O2** možnost kombinuje několik možností k vytvoření velmi rychlý kód.  
  
 Pokud používáte **/Os** nebo **/Ot**, pak musíte zadat také [/Og](../../build/reference/og-global-optimizations.md) za účelem optimalizace kód.  
  
> [!NOTE]
>  Informace získané z profilace testovací spouští přepíší optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete [Profile-Guided optimalizace](../../build/reference/profile-guided-optimizations.md).  
  
 **x86 konkrétní**  
  
 Následující příklad kódu ukazuje rozdíl mezi upřednostnit malý kód (**/Os**) možnosti a upřednostnit rychlého kód (**/Ot**) možnost:  
  
> [!NOTE]
>  Následující text popisuje očekávané chování při použití **/Os** nebo **/Ot**. Ale chování kompilátoru z vydání release může vést k jiné optimalizace pro následující kód.  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 Jak je vidět ve fragmentu kódu počítače níže, když kompiluje DIFFER.c pro velikost (**/Os**), implementuje kompilátoru násobení výrazu v příkaz return explicitně jako násobkem k vytvoření krátké ale nižší pořadí kódu:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 Případně, pokud DIFFER.c zkompilovat pro rychlost (**/Ot**), implementuje kompilátoru násobení výrazu v příkaz return jako řadu shift a `LEA` pokyny k vytvoření rychlé ale déle pořadí kódu:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **END x86 konkrétní**  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **optimalizace** stránku vlastností.  
  
4.  Změnit **upřednostnit velikost a rychlost** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)