---
title: -QIfist (potlačit _ftol) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77ec65e330cebb1de718330ba129e960383b31c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378402"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Potlačit _ftol)
Zastaralé Potlačí volání pomocné funkce `_ftol` po vyžaduje převod z typu s plovoucí desetinnou čárkou integrální typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  **/ QIfist** je dostupný jenom v kompilátoru cílení x86; tato možnost kompilátoru není k dispozici v kompilátory cílení na [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] orARM.  
  
 Kromě převod z typu s plovoucí desetinnou čárkou integrální typ `_ftol` funkce zajišťuje zaokrouhlení režim jednotky s plovoucí desetinnou čárkou (FPU) směrem k nule (truncate), nastavením bity 10 a 11 řídicího slova. To zaručuje, že převod z typu s plovoucí desetinnou čárkou integrální typ k podle standardu ANSI C (část čísla se zahodí). Při použití **/QIfist**, tato záruka už neplatí. Zaokrouhlení režimu bude mít jednu z čtyři, jak je uvedeno v Intel v příručkách:  
  
-   Zaokrouhlí na nejbližší (sudé číslo. Pokud stejnou vzdálenost)  
  
-   Zaokrouhlí směrem k záporné nekonečno  
  
-   Zaokrouhlí směrem k kladné infinity  
  
-   Zaokrouhlí směrem k nule.  
  
 Můžete použít [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) funkce C Run-Time k úpravě zaokrouhlení chování FPU. Režim FPU zaokrouhlení výchozí hodnota je "Zaokrouhlit na nejbližší." Pomocí **/QIfist** může zvýšit výkon vaší aplikace, ale není bez rizika. Měli byste důkladně otestovat části kódu, které jsou citlivé na zaokrouhlení režimy před spoléhají na kód vytvořené s **/QIfist** v produkčním prostředí.  
  
 [/ arch (x86)](../../build/reference/arch-x86.md) a **/QIfist** nelze použít na stejné kompilace.  
  
> [!NOTE]
>  **/ QIfist** není v platnosti ve výchozím nastavení protože také zaokrouhlení ovlivňují plovoucí, přejděte na plovoucí bits bodu zaokrouhlení (které dojde po každé výpočtu), takže když nastavíte příznaky pro zaokrouhlení stylu jazyka C (směrem k nule), vaše plovoucí bod výpočty se mohou lišit. **/ QIfist** by se neměla používat, pokud kód závisí na očekávané chování zkracování zlomkové části číslo s plovoucí desetinnou čárkou. Pokud si nejste jistí, nepoužívejte **/QIfist**.  
  
 **/QIfist** možnost je zastaralé od verze Visual Studio 2005. Kompilátor udělal významná vylepšení v float int převod urychlit. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)