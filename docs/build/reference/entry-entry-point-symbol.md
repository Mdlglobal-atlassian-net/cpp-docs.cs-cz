---
title: "-ENTRY (Symbol vstupního bodu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs: C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6daafeba4376cdab679d7e93dce0605fae97a98e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (symbol vstupního bodu)
```  
/ENTRY:function  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *funkce*  
 Funkci, která určuje počáteční uživatelem definované adres pro soubor .exe nebo DLL.  
  
## <a name="remarks"></a>Poznámky  
 Možnost/Entry určuje funkci vstupního bodu jako počáteční adresa pro soubor .exe nebo DLL.  
  
 Funkce musí být definována pro použití `__stdcall` konvence volání. Parametry a návratové hodnoty závisí na, pokud je program konzolovou aplikaci, aplikace systému windows nebo knihovny DLL. Doporučujeme nechat linkeru nastavit vstupního bodu tak, že je správně inicializována běhové knihovny jazyka C a C++ konstruktory pro statické objekty jsou spouštěny.  
  
 Ve výchozím nastavení je počáteční adresa název funkce z běhové knihovny jazyka C. Linkeru vybere ho podle atributy programu, jak je znázorněno v následující tabulce.  
  
|Název funkce|Výchozí pro|  
|-------------------|-----------------|  
|**mainCRTStartup** (nebo **wmainCRTStartup**)|Aplikace, která používá /SUBSYSTEM:CONSOLE; volání `main` (nebo `wmain`)|  
|**WinMainCRTStartup** (nebo **wWinMainCRTStartup**)|Aplikace, která používá /SUBSYSTEM:**WINDOWS**; volání `WinMain` (nebo `wWinMain`), které musí být definován používat`__stdcall`|  
|**_DllMainCRTStartup –**|KNIHOVNY DLL; volání `DllMain` pokud existuje, které musí být definován používat`__stdcall`|  
  
 Pokud [/dll](../../build/reference/dll-build-a-dll.md) nebo [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) možnost nezadáte, linkeru vybere subsystém a vstupního bodu, podle toho, jestli `main` nebo `WinMain` je definována.  
  
 Funkce `main`, `WinMain`, a `DllMain` jsou tři formy uživatelem definované vstupní bod.  
  
 Při vytváření bitové kopie spravované, funkce určené k/Entry musí mít podpis (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).  
  
 Informace o tom, jak definovat vlastní `DllMain` vstupní bod, najdete v části [knihovny DLL a Visual C++ chování běhové knihovny](../../build/run-time-library-behavior.md) .  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **vstupní bod** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)