---
title: x64 – konvence volání
description: Podrobnosti o výchozí konvenci volání metody ABI x64
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856882"
---
# <a name="x64-calling-convention"></a>x64 – konvence volání

Tato část popisuje standardní procesy a konvence, které jedna funkce (volající) používá k volání jiné funkce (volaný) v kódu x64.

## <a name="calling-convention-defaults"></a>Výchozí nastavení konvence volání

Binární rozhraní aplikace x64 (ABI) používá ve výchozím nastavení konvenci volání rychlého volání. Místo se přiděluje v zásobníku volání jako stínové úložiště pro volané, aby se tyto registry uložily. Mezi argumenty volání funkce a Registry použitými pro tyto argumenty je pouze striktní korespondence 1:1. Všechny argumenty, které se nevejdou do 8 bajtů nebo nejsou 1, 2, 4 nebo 8 bajtů, musí být předány odkazem. Jeden argument se nikdy nerozprostře mezi několik registrů. Zásobník registru x87 není používán a může být použit volaným, ale musí být považován za volatili napříč voláními funkce. Všechny operace s plovoucí desetinnou čárkou se provádějí pomocí 16 XMM Registry. Celočíselné argumenty jsou předány v registrech RCX, RDX, R8 a R9. Argumenty s plovoucí desetinnou čárkou jsou předány v XMM0L, XMM1L, XMM2L a XMM3L. 16bitové argumenty jsou předány odkazem. Předávání parametrů je podrobně popsáno v tématu [předávání parametrů](#parameter-passing). Kromě těchto registrů jsou RAX, R10, R11, XMM4 a XMM5 považovány za nestálé. Všechny ostatní Registry jsou nestálé. Použití registru je podrobně popsáno v části [použití registru](../build/x64-software-conventions.md#register-usage) a v [uložených registrech volající/volaný](#callercallee-saved-registers).

Pro prototypované funkce jsou před předáním převedeny všechny argumenty na očekávané typy volaný. Volající zodpovídá za přidělování prostoru pro parametry volaného a musí vždy přidělit dostatek místa pro uložení čtyř parametrů registru, a to i v případě, že volaný nebere mnoho parametrů. Tato konvence zjednodušuje podporu neprototypových funkcí jazyka C a vararg C/C++ Functions. V případě funkcí vararg nebo Unprototyped musí být všechny hodnoty s plovoucí desetinnou čárkou duplikovány v odpovídajícím registru pro obecné účely. Všechny parametry za první čtyři musí být uloženy v zásobníku po stínovém úložišti před voláním. Podrobnosti o funkci vararg najdete v [vararg](#varargs). Informace o neprototypované funkci jsou podrobně popsané v [neprototypované](#unprototyped-functions)funkci.

## <a name="alignment"></a>Zarovnání

Většina struktur je zarovnána na své přirozené zarovnání. Primárními výjimkami jsou ukazatel zásobníku a `malloc` nebo `alloca` paměti, která je zarovnána na 16 bajtů, aby bylo možné povýšit výkon. Zarovnání nad 16 bajtů se musí provést ručně, ale vzhledem k tomu, že 16 bajtů je společná velikost zarovnání pro XMM operace, tato hodnota by měla fungovat pro většinu kódu. Další informace o rozložení a zarovnání struktury najdete v tématu [typy a úložiště](../build/x64-software-conventions.md#types-and-storage). Informace o rozložení zásobníku najdete v tématu [použití zásobníku x64](../build/stack-usage.md).

## <a name="unwindability"></a>Zpětná operace

Funkce list jsou funkce, které nemění žádné nestálé Registry. Funkce, která není typu list, může měnit nestálý RSP, například voláním funkce nebo přidělením dalšího prostoru zásobníku pro místní proměnné. Aby bylo možné obnovit nestálé Registry při zpracování výjimky, nelistové funkce musí být opatřeny poznámkami se statickými daty, které popisují, jak tuto funkci v libovolné instrukci správně odvinout. Tato data jsou ukládána jako *PDATA*nebo data procedur, která zase odkazují na *XData*, data zpracovávající výjimky. XData obsahuje informace o unwindu a může odkazovat na další PDATA nebo funkci obslužné rutiny výjimky. Protokoly a epilogy jsou vysoce omezené, aby je bylo možné správně popsat v XData. Ukazatel zásobníku musí být zarovnán na 16 bajtů v jakékoli oblasti kódu, která není součástí epilogu nebo prologu, s výjimkou v rámci funkcí listu. Funkce list lze oddělit pouhým simulací návratu, takže pdata a XData nejsou požadovány. Podrobnosti o správné struktuře protokolů a epilogech funkce naleznete v tématu [prolog a epilog x64](../build/prolog-and-epilog.md). Další informace o zpracování výjimek a o zpracování výjimek a o odvíjení pdata a XData naleznete v tématu [zpracování výjimek x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Předávání parametrů

První čtyři celočíselné argumenty jsou předány v registrech. Celočíselné hodnoty jsou předány v pořadí zleva doprava v RCX, RDX, R8 a R9, v uvedeném pořadí. Do zásobníku jsou předány argumenty 5 a vyšší. Všechny argumenty jsou v registrech zarovnané vpravo, takže volaný může ignorovat horní bity registru a přistupovat jenom k části registru, která je nezbytná.

Všechny argumenty s plovoucí desetinnou čárkou a dvojitou přesností v prvních čtyřech parametrech jsou předány v XMM0-XMM3 v závislosti na pozici. Celočíselné registry RCX, RDX, R8 a R9, které by se obvykle používaly pro tyto pozice, se ignorují, s výjimkou argumentů VarArgs Case. Podrobnosti najdete v tématu [VarArgs](#varargs). Podobně jsou registry XMM0-XMM3 ignorovány, pokud je odpovídajícím argumentem typ Integer nebo ukazatel.

[__m128](../cpp/m128.md) typy, pole a řetězce nejsou nikdy předány okamžitou hodnotou. Místo toho je ukazatel předán do paměti přidělené volajícím. Struktury a sjednocení s velikostí 8, 16, 32 nebo 64 bitů a typy __m64 jsou předány, jako kdyby byly celá čísla stejné velikosti. Struktury nebo sjednocení jiných velikostí jsou předány jako ukazatel na paměť přidělenou volajícím. Pro tyto agregované typy předané jako ukazatel, včetně \__m128, musí být dočasná paměť přidělená volajícímu zarovnaná na 16 bajtů.

Vnitřní funkce, které nepřiřazují prostor zásobníku a nevolají jiné funkce, někdy používají jiné nestálé Registry k předání dalších argumentů registru. Tato optimalizace je umožněna těsnou vazbou mezi kompilátorem a implementací vnitřní funkce.

Volaný je zodpovědný za výpis parametrů registru do jejich stínového prostoru v případě potřeby.

Následující tabulka shrnuje, jak se předávají parametry:

|Typ parametru|Jak úspěšné|
|--------------------|----------------|
|Plovoucí desetinná čárka|Prvních 4 parametry – XMM0 až XMM3. Ostatní prošly v zásobníku.|
|Integer|Prvních 4 parametry – RCX, RDX, R8, R9. Ostatní prošly v zásobníku.|
|Agreguje (8, 16, 32 nebo 64 bitů) a __m64|Prvních 4 parametry – RCX, RDX, R8, R9. Ostatní prošly v zásobníku.|
|Agregace (jiné)|Podle ukazatele. Prvních 4 parametry byly předány jako ukazatelé v RCX, RDX, R8 a R9.|
|__m128|Podle ukazatele. Prvních 4 parametry byly předány jako ukazatelé v RCX, RDX, R8 a R9.|

### <a name="example-of-argument-passing-1---all-integers"></a>Příklad předání argumentu 1 – všechna celá čísla

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Příklad předání argumentu 2 – všechny Floaty

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Příklad předávání argumentu 3 – smíšené čísla a Floaty

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Příklad předávání argumentu 4 __m64, \__m128 a agregace

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Vararg

Pokud jsou parametry předány prostřednictvím vararg (například argumenty se třemi tečkami), platí, že se použije normální konvence předávání parametru registru, včetně obtékající pátého a následného argumentu do zásobníku. Je to zodpovědnost za volaný výpis argumentů, na které se zabere adresa. Pouze pro hodnoty s plovoucí desetinnou čárkou musí celočíselný registr i registr s plovoucí desetinnou čárkou obsahovat hodnotu, pro případ, že volaný očekává hodnotu v celočíselném registru.

## <a name="unprototyped-functions"></a>Neprototypované funkce

U funkcí, které nejsou plně prototypované, volající předává celočíselné hodnoty jako celé číslo a hodnoty s plovoucí desetinnou čárkou jako dvojitou přesnost. Pouze pro hodnoty s plovoucí desetinnou čárkou obsahuje celočíselný registr i registr s plovoucí desetinnou čárkou hodnotu float pro případ, že volaný očekává hodnotu v celočíselném registru.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Vrácené hodnoty

Skalární návratová hodnota, která se může vejít do 64 bitů, se vrátí prostřednictvím RAX; To zahrnuje __m64 typy. Neskalární typy včetně typů float, Double a Vector, jako je například [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) [__m128d](../cpp/m128d.md) jsou vráceny v XMM0. Stav nepoužitých bitů v hodnotě vrácené v RAX nebo XMM0 není definován.

Uživatelsky definované typy mohou být vráceny hodnotou z globálních funkcí a statických členských funkcí. Chcete-li vrátit uživatelem definovaný typ podle hodnoty v RAX, musí mít délku 1, 2, 4, 8, 16, 32 nebo 64 bitů. Musí mít také žádné uživatelsky definované konstruktory, destruktory ani operátory přiřazení Copy; žádné soukromé nebo chráněné nestatické datové členy; žádné nestatické datové členy typu odkazu; žádné základní třídy; žádné virtuální funkce; a žádné datové členy, které tyto požadavky nesplňují ani. (To je v podstatě definice typu v jazyce C++ 03 POD. Vzhledem k tomu, že se definice v standardu C++ 11 změnila, nedoporučujeme pro tento test použít `std::is_pod`.) V opačném případě volající předpokládá zodpovědnost za přidělování paměti a předání ukazatele pro návratovou hodnotu jako první argument. Další argumenty jsou pak posunuty o jeden argument vpravo. Stejný ukazatel musí být vrácen volaným v RAX.

Tyto příklady ukazují, jak se předávají parametry a návratové hodnoty pro funkce se zadanými deklaracemi:

### <a name="example-of-return-value-1---64-bit-result"></a>Příklad návratové hodnoty 1-64 – bitový výsledek

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Příklad návratové hodnoty 2-128 – bitový výsledek

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Příklad návratové hodnoty 3 – výsledek typu uživatele podle ukazatele

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Příklad návratové hodnoty 4 – výsledek typu uživatele podle hodnoty

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry

Registry RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 a horní části YMM0-15 a ZMM0-15 se považují za nestálé a musí být považovány za zničené při volání funkce (Pokud není jinak bezpečnost-provable analýzou, jako je celá optimalizace programu). V AVX512VL jsou registry ZMM, YMM a XMM v registru 16-31 nestálé.

Registry RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 a XMM6-15 jsou považovány za nestálé a musí být uloženy a obnoveny funkcí, která je používá.

## <a name="function-pointers"></a>Ukazatele na funkce
 
Ukazatele na funkci jsou pouhými ukazateli na popisek příslušné funkce. Neexistují žádné požadavky obsahu (TOC) pro ukazatele na funkce.

## <a name="floating-point-support-for-older-code"></a>Podpora plovoucí desetinné čárky pro starší kód

Protokoly MMX a Registry zásobníku s plovoucí desetinnou čárkou (MM0-MM7/ST0-ST7) jsou zachovány napříč přepínači kontextu. Pro tyto registry neexistuje explicitní konvence volání. Použití těchto registrů je výhradně zakázané v kódu režimu jádra.

## <a name="fpcsr"></a>FpCsr

Stav registru obsahuje také řídicí slovo x87 FPU. Konvence volání Určuje, že tento registr je nestálý.

Na začátku provádění programu je na základě registru ovládacího prvku x87 FPU nastavené na následující standardní hodnoty:

| Registrace\[bitů] | Nastavení |
|-|-|
| FPCSR\[0:6] | Masky výjimek všechny 1 (všechny výjimky s maskou) |
| FPCSR\[7] | Rezervované – 0 |
| FPCSR\[8:9] | Kontrola přesnosti – 10B (dvojitá přesnost) |
| FPCSR\[10:11] | Zaoblení ovládacího prvku-0 (zaokrouhleno na nejbližší) |
| FPCSR\[12] | Nekonečno – ovládací prvek – 0 (nepoužívá se) |

Volaný, který upraví jakékoli pole v rámci FPCSR, musí je obnovit před návratem k jeho volajícímu. Kromě toho je nutné, aby volající, který změnil některá z těchto polí, obnovil jejich standardní hodnoty před vyvoláním volaného, ledaže by smlouva volaný očekává změněné hodnoty.

Existují dvě výjimky z pravidel o nestálosti kontrolních příznaků:

1. Ve funkcích, kde dokumentovaný účel dané funkce slouží k úpravě netěkavých příznaků FpCsr.

1. V případě, že je správně napravuje, že porušení těchto pravidel vede k programu, který se chová stejně jako program, ve kterém se tato pravidla neporušila, například prostřednictvím analýzy celého programu.

## <a name="mxcsr"></a>MxCsr

Stav registru zahrnuje také MxCsr. Konvence volání rozděluje tento registr na nestálou část a nestálou část. Těkavá část se skládá z šesti příznaků stavu, v MXCSR\[0:5], zatímco zbytek registru MXCSR\[6:15] se považuje za nestálý.

Nestálá část je nastavená na následující standardní hodnoty na začátku provádění programu:

| Registrace\[bitů] | Nastavení |
|-|-|
| MXCSR\[6] | Denormalizované jsou nuly – 0. |
| MXCSR\[7:12] | Masky výjimek všechny 1 (všechny výjimky s maskou) |
| MXCSR\[13:14] | Zaoblení ovládacího prvku-0 (zaokrouhleno na nejbližší) |
| MXCSR\[15] | Vyprázdnit na nulu pro maskované podtečení – 0 (vypnuto) |

Volaný, který upravuje jakékoliv nestálé pole v rámci MXCSR, musí je obnovit před návratem k jeho volajícímu. Kromě toho je nutné, aby volající, který změnil některá z těchto polí, obnovil jejich standardní hodnoty před vyvoláním volaného, ledaže by smlouva volaný očekává změněné hodnoty.

Existují dvě výjimky z pravidel o nestálosti kontrolních příznaků:

- Ve funkcích, kde dokumentovaný účel dané funkce slouží k úpravě netěkavých příznaků MxCsr.

- V případě, že je správně napravuje, že porušení těchto pravidel vede k programu, který se chová stejně jako program, ve kterém se tato pravidla neporušila, například prostřednictvím analýzy celého programu.

Nelze provést žádné předpoklady týkající se stavu těkavé části MXCSR napříč hranicí funkce, pokud není konkrétně popsána v dokumentaci funkce.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Pokud zahrnete SETJMPEX. h nebo setjmp. h, všechna volání do [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) navedou v unwind, který vyvolá destruktory a volání `__finally`.  To se liší od x86, kde včetně setjmp. h vede k vyvolání klauzulí `__finally` a destruktorů.

Volání `setjmp` zachová aktuální ukazatel zásobníku, jiné než nestálé registry a Registry MxCsr.  Volání `longjmp` se vrátí k nejnovějšímu webu volání `setjmp` a obnoví ukazatel zásobníku, nestálé registry a Registry MxCsr zpět do stavu, který zachovává nejnovější `setjmp` volání.

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)
