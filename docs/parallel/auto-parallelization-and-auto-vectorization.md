---
title: "Automatická paralelizace a Automatická vektorizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b458dbe06bd69817c659c3bfec1d1ab7a216d1f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatická paralelizace a automatická vektorizace
Automatickou vektorizací a automatickou vektorizací jsou navrženy pro zvýšení výkonu automatické přinášejí smyčky v kódu.  
  
## <a name="auto-parallelizer"></a>Automatickou vektorizací  
 [/Qpar](../build/reference/qpar-auto-parallelizer.md) kompilátoru přepínač umožňuje *Automatická paralelizace* smyček do vašeho kódu. Pokud zadáte tento příznak beze změny existujícího kódu, kompilátor vyhodnotí kód najít cykly, které může mít užitek z paralelního zpracování. Vzhledem k tomu, že může najít cykly, které nemusíte dělat většinu práce a proto nebude využívat paralelizace a vzhledem k tomu, že všechny nepotřebné paralelizace může způsobit například fondu vláken, navíc synchronizace nebo jiné zpracování, které by mohlo způsobit snížení výkon místo zvýšení jeho, kompilátor je konzervativní při výběru cykly, které ji parallelizes. Představte si třeba v následujícím příkladu, ve kterém není znám horní mez smyčky v době kompilace:  
  
```cpp  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Protože `u` může být malá hodnota, kompilátor nebude automaticky paralelní této smyčky. Ale stále můžete ho paralelizovaná málo, protože víte, že `u` bude vždy velké. Pokud chcete povolit Automatická paralelizace, zadejte [#pragma loop(hint_parallel(n))](../preprocessor/loop.md), kde `n` je počet vláken učinit paralelní napříč. V následujícím příkladu se pokusí kompilátor paralelní smyčky mezi 8 vláken.  
  
```cpp  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Stejně jako u všech [direktivy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), syntaxe alternativní – Direktiva pragma `__pragma(loop(hint_parallel(n)))` je také podporována.  
  
 Existují některé cykly, které kompilátor nelze paralelní i v případě, že se má. Tady je příklad:  
  
```cpp  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
 Funkce `upper_bound()` může změnit pokaždé, když je volána. Vzhledem k tomu, že je známa horní mez, můžete kompilátor emitování diagnostiky zprávu, která vysvětluje, proč ji nelze paralelní této smyčky. Následující příklad ukazuje smyčku, která může být paralelizovaná několika málo, smyčku, která nemůže být paralelizovaná několika málo, syntaxe kompilátoru k použití v příkazovém řádku a výstup kompilátoru pro jednotlivé možnosti příkazového řádku:  
  
```cpp  
int A[1000];  
void test() {  
#pragma loop(hint_parallel(0))  
    for (int i=0; i<1000; ++i) {  
        A[i] = A[i] + 1;  
    }  
  
    for (int i=1000; i<2000; ++i) {  
        A[i] = A[i] + 1;  
    }  
}  
  
```  
  
 Kompilování pomocí tohoto příkazu:  
  
 **cl d:\myproject\mylooptest.cpp/O2 /Qpar /Qpar-sestavy: 1**  
  
 vypočítá tento výstup:  
  
 **---Analýza funkce: void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4): paralelizovaná málo smyčky**  
  
 Kompilování pomocí tohoto příkazu:  
  
 **cl d:\myproject\mylooptest.cpp/O2 /Qpar /Qpar-sestavy: 2**  
  
 vypočítá tento výstup:  
  
 **---Analýza funkce: void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4): paralelizovaná málo smyčky**   
 **d:\myproject\mytest.cpp(4): smyčky nejsou paralelizovaná málo z důvodu '1008.**  
  
 Všimněte si, ve výstupu rozdíl mezi dva různé [/Qpar-report (úroveň sestav automatickou vektorizací)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) možnosti. **/ Qpar-report: 1** výstupy paralelní zpracování zprávy pouze pro cykly, které jsou úspěšně paralelizovaná málo. **/ Qpar-sestavy: 2** výstupy paralelní zpracování zpráv pro obě parallelizations úspěšné a neúspěšné smyčky.  
  
 Další informace o kódech důvod a zpráv najdete v tématu [nástrojů pro vektorizaci a paralelní zpracování zprávy](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
## <a name="auto-vectorizer"></a>Automatickou vektorizací  
 Automatickou vektorizací analyzuje smyčky v kódu a používá vektoru registry a pokyny v cílovém počítači provést, pokud je to možné. Tím lze vylepšit výkon vašeho kódu. Kompilátor cílem pokynů SSE2 AVX a AVX2 v procesory Intel nebo AMD nebo NEÓNOVÁ pokyny procesory ARM podle požadavků [/arch](../build/reference/arch-minimum-cpu-architecture.md) přepínače.  
  
 Automatickou vektorizací může generovat jiné pokyny, než je zadáno v **/arch** přepínače. Tyto pokyny jsou dát kontrolu runtime a ujistěte se, že kód stále běží správně. Například když zkompilujete **/arch:SSE2**, může být vygenerované SSE4.2 pokyny. Kontrolu runtime ověří, že je k dispozici na cílový procesor SSE4.2 a přejde na jiný SSE4.2 verzi smyčky, pokud procesor nepodporuje tyto pokyny.  
  
 Ve výchozím nastavení je automatickou vektorizací povolené. Pokud chcete porovnat výkon kódu v rámci vectorization, můžete použít [#pragma loop(no_vector)](../preprocessor/loop.md) zakázat vectorization žádné danou smyčku.  
  
```  
  
      #pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 Stejně jako u všech [direktivy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), syntaxe alternativní – Direktiva pragma `__pragma(loop(no_vector))` je také podporována.  
  
 Jako s automatickou vektorizací, můžete zadat [/Qvec-report (úroveň sestav automatickou vektorizací)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) možnost příkazového řádku, buď sestavy úspěšně vectorized smyčky pouze –**/Qvec-sestavy: 1**– nebo úspěšně i neúspěšně vectorized smyčky –**/Qvec-sestavy: 2**).  
  
 Další informace o kódech důvod a zpráv najdete v tématu [nástrojů pro vektorizaci a paralelní zpracování zprávy](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
 Příklad znázorňující, jak funguje nástrojů pro vektorizaci v praxi, naleznete v části [projektu Austinu část 2 6: kulmy stránky](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## <a name="see-also"></a>Viz také  
 [smyčky](../preprocessor/loop.md)   
 [Paralelní programování v nativním kódu](http://go.microsoft.com/fwlink/p/?linkid=263662)   
 [/ Qpar (automatickou vektorizací)](../build/reference/qpar-auto-parallelizer.md)   
 [/ Qpar-report (úroveň sestav automatickou vektorizací)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [/ Qvec-report (úroveň sestav automatickou vektorizací)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [Zprávy nástrojů pro vektorizaci a paralelní zpracování](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)