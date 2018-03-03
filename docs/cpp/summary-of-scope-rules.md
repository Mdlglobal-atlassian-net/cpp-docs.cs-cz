---
title: Souhrn pravidel rozsahu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c530a586ca2b8b70cfdc967c354738e93435f20c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-scope-rules"></a>Souhrn pravidel rozsahu
Použití názvu musí být v daném oboru jednoznačné (až do místa, kde je určeno přetížení). Pokud název označuje funkce, musí být jednoznačné s ohledem na počet a typ parametry funkce. Pokud název zůstane jednoznačným, [přístup ke členu](../cpp/member-access-control-cpp.md) pravidla.  
  
## <a name="constructor-initializers"></a>Inicializátory konstruktoru  
 Inicializátory konstruktoru (popsané v [inicializace základů a členů](http://msdn.microsoft.com/en-us/2f71377e-2b6b-49da-9a26-18e9b40226a1)) jsou vyhodnocovány v oboru nejkrajnější blok konstruktor, pro které jsou uvedené. Proto že můžete použít názvy parametrů v konstruktoru.  
  
## <a name="global-names"></a>Globální názvy  
 Název objektu, funkce nebo enumerátoru je globální, pokud je zaveden mimo jakoukoli funkci nebo třídu nebo je umístěn za předponu globálního unárního operátoru oboru (`::`) a není-li použit ve spojení s některým z těchto binárních operátorů:  
  
-   Rozlišení oboru (`::`)  
  
-   Výběr členů pro objekty a odkazy (**.**)  
  
-   Výběr členů pro ukazatele (**->**)  
  
## <a name="qualified-names"></a>Kvalifikované názvy  
 Názvy použité s binárním operátorem rozlišení oboru (`::`) jsou označovány jako „kvalifikované názvy“. Název zadaný po binárním operátoru rozlišení oboru musí být členem třídy uvedené na levé straně operátoru nebo členem její základní třídy.  
  
 Názvy zadané po výběru členů operátoru (**.** nebo  **->** ) musí být členy typu třídy objektu zadaného na levé straně operátoru nebo členové jeho základní třídy. Názvy zadané na pravé straně operátoru výběru členů (**->**) může být také objekty jiné třídy typu, za předpokladu, že na levé straně  **->**  je objekt třídy a aby třída definuje operátor přetížené výběr členů (**->**), se vyhodnocuje ukazatel na jiný typ třídy. (Toto přidělení je podrobněji popsána v [přístup ke členu třída](../cpp/member-access.md).)  
  
 Kompilátor vyhledá názvy v následujícím pořadí a toto hledání zastaví, když je název nalezen:  
  
1.  Rozsah aktuálního bloku, pokud je název použit uvnitř funkce, v opačném případě globální rozsah.  
  
2.  I přes vymezeném oboru bloku včetně oboru nejzevnější funkce (která zahrnuje parametry funkce).  
  
3.  Pokud je název použit uvnitř členské funkce, je název vyhledán v rozsahu třídy.  
  
4.  Název je vyhledán v základních třídách této třídy.  
  
5.  Je prohledán nadřazený rozsah vnořené třídy (pokud existuje) a její základní třídy. Hledání pokračuje, dokud není prohledán vnější nadřazený rozsah třídy.  
  
6.  Je prohledán globální rozsah.  
  
 Avšak toto pořadí hledání lze upravit následujícím způsobem:  
  
1.  Názvy začínající `::` vynutí, aby hledání začalo v globálním rozsahu.  
  
2.  Názvy před sebou **– třída**, `struct`, a **– typ union** klíčová slova vynutit kompilátoru, aby vyhledávají se pouze **třída**, `struct`, nebo **sjednocení**  názvy.  
  
3.  Názvy na levé straně operátor řešení rozsahu (`::`) může být pouze **třída**, `struct`, **obor názvů**, nebo **sjednocení** názvy.  
  
 Pokud název odkazuje na nestatický člen, ale je použit ve statické členské funkci, je vygenerována chybová zpráva. Podobně, pokud název odkazuje žádné nestatické členské v nadřazených tříd, chybová zpráva je vygenerovat, protože závorkách třídy nemají obklopuje třída **to** ukazatele.  
  
## <a name="function-parameter-names"></a>Názvy parametrů funkce  
 Názvy parametrů funkce v definice funkcí se považuje za v oboru bloku nejkrajnější funkce. Proto jsou místními názvy a dostanou se mimo rozsah, když funkce skončí.  
  
 Názvy parametrů funkce v deklaracích – funkce (prototypy) jsou v oboru místní deklarace a se dostala mimo rozsah na konci tohoto prohlášení.  
  
 Výchozí parametry jsou v oboru parametr, pro které jsou výchozí, jak je popsáno v předchozí dva odstavce. Avšak nemají přístup k lokálním proměnným nebo nestatickým členům třídy. Výchozí parametry jsou vyhodnocovány v místě volání funkce, ale jsou vyhodnocovány v deklaraci funkce původní obor. Výchozí parametry pro členské funkce, proto jsou vždy vyhodnoceny v rozsahu třídy.  
  
## <a name="see-also"></a>Viz také  
 [Dědičnost](../cpp/inheritance-cpp.md)