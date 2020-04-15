---
title: x64 – použití zásobníku
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b598c33fbdd56630ca3e5ef0da551f38a73baa26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335531"
---
# <a name="x64-stack-usage"></a>x64 – použití zásobníku

Všechny paměti mimo aktuální adresu RSP je považován za nestálý: Operační systém nebo ladicí program může přepsat tuto paměť během relace ladění uživatele nebo obslužné rutiny přerušení. Proto RSP musí být vždy nastavena před pokusem o čtení nebo zápis hodnot do rámce zásobníku.

Tato část popisuje přidělení místa zásobníku pro místní proměnné a **alloca** vnitřní.

## <a name="stack-allocation"></a>Přidělení zásobníku

Prolog funkce je zodpovědný za přidělování místa v zásobníku pro místní proměnné, uložené registry, parametry zásobníku a parametry registru.

Oblast parametrů je vždy v dolní části `alloca` zásobníku (i v případě, že se používá), takže bude vždy přilehlé k zpáteční adrese během volání jakékoli funkce. Obsahuje alespoň čtyři položky, ale vždy dostatek místa pro uložení všech parametrů potřebných pro všechny funkce, které mohou být volány. Všimněte si, že místo je vždy přiděleno pro parametry registru, i v případě, že parametry samotné nejsou nikdy umístěny do zásobníku; volaný je zaručeno, že prostor byl přidělen pro všechny jeho parametry. Adresy domů jsou vyžadovány pro argumenty registru, takže souvislá oblast je k dispozici v případě, že volaná funkce potřebuje adresu seznamu argumentů (va_list) nebo jednotlivého argumentu. Tato oblast také poskytuje vhodné místo pro uložení argumentů registru během spuštění thunk a jako možnost ladění (například usnadňuje nalezení argumentů během ladění, pokud jsou uloženy na svých domovských adresách v kódu prologu). I v případě, že volaná funkce má méně než 4 parametry, jsou tato 4 umístění zásobníku efektivně vlastněna volanou funkcí a může být použita volanou funkcí pro jiné účely kromě ukládání hodnot registru parametrů.  Volající tedy nemusí ukládat informace v této oblasti zásobníku přes volání funkce.

Pokud je ve funkci`alloca`dynamicky přiděleno místo ( ) , musí být jako ukazatel rámce použit trvalý registr, který označuje základnu pevné části zásobníku, a tento registr musí být uložen a inicializován v prologu. Všimněte `alloca` si, že při použití volání stejného volaní od stejného volajícího může mít různé adresy domů pro jejich parametry registru.

Zásobník bude vždy udržována 16 bajt zarovnaný, s výjimkou v rámci prologu (například po vrácení adresy je posunuta) a s výjimkou případů, kdy je uvedeno v [typech funkcí](#function-types) pro určitou třídu funkcí rámce.

Následuje příklad rozložení zásobníku, kde funkce A volá funkci bez listu B. Prolog funkce A již přidělil místo pro všechny parametry registru a zásobníku vyžadované B v dolní části zásobníku. Volání pushy zpáteční adresu a Prolog B přiděluje místo pro své místní proměnné, stálé registry a místo potřebné pro volání funkcí. Pokud B `alloca`používá , je místo přiděleno mezi místní proměnnou/stálé hospo-

![Příklad konverze AMD](../build/media/vcamd_conv_ex_5.png "Příklad konverze AMD")

Když funkce B volá jinou funkci, zpáteční adresa je posunuta těsně pod domovskou adresu pro RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Konstrukce oblasti zásobníku dynamických parametrů

Pokud je použit ukazatel rámce, existuje možnost dynamicky vytvořit oblast zásobníku parametrů. To není aktuálně provedeno v kompilátoru x64.

## <a name="function-types"></a>Typy funkcí

Existují v podstatě dva typy funkcí. Funkce, která vyžaduje rámec zásobníku, se nazývá *funkce rámce*. Funkce, která nevyžaduje rámec zásobníku se nazývá *listová funkce*.

Funkce rámce je funkce, která přiděluje místo v zásobníku, volá další funkce, ukládá stálé registry nebo používá zpracování výjimek. Vyžaduje také položku tabulky funkcí. Funkce rámce vyžaduje prolog a epilog. Funkce rámce může dynamicky přidělit místo v zásobníku a může využívat ukazatel rámce. Funkce rámce má k dispozici všechny možnosti tohoto volajícího standardu.

Pokud funkce rámce nevolá jinou funkci, není nutné zarovnat zásobník (odkazuje v [části přidělení zásobníku).](#stack-allocation)

Funkce list je funkce, která nevyžaduje položku tabulky funkce. Nemůže provádět změny v žádné stálé registry, včetně RSP, což znamená, že nemůže volat žádné funkce nebo přidělit místo v zásobníku. Je povoleno ponechat zásobníku nezarovnané při jeho spuštění.

## <a name="malloc-alignment"></a>malloc zarovnání

[malloc](../c-runtime-library/reference/malloc.md) je zaručeno, že vrátí paměť, která je vhodně zarovnána pro ukládání libovolného objektu, který má základní zarovnání a které by se vešlo do množství paměti, která je přidělena. *Základní zarovnání* je zarovnání, které je menší nebo rovno největší zarovnání, které je podporováno implementací bez specifikace trasy. (V jazyce Visual C++ se jedná o `double`zarovnání, které je požadováno pro nebo 8 bajtů. V kódu, který cílí na 64bitové platformy, je to 16 bajtů.) Například přidělení čtyř bajtů by bylo zarovnáno na hranici, která podporuje jakýkoli čtyřbajtový nebo menší objekt.

Visual C++ umožňuje typy, které mají *rozšířené zarovnání*, které jsou také známé jako *příliš zarovnané* typy. Například Typy SSE [__m128](../cpp/m128.md) __m128 `__m256`a , a typy, `n` které jsou deklarovány pomocí kde `__declspec(align( n ))` je větší než 8, mají rozšířené zarovnání. Zarovnání paměti na hranici, která je vhodná pro `malloc`objekt, který vyžaduje rozšířené zarovnání, není zaručeno . Chcete-li přidělit paměť pro přerovnané typy, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) a související funkce.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musí být zarovnán 16 bajtů a navíc nutné použít ukazatel rámce.

Zásobník, který je přidělen musí obsahovat prostor za ním pro parametry následně volal funkce, jak je popsáno v [přidělení zásobníku](#stack-allocation).

## <a name="see-also"></a>Viz také

[softwarové konvence x64](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
