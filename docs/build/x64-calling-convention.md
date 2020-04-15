---
title: x64 – konvence volání
description: Podrobnosti o výchozí konvence volání x64 ABI.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335132"
---
# <a name="x64-calling-convention"></a>x64 – konvence volání

Tato část popisuje standardní procesy a konvence, které jedna funkce (volající) používá k volání do jiné funkce (volaný) v kódu x64.

## <a name="calling-convention-defaults"></a>Výchozí nastavení konvence volání

Binární rozhraní aplikace x64 (ABI) používá ve výchozím nastavení konvenci rychlého volání čtyř registrů. Místo je přiděleno v zásobníku volání jako úložiště stínů pro volané k uložení těchto registrů. Existuje přísná shoda 1:1 mezi argumenty volání funkce a registry používané pro tyto argumenty. Každý argument, který se nevejde do 8 bajtů nebo není 1, 2, 4 nebo 8 bajtů, musí být předán odkazem. Jeden argument je nikdy rozložena do více registrů. Zásobník registru x87 je nepoužívaný a může být používán volava, ale musí být považován za volatilní napříč voláními funkcí. Všechny operace s plovoucí desetinnou desetinnou tázkem se provádějí pomocí registrů 16 XMM. Celé číslo argumenty jsou předány v registrech RCX, RDX, R8 a R9. Argumenty s plovoucí desetinnou tázkem jsou předány v xmm0l, xmm1l, xmm2l a xmm3l. 16bajtové argumenty jsou předány odkazem. Předávání parametrů je podrobně popsáno v [parametru Předávání](#parameter-passing). Kromě těchto registrů jsou RAX, R10, R11, XMM4 a XMM5 považovány za volatilní. Všechny ostatní registry jsou nestálé. Využití registru je podrobně zdokumentováno v [registru Využití](../build/x64-software-conventions.md#register-usage) a Volající [/ Volaný uložené registry](#callercallee-saved-registers).

Pro prototypové funkce jsou všechny argumenty před předáním převedeny na očekávané volané typy. Volající je zodpovědný za přidělení místa pro parametry volaný a musí vždy přidělit dostatek místa pro uložení čtyř parametrů registru, i v případě, že volaný nepřevezme tolik parametrů. Tato konvence zjednodušuje podporu pro neprototypované funkce jazyka C a funkce vararg C/C++. Pro funkce vararg nebo unprototyped musí být všechny hodnoty s plovoucí desetinnou desetinnou tísní duplikovány v odpovídajícím registru pro obecné účely. Všechny parametry za první čtyři musí být uloženy v zásobníku po stínové úložiště před voláním. Podrobnosti o funkci Vararg lze nalézt v [Varargs](#varargs). Neprototypové informace o funkcích jsou podrobně popsány v [neprototypové funkci](#unprototyped-functions).

## <a name="alignment"></a>Zarovnání

Většina struktur je zarovnána s jejich přirozeným zarovnáním. Primární výjimky jsou ukazatel `malloc` zásobníku nebo `alloca` paměti, které jsou zarovnány do 16 bajtů za účelem podpory výkonu. Zarovnání nad 16 bajtů musí být provedeno ručně, ale vzhledem k tomu, že 16 bajtů je společná velikost trasy pro operace XMM, tato hodnota by měla fungovat pro většinu kódu. Další informace o rozložení a zarovnání struktury naleznete v tématu [Typy a úložiště](../build/x64-software-conventions.md#types-and-storage). Informace o rozložení zásobníku naleznete v tématu [x64 využití zásobníku](../build/stack-usage.md).

## <a name="unwindability"></a>Unwindability

Funkce listu jsou funkce, které nemění žádné nestálé registry. Nelistová funkce může změnit nevolatilní RSP, například voláním funkce nebo přidělením dalšího místa zásobníku pro místní proměnné. Chcete-li obnovit nestálé registry při zpracování výjimky, musí být funkce bez listu označeny statickými daty, která popisují, jak správně uvolnit funkci na libovolné instrukci. Tato data jsou uložena jako *pdata*, nebo procedura data, která zase odkazuje na *xdata*, zpracování dat výjimky. Xdata obsahuje unwinding informace a může přejděte na další pdata nebo funkce obslužné rutiny výjimky. Prologs a epilogs jsou velmi omezené, takže mohou být správně popsány v xdata. Ukazatel zásobníku musí být zarovnán na 16 bajtů v libovolné oblasti kódu, která není součástí epilogu nebo prologu, s výjimkou funkcí listu. Listové funkce lze odvíjet jednoduše simulací návratu, takže pdata a xdata nejsou vyžadovány. Podrobnosti o správné struktuře funkčních prologů a epilogů najdete v [tématu x64 prolog a epilog](../build/prolog-and-epilog.md). Další informace o zpracování výjimek a zpracování výjimek a odvíjení dat a xdata naleznete v [tématu zpracování výjimek x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Předávání parametrů

První čtyři celé číslo argumenty jsou předány v registrech. Celočíselné hodnoty jsou předávány v pořadí zleva doprava v RCX, RDX, R8 a R9. Argumenty pět a vyšší jsou předány v zásobníku. Všechny argumenty jsou v registrech odůvodněny právem, takže volaný může ignorovat horní bity registru a získat přístup pouze k části registru nezbytné.

Všechny argumenty s plovoucí desetinnou a dvojitou přesností v prvních čtyřech parametrech jsou předány v XMM0 - XMM3, v závislosti na pozici. Celé číslo registruje RCX, RDX, R8 a R9, které by se normálně používaly pro tyto pozice, jsou ignorovány, s výjimkou argumentů varargs. Podrobnosti viz [Varargs](#varargs). Podobně registry XMM0 - XMM3 jsou ignorovány, pokud je odpovídající argument celočíselný nebo ukazatel typu.

[__m128](../cpp/m128.md) typy, pole a řetězce nejsou nikdy předány okamžitou hodnotou. Místo toho je předán ukazatel do paměti přidělené volajícím. Struktury a sjednocení velikosti 8, 16, 32 nebo 64 bitů a __m64 typů jsou předávány, jako by se jednalo o celá čísla stejné velikosti. Struktury nebo sjednocení jiných velikostí jsou předány jako ukazatel paměti přidělené volajícím. Pro tyto agregační typy \_předané jako ukazatel, včetně _m128, volající přidělené dočasné paměti musí být zarovnaný 16 bajtů.

Vnitřní funkce, které nepřidělují místo v zásobníku a nevolají jiné funkce, někdy používají jiné nestálé registry k předání dalších argumentů registru. Tato optimalizace je možné těsné vazby mezi kompilátoru a implementace vnitřní funkce.

Volaný je zodpovědný za ukládání parametrů registru do jejich stínového prostoru v případě potřeby.

Následující tabulka shrnuje, jak jsou předávané parametry:

|Typ parametru|Jak prošel|
|--------------------|----------------|
|Plovoucí desetinná čárka|První 4 parametry - XMM0 až XMM3. Jiní předávali zásobník.|
|Integer|První 4 parametry - RCX, RDX, R8, R9. Jiní předávali zásobník.|
|Agregáty (8, 16, 32 nebo 64 bitů) a __m64|První 4 parametry - RCX, RDX, R8, R9. Jiní předávali zásobník.|
|Agregáty (ostatní)|Podle ukazatele. První 4 parametry předané jako ukazatele v RCX, RDX, R8 a R9|
|__m128|Podle ukazatele. První 4 parametry předané jako ukazatele v RCX, RDX, R8 a R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Příklad argumentu předávání 1 - všechna celá čísla

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Příklad argumentu předávání 2 - všechny plováky

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Příklad argumentu předávání 3 - smíšené ints a plováky

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Příklad argumentu předání 4 \_-__m64, _m128 a agregací

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Vararg

Pokud parametry jsou předány prostřednictvím varargs (například tři tečky argumenty), pak normální parametr registru předávání konvence platí, včetně rozlití páté a následné argumenty zásobníku. Je to callee odpovědnost za výpis argumenty, které mají jejich adresu přijata. Pouze pro hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou musí celočíselný registr i registr s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou hodnotou obsahovat hodnotu v případě, že volaný očekává hodnotu v celočíselných registrech.

## <a name="unprototyped-functions"></a>Neprototypové funkce

Pro funkce, které nejsou plně prototypovány, volající předá celočíselné hodnoty jako celá čísla a hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou jako dvojitou přesnost. Pouze pro hodnoty s plovoucí desetinnou desetinnou hodnotou obsahuje celočíselný registr a registr s plovoucí desetinnou desetinnou desetinnou hodnotou hodnotu pro případ, že volaný očekává hodnotu v celočíselných registrech.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Vrácené hodnoty

Skalární vrácená hodnota, která se vejde do 64 bitů, je vrácena prostřednictvím RAX; to zahrnuje __m64 typy. Neskalární typy včetně plovoucích, dvojnic a vektorových typů, jako jsou [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) jsou vráceny v XMM0. Stav nepoužívaných bitů v hodnotě vrácené v RAX nebo XMM0 není definován.

Uživatelem definované typy lze vrátit podle hodnoty z globálních funkcí a statických členských funkcí. Chcete-li vrátit uživatelem definovaný typ podle hodnoty v RAX, musí mít délku 1, 2, 4, 8, 16, 32 nebo 64 bitů. Musí mít také žádný uživatelem definovaný konstruktor, destruktor nebo operátor přiřazení kopírování; žádné soukromé nebo chráněné nestatické datové členy; žádné nestatické datové členy referenčního typu; žádné základní třídy; žádné virtuální funkce; a žádné datové členy, které také nesplňují tyto požadavky. (Toto je v podstatě definice typu Pod C++03. Vzhledem k tomu, že definice se změnila ve standardu `std::is_pod` C++ 11, nedoporučujeme používat pro tento test.) V opačném případě volající přebírá odpovědnost za přidělení paměti a předání ukazatele pro vrácenou hodnotu jako první argument. Následné argumenty jsou pak posunuty o jeden argument doprava. Stejný ukazatel musí být vrácenvolní v RAX.

Tyto příklady ukazují, jak jsou předávány parametry a vrácené hodnoty pro funkce se zadanými deklaracemi:

### <a name="example-of-return-value-1---64-bit-result"></a>Příklad vrácené hodnoty 1 - 64bitový výsledek

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Příklad vrácené hodnoty 2 - 128bitový výsledek

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Příklad vrácené hodnoty 3 - výsledek typu uživatele ukazatelem

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Příklad vrácené hodnoty 4 - výsledek typu uživatele podle hodnoty

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Volající/Volaný uložené registry

Registry RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 a horní části YMM0-15 a ZMM0-15 jsou považovány za volatilní a musí být považovány za zničené při volání funkcí (pokud není jinak bezpečnost-provitatelné analýzou, jako je optimalizace celého programu). Na AVX512VL registry ZMM, YMM a XMM 16-31 jsou volatilní.

Registry RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 a XMM6-15 jsou považovány za stálé a musí být uloženy a obnoveny funkcí, která je používá.

## <a name="function-pointers"></a>Ukazatele funkcí

Ukazatele funkce jsou jednoduše ukazatele na popisek příslušné funkce. Neexistují žádné požadavky na obsah (TOC) pro ukazatele funkce.

## <a name="floating-point-support-for-older-code"></a>Podpora s plovoucí desetinnou čárkou pro starší kód

MMX a plovoucí desetinná žlábka zásobníku registry (MM0-MM7/ST0-ST7) jsou zachovány napříč přepnutí kontextu. Neexistuje žádná konvence explicitní volání pro tyto registry. Použití těchto registrů je přísně zakázáno v kódu režimu jádra.

## <a name="fpcsr"></a>FpCsr

Stav registru také obsahuje řídicí slovo x87 FPU. Konvence volání diktuje tento registr, který má být stálý.

Registr řídicích slov x87 FPU je na začátku spuštění programu nastaven na následující standardní hodnoty:

| Registrovat\[bity] | Nastavení |
|-|-|
| FPCSR\[0:6] | Výjimka maskuje všechny jedničky (všechny maškované výjimky) |
| FPCSR\[7] | Rezervováno - 0 |
| FPCSR\[8:9] | Přesné řízení - 10B (dvojitá přesnost) |
| FPCSR\[10:11] | Řízení zaokrouhlení - 0 (zaoblené do nejbližší) |
| FPCSR\[12] | Infinity control - 0 (nepoužívá se) |

Volaný, který upravuje libovolné pole v rámci FPCSR musí obnovit před návratem k jeho volajícímu. Kromě toho volající, který změnil některé z těchto polí musí obnovit jejich standardní hodnoty před vyvoláním volaného, pokud po dohodě volaný očekává změněné hodnoty.

Existují dvě výjimky z pravidel týkajících se nevolatility kontrolních příznaků:

1. Ve funkcích, kde je zdokumentovaným účelem dané funkce upravit stálé příznaky FpCsr.

1. Pokud je prokazatelně správné, že porušení těchto pravidel má za následek program, který se chová stejně jako program, kde tato pravidla nejsou porušena, například prostřednictvím analýzy celého programu.

## <a name="mxcsr"></a>MxCsr

Stav registru zahrnuje také MxCsr. Konvence volání rozdělí tento registr na těkavou část a stálou část. Těkavá část se skládá ze šesti\[stavových příznaků v MXCSR 0:5], zatímco zbytek registru, MXCSR\[6:15], je považován za stálé.

Nestálá část je na začátku spuštění programu nastavena na následující standardní hodnoty:

| Registrovat\[bity] | Nastavení |
|-|-|
| MXCSR\[6] | Denormaly jsou nuly - 0 |
| MXCSR\[7:12] | Výjimka maskuje všechny jedničky (všechny maškované výjimky) |
| MXCSR\[13:14] | Řízení zaokrouhlení - 0 (zaoblené do nejbližší) |
| MXCSR\[15] | Zarovnaná do nuly pro maskovaný podtečení - 0 (vypnuto) |

Volaný, který upravuje libovolné stálé pole v rámci MXCSR musí obnovit před návratem k jeho volajícímu. Kromě toho volající, který změnil některé z těchto polí musí obnovit jejich standardní hodnoty před vyvoláním volaného, pokud po dohodě volaný očekává změněné hodnoty.

Existují dvě výjimky z pravidel týkajících se nevolatility kontrolních příznaků:

- Ve funkcích, kde je zdokumentovaným účelem dané funkce upravit stálé příznaky MxCsr.

- Pokud je prokazatelně správné, že porušení těchto pravidel má za následek program, který se chová stejně jako program, kde tato pravidla nejsou porušena, například prostřednictvím analýzy celého programu.

Nelze provést žádné předpoklady o stavu těkavé části MXCSR přes hranice funkce, pokud není výslovně popsáno v dokumentaci funkce.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Pokud zahrnete setjmpex.h nebo setjmp.h, všechna volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) za následek `__finally` unwind, který vyvolá destruktory a volání.  To se liší od x86, kde včetně `__finally` setjmp.h výsledky klauzule a destruktory nejsou vyvolány.

Volání zachová `setjmp` aktuální ukazatel zásobníku, nestálé registry a Registry MxCsr.  Volání `longjmp` pro návrat na `setjmp` nejnovější web volání a obnoví ukazatel zásobníku, nestálé registry a registry MxCsr zpět do `setjmp` stavu, který je zachován nejnovějším voláním.

## <a name="see-also"></a>Viz také

[softwarové konvence x64](../build/x64-software-conventions.md)
