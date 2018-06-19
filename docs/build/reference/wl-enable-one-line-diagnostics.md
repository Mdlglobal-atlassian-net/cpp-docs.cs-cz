---
title: -WL (Povolit diagnostiku online) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58a6b41e66f7ec37ad02747edb8331049b9baef5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376784"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Povolit diagnostiku online)
Další informace se připojí k chybě nebo upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/WL  
```  
  
## <a name="remarks"></a>Poznámky  
 Chybové zprávy upozornění z kompilátoru C++ a může následovat další informace, které se zobrazí ve výchozím nastavení na nový řádek. Při kompilaci z příkazového řádku na další řádek informace může být přidán k chybě nebo upozornění. To může být žádoucí, pokud zaznamenáte výstupu sestavení do protokolového souboru a pak zpracovat protokol najít všechny chyby a upozornění. Středník dojde k oddělení chyby nebo zprávy upozornění z další řádku.  
  
 Ne všechny chybové zprávy a upozornění mají další řádek informace. Následující kód vygenerují chybu, která má další řádek informace; umožní vám testování účinků při použití **/Wl online**.  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)