---
title: vtordisp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b9341221ecafc6204a9f126ea50eb22d54ffec35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vtordisp"></a>vtordisp
**Konkrétní C++**  
  
 Řídí přidání skrytého členu vtordisp pro přesunutí vytvoření nebo zničení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### <a name="parameters"></a>Parametry  
 `push`  
 Uloží aktuální nastavení vtordisp do vnitřního zásobníku kompilátoru a nastaví nové nastavení vtordisp do parametru `n`.  Není-li parametr `n` zadán, aktuální nastavení vtordisp není změněno.  
  
 `pop`  
 Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru a obnoví nastavení vtordisp na odstraněnou hodnotu.  
  
 `n`  
 Určuje novou hodnotu nastavení vtordisp. Možnými hodnotami jsou 0, 1 a 2, které odpovídají možnostem kompilátoru /vd0, /vd1 a /vd2. Další informace najdete v tématu [/vd (zakázat posunutí konstrukcí)](../build/reference/vd-disable-construction-displacements.md).  
  
 `on`  
 Ekvivalentní `#pragma vtordisp(1)`.  
  
 `off`  
 Ekvivalentní `#pragma vtordisp(0)`.  
  
## <a name="remarks"></a>Poznámky  
 Direktivu pragma `vtordisp` lze použít pouze v kódu, který používá virtuální základy. Přepisuje-li odvozená třída virtuální funkci, kterou třída dědí z virtuální základní třídy, a pokud konstruktor nebo destruktor odvozené základní třídy tuto funkci volá pomocí ukazatele na virtuální základní třídu, kompilátor může do tříd s virtuálními základy zavést dodatečná skrytá pole `vtordisp`.  
  
 Direktiva pragma `vtordisp` ovlivňuje rozložení tříd uvedených za ní. Pro kompletní moduly určují možnosti /vd0, /vd1 a /vd2 stejné chování. Zadáním hodnoty `0` nebo `off` jsou skryté členy `vtordisp` potlačeny. Členy `vtordisp` vypněte pouze v případě, že neexistuje situace, kdy by konstruktory a destruktory třídy volaly virtuální funkce objektu, na který ukazuje ukazatel `this`.  
  
 Zadáním výchozí hodnoty `1` nebo `on` je povoleno použití skrytých členů `vtordisp` tam, kde jsou zapotřebí.  
  
 Určení `2` umožňuje skrytého `vtordisp` členy pro všechny virtuální základů s virtuální funkce.  `vtordisp(2)`může být potřeba zajistit správné výkon `dynamic_cast` na objekt částečně zkonstruovat. Další informace najdete v tématu [upozornění kompilátoru (úroveň 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).  
  
 Direktiva `#pragma vtordisp()` bez argumentů obnoví nastavení vtordisp na počáteční nastavení.  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)