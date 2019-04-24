---
title: x64 zásobníku využití
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 902e4304ac124be46c6edf0860118dc522b34890
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314813"
---
# <a name="x64-stack-usage"></a>x64 zásobníku využití

Všechny paměti větší než aktuální adresu RSP se považuje za volatile: Operační systém nebo ladicího programu, mohou přepsat tuto paměť během uživatelské relace ladění nebo obslužné rutiny přerušení. RSP proto musí být vždycky nastavená před pokusem o čtení nebo zápisu hodnot do bloku zásobníku.

Tato část pojednává o přidělení zásobníku prostoru pro místní proměnné a **alloca** vnitřní.

## <a name="stack-allocation"></a>Přidělení zásobníku

Prologu funkce zodpovídá za přidělování místa v zásobníku pro místní proměnné, uložené registry, parametry zásobníku a parametry registru.

Oblasti parametrů je vždy v dolní části zásobníku (i v případě `alloca` se používá), takže ho bude vždy sousední na návratovou adresu během každé volání funkce. Obsahuje alespoň čtyři položky, ale vždy dostatek místa pro všechny parametry vyžadované všechny funkce, které může být volána. Všimněte si, že je vždy přiděleno místo pro parametry registru, i když parametrů samotných jsou nikdy adresami v zásobníku; Volaný je zaručeno, že bylo přiděleno místo pro všechny její parametry. Poštovní adresy jsou požadované pro argumenty registru, takže souvislých oblasti je dostupná v případě, že volaná funkce je potřeba převzít adresu proměnné seznamu argumentů (va_list) nebo jednotlivým argument. Tato oblast také poskytuje praktické místo k uložení argumentů registru při provádění převodu a jako možnost ladění (například umožňuje argumenty snadné najít během ladění, pokud se ukládají na své domovské adresy v kódu prologu). I v případě, že volaná funkce má méně než 4 parametry, umístění těchto 4 zásobníku jsou efektivně vlastní volané funkce a může využívat k jiným účelům kromě uložení hodnot parametrů registru volané funkce.  Proto nemusí volající uložit informace v této oblasti zásobníku ve volání funkce.

Pokud místo dynamicky přidělit (`alloca`) ve funkci, pak stálé registru a musí být jako ukazatel na rámec k označení základní pevnou součástí zásobníku, který registrace musí být uloženy a inicializovat v prologu. Všimněte si, že `alloca` se používá, volání stejné volaný ze stejné volající může mít různé domovské adresy pro své parametry registru.

Zásobníku se vždycky zachovají s 16 bajtů zarovnána, s výjimkou v rámci prolog (například po zpáteční adresu) a s výjimkou uvedenou v [typy funkcí](#function-types) třídy funkce rámce.

Následující je příklad rozložení zásobníku, kde funkce A volání mimo úroveň listu funkce prolog B. funkce A již přidělené místo pro všechny registrace a zásobníku parametrů vyžadovaných B v dolní části zásobníku. Posune návratovou adresu volání a B prologu přiděluje místo pro své místní proměnné, stálé registry a místa potřebného pro jeho volání funkcí. Pokud B používá `alloca`, místo je rozdělena mezi místní proměnné nebo stálé registr uložit oblasti a oblasti zásobníku parametrů.

![Příklad převodu AMD](../build/media/vcamd_conv_ex_5.png "Příklad převodu AMD")

Když se funkce B volá jinou funkci, převede se zpětná adresa pro RCX pod adresa domů.

## <a name="dynamic-parameter-stack-area-construction"></a>Zásobník konstrukce dynamické oblasti parametrů

Pokud se používá ukazatel na rámec, existuje možnost k vytvoření dynamické oblasti zásobníku parametrů. Není to aktuálně x64 kompilátoru.

## <a name="function-types"></a>Typy funkcí

V podstatě existují dva typy funkcí. Volá funkci, která vyžaduje blok zásobníku *rámec funkce*. Je volána funkce, která nevyžaduje blok zásobníku *listové funkce*.

Funkce rámce je funkce, která přiděluje místo v zásobníku volání dalších funkcí, ukládá stálé registry a používá zpracování výjimek. Také vyžaduje záznam tabulky funkcí. Funkce rámce vyžaduje prologu a epilogu. Bloková funkce můžete dynamicky přidělit místo v zásobníku a můžete použít ukazatel na rámec. Funkce rámce obsahuje všechny funkce tohoto volání standardní k dispozici.

Pokud funkce rámce nevolá jinou funkci, není to nutné k zarovnání zásobníku (odkazováno v oddíle [přidělení zásobníku](#stack-allocation)).

Funkce typu list je ten, který nevyžaduje, aby záznam tabulky funkcí. Ho nemůže provádět změny libovolné stálé registry, včetně RSP, což znamená, že nelze volat jakékoli funkce nebo přidělit místo v zásobníku. Je povoleno ji nechte nezarovnaných zásobníku během provádění.

## <a name="malloc-alignment"></a>malloc – zarovnání

[malloc](../c-runtime-library/reference/malloc.md) je zaručeno, že vrací paměť, která je vhodně zarovnaný pro uložení libovolného objektu, který má základní zarovnání a který může podle množství paměti, která je přidělena. A *základní zarovnání* je zarovnání menší než nebo rovno největšímu zarovnání, které je podporováno implementací bez specifikace zarovnání. (V jazyce Visual C++, je toto zarovnání, které je vyžadováno pro `double`, nebo 8 bajtů. V kódu, který cílí na 64bitové platformy je 16 bajtový.) Například přidělení čtyř bajtů by mělo být zarovnáno na hranici, která podporuje libovolný čtyřbajtový nebo menší objekt.

Visual C++ umožňuje typy, které mají *rozšířené zarovnání*, která se také označují jako *nadbytečně zarovnané* typy. Například typy SSE [__m128](../cpp/m128.md) a `__m256`a typy, které jsou deklarovány pomocí `__declspec(align( n ))` kde `n` je větší než 8, mají rozšířené zarovnání. Zarovnání paměti na hranici, která je vhodná pro objekt, který vyžaduje rozšířené zarovnání není zaručeno, že podle `malloc`. Chcete-li přidělit paměť pro nadbytečně zarovnané typy, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) a související funkce.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musí být 16 bajtů zarovnána a kromě toho budete muset použít ukazatel na rámec.

Zásobník, který je přidělen musí obsahovat místa po něm pro parametry, které následně volané funkce, jak je popsáno v [přidělení zásobníku](#stack-allocation).

## <a name="see-also"></a>Viz také:

[x64 – softwarové konvence](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
