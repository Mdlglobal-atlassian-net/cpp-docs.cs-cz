---
title: -vmm,. - virtuální počítače, - vmv (obecná reprezentace) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2f79238c890d43678332203acbe9d935a54102
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379559"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (obecná reprezentace)
Použít, když [/vmb, / vmg (metoda reprezentace)](../../build/reference/vmb-vmg-representation-method.md) je vybrán jako [metoda reprezentace](../../build/reference/vmb-vmg-representation-method.md). Tyto možnosti znamenat model dědičnosti definice třídy není ještě došlo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto možnosti jsou popsány v následující tabulce.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/vmm**|Určuje vyjádření nejobecnější ukazatele na člena třídy jako ten, který používá vícenásobná dědičnost.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [pointers_to_members – #pragma](../../preprocessor/pointers-to-members.md) je **vícenásobná dědičnost –**.<br /><br /> Tento zápis je větší než se vyžaduje pro jedna dědičnost.<br /><br /> Pokud je virtuální dědičnost model definice třídy, pro kterou je deklarován ukazatel na člena, kompilátor vygeneruje chybu.|  
|**/vms**|Určuje vyjádření nejobecnější ukazatele na člena třídy jako ten, který používá žádné dědičnosti nebo jedna dědičnost.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [pointers_to_members – #pragma](../../preprocessor/pointers-to-members.md) je **single_inheritance**.<br /><br /> Toto je nejmenší reprezentace ukazatel na člena třídy.<br /><br /> Pokud je model dědičnosti definice třídy, pro kterou je deklarován ukazatele na člena, několik nebo virtuální, kompilátor vygeneruje chybu.|  
|**/vmv**|Určuje vyjádření nejobecnější ukazatele na člena třídy jako ten, který používá virtuální dědičnost. Tato nikdy dojde k chybě a je výchozí.<br /><br /> Odpovídající [– klíčové slovo dědičnosti](../../cpp/inheritance-keywords.md) a argument [pointers_to_members – #pragma](../../preprocessor/pointers-to-members.md) je **virtual_inheritance**.<br /><br /> Tato možnost vyžaduje větší ukazatel a další kód interpretovat ukazatele než ostatní možnosti.|  
  
 Když zadáte jednu z těchto možností model dědičnosti, tento model se používá pro všechny ukazatelé na členy třídy, bez ohledu na jejich dědičnost typů nebo zda je ukazatel deklarovaný před nebo po třídy. Proto, pokud chcete vždy použít jedním dědičnost třídy, můžete snížit velikost kód kompilovat s **/VMS**, nicméně pokud chcete použít nejobecnější případ (za cenu největší znázornění dat), kompilovat s **/vmv**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/ vmb, / vmg (metoda reprezentace)](../../build/reference/vmb-vmg-representation-method.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)