---
title: Přidělení zásobníku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 514b20847f588dab7a5c205be36c1fbd725df17d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stack-allocation"></a>Přidělení zásobníku
Prolog funkce zodpovídá za přidělování místa v zásobníku pro místní proměnné, – uložené registry, zásobníku parametrů a parametry registru.  
  
 Oblast parametru je vždy v dolní části zásobníku (i když je použita funkce alloca) tak, aby ho bude vždy přiléhající návratové adresy během volání žádné funkce. Obsahuje alespoň čtyři záznamy, ale vždycky potřeboval dostatkem místa pro všechny parametry funkcí, které může být volána. Všimněte si, že je vždy přiděleno místo pro parametry registru, i v případě, že jsou parametry sami nikdy adresami zásobníku; Volaný záruku, že je pro všechny její parametry přiděleno místo. Domovské adresy jsou požadovány pro argumenty registru tak souvislý oblasti je dostupná v případě, že volaná funkce musí vzít na adresu seznamu argumentů (va_list) nebo jednotlivé argument. Tato oblast představuje také vhodné místo pro uložení argumentů registru během provádění převodu a jako možnost ladění (například umožňuje argumentům snadno najít během ladění, pokud jsou uložené na jejich domovských adresách v kódu prologu). I v případě volaná funkce obsahuje méně než 4 parametry, tyto 4 zásobníku umístění jsou efektivně vlastněny volaná funkce a může být používán volaná funkce pro jiné účely, než uložení hodnot parametrů registru.  Proto nemůže volající uložit informace v této oblasti zásobníku prostřednictvím volání funkce.  
  
 Pokud místo dynamicky přiděluje (alloca –) ve funkci, stálý registr musí být použit jako ukazatel na rámec k označení základu pevné části zásobníku a této registrace musí být uloženy a v prologu inicializovat. Všimněte si, že při použití alloca – volání stejného volaného ze stejné volající může mít různé domovské adresy pro své parametry registru.  
  
 V zásobníku se vždycky zachovají s 16 bajtů zarovnán, kromě v rámci prologu (například po návratové adresy) a s výjimkou uvedenou v [typy funkce](../build/function-types.md) některých tříd rámcových funkcí.  
  
 Toto je příklad rozložení zásobníku, kde funkce A volání mimo úroveň listu funkce prolog B. funkce A již přidělené místo pro všechny registrace a zásobníku parametrů požadovaných b v dolní části zásobníku. Volání posune návratovou adresu a na B prologu přiděluje místo pro jeho místní proměnné, stálé registry a prostor potřebný pro jeho volání funkcí. Pokud B používá alloca –, je místo přidělené mezi oblasti místním registru proměnné/stálé úložné a oblasti zásobníku parametrů.  
  
 ![Příklad převodu AMD](../build/media/vcamd_conv_ex_5.png "vcAmd_conv_ex_5")  
  
 Když funkce B volá jinou funkci, zpětná adresa je posunuta domovské adresy pro RCX.  
  
## <a name="see-also"></a>Viz také  
 [Použití zásobníku](../build/stack-usage.md)