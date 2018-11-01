---
title: Přidělení zásobníku
ms.date: 11/04/2016
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
ms.openlocfilehash: 23b22491a6eeac078f551a6513a7ecad4be43fe9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478818"
---
# <a name="stack-allocation"></a>Přidělení zásobníku

Prologu funkce zodpovídá za přidělování místa v zásobníku pro místní proměnné, uložené registry, parametry zásobníku a parametry registru.

Oblasti parametrů je vždy v dolní části zásobníku (i v případě, že je použita funkce alloca), takže ho bude vždy sousední na návratovou adresu během každé volání funkce. Obsahuje alespoň čtyři položky, ale vždy dostatek místa pro všechny parametry vyžadované všechny funkce, které může být volána. Všimněte si, že je vždy přiděleno místo pro parametry registru, i když parametrů samotných jsou nikdy adresami v zásobníku; Volaný je zaručeno, že bylo přiděleno místo pro všechny její parametry. Poštovní adresy jsou požadované pro argumenty registru, takže souvislých oblasti je dostupná v případě, že volaná funkce je potřeba převzít adresu proměnné seznamu argumentů (va_list) nebo jednotlivým argument. Tato oblast také poskytuje praktické místo k uložení argumentů registru při provádění převodu a jako možnost ladění (například umožňuje argumenty snadné najít během ladění, pokud se ukládají na své domovské adresy v kódu prologu). I v případě, že volaná funkce má méně než 4 parametry, umístění těchto 4 zásobníku jsou efektivně vlastní volané funkce a může využívat k jiným účelům kromě uložení hodnot parametrů registru volané funkce.  Proto nemusí volající uložit informace v této oblasti zásobníku ve volání funkce.

Pokud se místo přiděluje dynamicky (alloca) ve funkci, stálé registr musí být použit jako ukazatel na rámec, k označení základní pevnou součástí do zásobníku a registru musí být uloženy a inicializovat v prologu. Všimněte si, že při použití funkce alloca volání stejné volaný ze stejné volající může mít různé domovské adresy pro své parametry registru.

Zásobníku se vždycky zachovají s 16 bajtů zarovnána, s výjimkou v rámci prolog (například po zpáteční adresu) a s výjimkou uvedenou v [typy funkcí](../build/function-types.md) třídy funkce rámce.

Následující je příklad rozložení zásobníku, kde funkce A volání mimo úroveň listu funkce prolog B. funkce A již přidělené místo pro všechny registrace a zásobníku parametrů vyžadovaných B v dolní části zásobníku. Posune návratovou adresu volání a B prologu přiděluje místo pro své místní proměnné, stálé registry a místa potřebného pro jeho volání funkcí. Pokud B používá alloca, je mezi místní proměnné nebo stálé registr uložit oblasti a oblasti zásobníku parametrů přidělené místo.

![Příklad převodu AMD](../build/media/vcamd_conv_ex_5.png "Příklad převodu AMD")

Když se funkce B volá jinou funkci, převede se zpětná adresa pro RCX pod adresa domů.

## <a name="see-also"></a>Viz také

[Použití zásobníku](../build/stack-usage.md)