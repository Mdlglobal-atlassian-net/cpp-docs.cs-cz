---
title: "-BASE (základní adresa) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddf399757d881484817be676ca3077b4fc21709
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="base-base-address"></a>/BASE (základní adresa)
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 / Základní možnost nastaví základní adresa pro program, přepsání výchozí umístění pro soubor knihovny DLL nebo .exe. Výchozí základní adresa pro soubor .exe je 0x400000 pro bitové kopie, 32bitový nebo 0x140000000 pro 64bitové bitové kopie. Pro knihovny DLL je výchozí základní adresa 0x10000000 pro bitové kopie, 32bitový nebo 0x180000000 pro 64bitové bitové kopie. V operačních systémech, které nepodporují adresu místa rozložení náhodné (technologie ASLR) nebo pokud byla nastavena možnost /DYNAMICBASE:NO operačního systému nejdřív pokusí se načíst jeho zadaný programu nebo výchozí základní adresa. Pokud dostatek místa není k dispozici, systém přemístí program. Chcete-li zabránit přemístění, použijte [/FIXED](../../build/reference/fixed-fixed-base-address.md) možnost.  
  
 Propojovací chybu pokud *adresu* není násobkem 64 kB. Volitelně můžete zadat velikost programu; linkeru vydá upozornění, pokud program se nemůže vejít velikostí, které zadáte.  
  
 Na příkazovém řádku je další způsob, jak zadat základní adresu pomocí souboru odpovědí základní adresu. Soubor odezvy základní adresa je textový soubor, který obsahuje základní adresy a volitelné velikosti všechny knihovny DLL, bude používat váš program a text jedinečný klíč pro každou základní adresu. Chcete-li zadat základní adresu pomocí souboru odpovědí, použijte znaku zavináče (@) a název souboru odpovědí *filename*, za nímž čárkou, pak se `key` hodnotu pro základní adresu používat v souboru. Hledá linkeru *filename* buď na zadané cestě, nebo pokud není zadána žádná cesta, v adresáři určeném v proměnné prostředí LIB. Každý řádek v *filename* představuje jeden DLL a má následující syntaxi:  
  
```  
  
key address [size] ;comment  
```  
  
 `key` Je řetězec alfanumerické znaky a není velká a malá písmena. To je obvykle název knihovny DLL, ale nemusí být. `key` Následuje na základní *adresu* v jazyce C, šestnáctkové nebo desítkové soustavě a volitelné maximální `size`. Všechny tři argumenty jsou oddělené mezerami nebo karty. Linkeru vydá upozornění, pokud zadaný `size` je menší než požadované programem virtuální adresní prostor. A `comment` je zadán středníkem (;) a může být na stejném nebo na samostatném řádku. Linkeru ignoruje všechny text z středník na konec řádku. Tento příklad ukazuje součástí takový soubor:  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 Pokud soubor, který obsahuje tyto řádky nazývá DLLS.txt, platí následující ukázkový příkaz tyto informace:  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>Poznámky  
 Z bezpečnostních důvodů se společnost Microsoft doporučuje, můžete použít [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) jako možnost základní adresy pro vaše spustitelné soubory. Tím se vygeneruje spustitelné bitové kopie, který může být náhodně rebased při načítání, pomocí funkce adresního prostoru rozložení náhodného přeskupování (technologie ASLR) systému Windows. Možnost /DYNAMICBASE ve výchozím nastavení zapnutý.  
  
 Jiný způsob, jak nastavit základní adresa je pomocí *základní* argument [název](../../build/reference/name-c-cpp.md) nebo [KNIHOVNY](../../build/reference/library.md) příkaz. /BASE a [/dll](../../build/reference/dll-build-a-dll.md) možnosti společně odpovídají **KNIHOVNY** příkaz.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **Linkeru** složky.  
  
3.  Vyberte **Upřesnit** stránku vlastností.  
  
4.  Změnit **základní adresu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)