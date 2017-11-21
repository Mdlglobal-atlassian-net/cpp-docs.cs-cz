---
title: "Optimalizace kódu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.assetid: 4f33e6c7-9870-43b3-9c2f-d7e44f764971
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3da29e9a0269c4748f10d9e8ba926103305239e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="optimizing-your-code"></a>Optimalizace kódu
Optimalizace spustitelný soubor, můžete dosáhnout rovnováhu mezi rychlé spuštění rychlost a velikost malý kód. Toto téma popisuje některé z mechanismů, které poskytuje Visual C++ pro optimalizaci kódu.  
  
## <a name="language-features"></a>Jazykové funkce  
 Následující témata popisují některé z funkcí Optimalizace v jazyce C/C++.  
  
 [Optimalizace Pragmas a klíčových slov](../../build/reference/optimization-pragmas-and-keywords.md)  
 Seznam klíčová slova a pragmas používané ve vašem kódu ke zlepšení výkonu.  
  
 [Možnosti kompilátoru uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md)  
 Seznam **/O** – možnosti kompilátoru konkrétně ovlivňujících velikost provádění rychlost nebo kódu.  
  
 [Deklarátor odkazu rvalue: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)  
 Odkazy rvalue podporu implementace *přesunout sémantiku*. Pokud přesunutí sémantiku slouží k implementaci knihovny šablon, výkon aplikací, které používají tyto šablony může výrazně zlepšit.  
  
### <a name="the-optimize-pragma"></a>Optimalizovat – direktiva Pragma  
 Pokud optimalizované část kódu způsobí chyby nebo zpomalení, můžete použít [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma k vypnutí možnosti optimalizace pro tento oddíl.  
  
 Vložte kód mezi dvěma direktivy, následujícím způsobem.  
  
```  
#pragma optimize("", off)  
// some code here   
#pragma optimize("", on)  
```  
  
## <a name="programming-practices"></a>Postupy programování  
 Možná jste si všimli další zprávy upozornění při kompilaci kódu s optimalizací. Toto chování je očekávané, protože některé upozornění se týkají pouze optimalizovaný kód. Pokud jste věnujte pozornost tato upozornění se můžete vyhnout mnoho problémů optimalizace.  
  
 Optimalizace programu pro rychlost paradoxically, by mohl způsobit kódu pomaleji. Je to proto, že některé optimalizace pro rychlost zvýšení velikosti kódu. Například vložené funkce eliminuje režijní náklady volání funkce. Ale vložené příliš mnoho kódu provést vašeho programu tak velká, že číslo stránky virtuální paměti chyb zvyšuje. Rychlost získaných během volání funkce odstraňuje proto mohou být ztraceny k odkládací paměť.  
  
 Následující témata popisují drželi osvědčených postupů programování.  
  
 [Tipy pro zlepšení časově kritického kódu](../../build/reference/tips-for-improving-time-critical-code.md)  
 Lépe kódování techniky přispět lepší výkon. Toto téma navrhuje kódování technik, které vám může pomoct zajistěte, aby uspokojivému provádění kritický pro čas části kódu.  
  
 [Doporučené postupy optimalizace](../../build/reference/optimization-best-practices.md)  
 Obsahuje obecné pokyny o optimálním optimalizovat vaší aplikace.  
  
## <a name="debugging-optimized-code"></a>Ladění optimalizovaného kódu  
 Protože optimalizace může změnit kód vytvořené kompilátor, doporučujeme ladit aplikaci a měření jeho výkon a pak optimalizovat kód.  
  
 Následující témata obsahují základní informace o ladění.  
  
-   [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
-   [Běžné problémy při vytváření sestavení pro vydání](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
 Následující témata obsahují více rozšířené informace o ladění.  
  
-   [Postupy: ladění optimalizovaného kódu](/visualstudio/debugger/how-to-debug-optimized-code)  
  
-   [Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost](../../build/reference/why-floating-point-numbers-may-lose-precision.md)  
  
 Následující soubory témata poskytují informace o tom, jak optimalizovat vytváření, načítání a provádění kódu.  
  
-   [Zvýšení propustnosti kompilátoru](../../build/reference/improving-compiler-throughput.md)  
  
-   [Použití názvu funkce bez závorek () nevygeneruje žádný kód](../../build/reference/using-function-name-without-parens-produces-no-code.md)  
  
-   [Optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md)  
  
-   [Určení optimalizace kompilátoru pro projekt knihovny ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)  
  
-   [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](../../build/dll-frequently-asked-questions.md#mfc_optimization)  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]Postup zkrátit čas načtení knihovny DLL metod najdete v tématu "Optimalizace DLL načíst doba" ve sloupci "Pod pokličkou" v "Časopis MSDN" na [knihovny MSDN](http://go.microsoft.com/fwlink/?linkid=556) webu.  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]Minimalizovat stránkování v aplikacích najdete v tématu "Zlepšení Runtime výkonu s hladké práce nastavit nástroj pro" a "vylepšení výkonu modulu Runtime s Smooth pracovní sady nástrojů – část 2" ve sloupci "Bugslayer" v "Časopis MSDN" na [MSDN Knihovna](http://go.microsoft.com/fwlink/?linkid=556) webu.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)