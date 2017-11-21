---
title: "try-finally – Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c76062799a0939ad86556c8e6718e94f2a3397e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="try-finally-statement-c"></a>try-finally – příkaz (C)
**Konkrétní Microsoft**  
  
 `try-finally` Příkaz je rozšíření Microsoft pro jazyk C, která umožňuje aplikacím zaručit spuštění kódu čištění, když dojde k přerušení spuštění bloku kódu. Čištění se skládá z úlohy, jako jsou rušení přidělení paměti, zavírání souborů a uvolněním popisovače souborů. `try-finally` Příkaz je zvláště užitečná pro rutiny, které mají několika místech, kde je provedena kontrola pro chybu, která by mohla způsobovat předčasné vrátit z rutiny.  
  
 *try-finally – příkaz*:  
 **__try***složené – příkaz*   
  
 **__finally***složené – příkaz*   
  
 Složený příkaz po `__try` části chráněného je klauzule. Složený příkaz po `__finally` je klauzule obslužné rutiny ukončení. Obslužná rutina určuje sadu akcí, které spustit, když je byl ukončen části chráněného, zda části chráněného je byl ukončen výjimku (abnormální ukončení), nebo standardní patří prostřednictvím (normální ukončení).  
  
 Řízení dosáhnou `__try` příkaz podle jednoduchý sekvenční provádění (patří prostřednictvím). Pokud vstoupí do ovládacího prvku `__try` prohlášení, jeho přidruženou obslužnou rutinu stane aktivní. Provádění pokračuje následujícím způsobem:  
  
1.  Chráněná část je spuštěna.  
  
2.  Obslužné rutiny ukončení je volána.  
  
3.  Po dokončení obslužné rutiny ukončení pokračuje po spuštění `__finally` příkaz. Bez ohledu na to, jak budou dát části končí (například prostřednictvím `goto` příkaz z chráněného obsahu nebo prostřednictvím `return` příkaz), obslužné rutiny ukončení je spuštěn před toku řízení přesune mimo chráněného oddílu.  
  
 `__leave` – Klíčové slovo je platný v rámci `try-finally` příkaz bloku. Účinek `__leave` je chcete přejít na konci `try-finally` bloku. Obslužné rutiny ukončení se spustí okamžitě. I když `goto` příkaz lze použít k dosažení stejného výsledku `goto` příkaz způsobuje uvolnění zásobníku. `__leave` Příkaz je efektivnější, protože nezahrnuje uvolnění zásobníku.  
  
 Ukončení `try-finally` příkaz pomocí `return` příkaz nebo `longjmp` běhové funkce považuje za abnormální ukončení. Není povolen přejít do `__try` prohlášení, ale právní přejít od jednoho. Všechny `__finally` příkazy, které jsou aktivní mezi bodem odeslání a cíl musí být spuštěn. To se označuje jako "místní unwind".  
  
 Obslužné rutiny ukončení není volána, pokud je tento proces se ukončil při provádění `try-finally` příkaz.  
  
> [!NOTE]
>  Strukturované zpracování výjimek pracuje s C a C++ zdrojové soubory. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování mechanismus výjimek C++ je také mnohem víc možností, v tom, že ho můžete zpracování výjimek libovolného typu.  
  
> [!NOTE]
>  Pro C++ – programy je třeba použít zpracovávání výjimek v jazyce C++ místo strukturované zpracování výjimek. Další informace najdete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *referenční příručka jazyka C++*.  
  
 Podívejte se příklad [zkuste-except – příkaz](../c-language/try-except-statement-c.md) zobrazíte jak `try-finally` příkaz funguje.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [try-finally – příkaz](../cpp/try-finally-statement.md)