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

Veškerá paměť nad aktuální adresou RSP je považována za nestálou: operační systém nebo ladicí program může tuto paměť přepsat během relace ladění uživatele nebo obslužné rutiny přerušení. Proto musí být RSP vždy nastaveno před pokusem o čtení nebo zápis hodnot do bloku zásobníku.

Tato část popisuje přidělení prostoru zásobníku pro lokální proměnné a vnitřní objekt **alokace** .

## <a name="stack-allocation"></a>Přidělení zásobníku

Prolog funkce zodpovídá za přidělování prostoru zásobníku pro místní proměnné, uložené registry, parametry zásobníku a parametry registru.

Oblast parametru je vždy ve spodní části zásobníku (i když `alloca` je použita), takže bude vždy sousedící s návratovou adresou při jakémkoli volání funkce. Obsahuje alespoň čtyři položky, ale vždy dostatek místa pro všechny parametry, které jsou vyžadovány všemi funkcemi, které mohou být volány. Všimněte si, že prostor je vždy přidělen pro parametry registru, a to i v případě, že samotný parametr nejsou nikdy domů do zásobníku; Volaný je zaručeno, že prostor byl přidělen pro všechny jeho parametry. Pro argumenty registru jsou požadovány domovské adresy, takže je k dispozici souvislá oblast pro případ, že volaná funkce musí převzít adresu seznamu argumentů (va_list) nebo jednotlivého argumentu. Tato oblast také nabízí vhodné místo pro uložení argumentů registru během provádění převodu a jako možnost ladění (například usnadňuje vyhledání argumentů během ladění, pokud jsou uloženy na jejich domovské adrese v kódu prologu). I v případě, že volaná funkce má méně než 4 parametry, tyto 4 umístění zásobníku efektivně vlastní volaná funkce a může být použita volanou funkcí pro jiné účely kromě ukládání hodnot registru parametrů.  Volající proto nesmí ukládat informace v této oblasti zásobníku napříč voláním funkce.

Pokud je místo dynamicky přiděleno`alloca`() ve funkci, pak musí být nestálý registr použit jako ukazatel na rámec k označení základu pevné části zásobníku a tento registr musí být uložen a inicializován v prologu. Všimněte si, `alloca` že když se používá, volání na stejný volaný ze stejného volajícího můžou mít pro své parametry registru různé domovské adresy.

Zásobník bude vždy zarovnaný se 16 bajty, s výjimkou prologu (například po posunutí návratové adresy) a s výjimkou, kde jsou uvedeny v [typech funkcí](#function-types) pro určitou třídu funkcí rámce.

Následuje příklad rozložení zásobníku, kde funkce zavolá funkci, která není typu list B. funkce A Prolog již pro všechny parametry registru a zásobníku vyžadované B v dolní části zásobníku již přidělené místo. Volání přehraje zpáteční adresu a prolog B přidělí místo pro své místní proměnné, nestálé registry a prostor, který je potřeba pro volání funkcí. Pokud B používá `alloca`, je místo přiděleno mezi místní proměnná/nestálá oblast uložení registru a oblast zásobníku parametrů.

![Příklad převodu AMD](../build/media/vcamd_conv_ex_5.png "Příklad převodu AMD")

Když funkce B volá jinou funkci, vrátí se zpětná adresa hned pod domovskou adresou pro RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Konstrukce dynamické oblasti zásobníku parametrů

Pokud se použije ukazatel na rámec, existuje možnost, aby dynamicky vytvořila oblast zásobníku parametrů. To se v současnosti neprovádí v kompilátoru x64.

## <a name="function-types"></a>Typy funkcí

Existují v podstatě dva typy funkcí. Funkce, která vyžaduje rámec zásobníku, se nazývá *funkce rámce*. Funkce, která nevyžaduje rámec zásobníku, se nazývá *listová funkce*.

Rámec funkce je funkce, která přiděluje prostor zásobníku, volá jiné funkce, ukládá nestálé registry nebo používá zpracování výjimek. Vyžaduje taky zadání tabulky funkcí. Funkce Frame vyžaduje prolog a epilog. Funkce Frame může dynamicky přidělovat prostor zásobníku a může používat ukazatel na rámec. Funkce rámce má všechny schopnosti tohoto volání standardu, a to při jejich vyřazení.

Pokud funkce Frame nevolá jinou funkci, není nutné zarovnávat zásobník (odkazovaný v rámci [přidělení zásobníku](#stack-allocation)oddílu).

Listová funkce je ta, která nevyžaduje položku tabulky funkcí. Nemůže provádět změny v nestálých registrech, včetně RSP, což znamená, že nemůže volat žádné funkce nebo přidělovat místo v zásobníku. Může zůstat při spuštění zásobníku v nezarovnaném režimu.

## <a name="malloc-alignment"></a>nepřidělitelné přidružení

je zaručeno, že bude vracet paměť, [která je vhodně](../c-runtime-library/reference/malloc.md) zarovnána pro uložení libovolného objektu, který má zásadní zarovnání a který se může vejít do velikosti paměti, která je přidělena. *Základní zarovnání* je zarovnání, které je menší nebo rovno největšímu zarovnání, které je podporováno implementací bez specifikace zarovnání. (V Visual C++ se jedná o zarovnání, které je vyžadováno pro `double`nebo 8 bajtů. V kódu, který cílí na 64 bitů, je 16 bajtů.) Například přidělení čtyř bajtů by bylo zarovnáno na hranici, která podporuje libovolný čtyři bajty nebo menší objekty.

Visual C++ povoluje typy, které mají *rozšířené zarovnání*, které jsou také označovány jako typy *přerovnávání* . Například typy SSE [__m128](../cpp/m128.md) a `__m256`a typy deklarované pomocí `__declspec(align( n ))` , kde `n` je větší než 8, mají rozšířené zarovnání. Zarovnání paměti na hranici, která je vhodná pro objekt, který vyžaduje rozšířené zarovnání, není zaručeno `malloc`. Chcete-li přidělit paměť pro typy, které jsou zarovnaných nahoru, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) a související funkce.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musí být zarovnaná na 16 bajtů a navíc musí používat ukazatel na rámec.

Zásobník, který je přidělen, musí obsahovat místo pro parametry následného volání funkce, jak je popsáno v tématu [alokace zásobníku](#stack-allocation).

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
