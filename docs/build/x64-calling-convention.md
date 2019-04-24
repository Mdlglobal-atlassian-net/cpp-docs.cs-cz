---
title: x64 konvence volání
description: Podrobnosti o výchozí x64 ABI konvenci volání.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 02bf4719766366049b600b148ad88fc238f4e54e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313612"
---
# <a name="x64-calling-convention"></a>x64 konvence volání

Tato část popisuje standardních procesů a vytváření názvů, které používá jeden – funkce (volajícího) pro volání do jiného – funkce (volaný) x64 kódu.

## <a name="calling-convention-defaults"></a>Výchozí konvence volání

X64 binární rozhraní aplikace (ABI) používá konvence volání rychlého volání čtyři registr ve výchozím nastavení. Jako úložiště stínové pro volané uložte tyto registry není přiděleno místo v zásobníku volání. Existuje striktní shoda mezi argumenty pro volání funkce a registry použité pro tyto argumenty. Jakýkoliv argument, který se nevejde do 8 bajtů nebo není 1, 2, 4 nebo 8 bajtů, musejí být předány podle odkazu. Jeden argument je nikdy rozdělena mezi více registrů. Registrovat x87 zásobníku se nepoužívá a mohou být využívána volaný, ale musíte vzít v úvahu volatile ve volání funkce. S plovoucí desetinnou čárkou všechny operace se provádějí pomocí 16 registry XMM. Celočíselné argumenty jsou předány v registrech RCX, RDX, R8 a R9. Plovoucí desetinná čárka, že jsou argumenty předávány v XMM0L, XMM1L, XMM2L a XMM3L. 16 bajtů argumenty jsou předány podle odkazu. Předávání parametrů je podrobně popsány v [předávání parametru](#parameter-passing). Kromě těchto registrů RAX, R10, R11, XMM4 a XMM5 považují volatile. Všechny ostatní registry jsou není typu volatile. Využití registrů je podrobně popsáno v [zaregistrovat využití](../build/x64-software-conventions.md#register-usage) a [volající/volaný – uloží zaregistruje](#callercallee-saved-registers).

Pro prototypové funkce jsou všechny argumenty převést na typy volaný očekává před předáním. Volající zodpovídá za přidělování prostoru pro parametry volaného a musí vždy přidělit dostatek místa pro uložení čtyři parametry registru, i v případě, že volaný nepřijímá daný počet parametrů. Tato konvence zjednodušuje podporu Neprototypové funkce jazyka C a C/C++ funkce vararg. Pro funkce vararg nebo unprototyped plovoucí čárky hodnoty musí být duplicitní do odpovídajícího registru pro obecné účely. Žádné parametry kromě první čtyři musí být uložen v zásobníku, po uložení stínové před voláním. Najdete podrobnosti funkce vararg v [Varargs](#varargs). Neprototypové funkce informace je podrobně popsaná v [Neprototypové funkce](#unprototyped-functions).

## <a name="alignment"></a>Zarovnání

Většina struktury jsou zarovnány na jejich přirozené zarovnání. Primární výjimky jsou ukazatel zásobníku a `malloc` nebo `alloca` paměti, což je zarovnán 16 bajtů za účelem zlepšení výkonu. Zarovnání výše 16 bajtů musí provádět ručně, ale protože 16 bajtů je běžné velikosti zarovnání XMM operací, tato hodnota by měla fungovat pro většinu kódu. Další informace o rozložení struktury a zarovnání naleznete v tématu [typy a úložiště](../build/x64-software-conventions.md#types-and-storage). Informace o rozložení zásobníku, naleznete v tématu [x64 zásobníku využití](../build/stack-usage.md).

## <a name="unwindability"></a>Funkcionalita unwind

Funkce listu jsou funkce, které neměnit žádné registry není typu volatile. Funkce mimo úroveň listu může změnit stálé RSP, například volání funkce nebo přiděluje další zásobníku pro místní proměnné. Aby bylo možné obnovit bez registry, když je výjimka ošetřena, mimo úroveň listu funkce musí být komentována atributem statická data, která popisuje, jak správně unwind funkci na libovolného instrukce. Tato data se ukládají jako *pdata*, nebo postup dat, které zase odkazuje na *xdata*, zpracování dat výjimek. Xdata odvíjení informacemi a může odkazovat na další pdata nebo funkce obslužné rutiny výjimky. Prology a epilogu funkce jsou vysoce omezenou tak, aby mohly být správně podle xdata. Ukazatel zásobníku musí být zarovnány na 16 bajtů v libovolné oblasti kódu, který není součástí epilogu nebo prologu, s výjimkou v rámci funkcí listu. Funkce listu můžete zachytila jednoduše tak, že budete jen simulovat vrácení, takže pdata a xdata nejsou povinné. Podrobnosti o struktuře správné funkce Prology a epilogu funkce naleznete v tématu [x64 sekvence prologu a epilogu](../build/prolog-and-epilog.md). Další informace o zpracování výjimek a zpracování výjimek a uvolnění pdata a xdata najdete v tématu [x64 zpracování výjimek](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Předávání parametrů

První čtyři celočíselné argumenty jsou předány v registrech. Celočíselné hodnoty jsou předány v pořadí zleva doprava v RCX, RDX, R8 a R9, v uvedeném pořadí. Argumenty 5 a vyšší jsou předány do zásobníku. Všechny argumenty jsou zarovnána vpravo v registrech, takže volaný může ignorovat horní bits do registru a přistupovat k pouze část do registru, které jsou nezbytné.

Argumentů s plovoucí desetinnou čárkou a dvojitou přesností v první čtyři parametry jsou předány v XMM0 - XMM3, v závislosti na umístění. Celočíselné registry RCX, RDX, R8 a R9, která se běžně používá pro tyto pozice jsou ignorovány, s výjimkou argumenty varargs. Podrobnosti najdete v tématu [Varargs](#varargs). Podobně XMM0 - XMM3 registry jsou ignorovány, pokud je odpovídající argument typu celé číslo nebo ukazatel.

[__m128](../cpp/m128.md) typy, pole a řetězce jsou nebyl nikdy předán okamžitou hodnotou. Místo toho je předán ukazatel na paměť přidělenou volajícím. Struktury a sjednocení velikosti 8, 16, 32 nebo 64 bitů a typů __m64, jsou předány jako by byly celých čísel stejné velikosti. Struktury nebo sjednocení ostatní formáty jsou předány jako ukazatele na paměť přidělenou volajícím. Pro tyto typy předány jako ukazatele včetně \__m128, volající – přidělené dočasné paměti musí být zarovnán na 16 bajtů.

Vnitřní funkce, které není přidělit místo v zásobníku a nemůžete volat jiné funkce, někdy použít závislé registry k předávání argumentů další registru. Tato optimalizace je možné díky těsné vazby mezi kompilátor a provádění vnitřní funkce.

Volaný zodpovídá za vypsání parametry registru do jejich stínové místo v případě potřeby.

Následující tabulka shrnuje, jak jsou předávány parametry:

|Typ parametru|Jak předávat|
|--------------------|----------------|
|Plovoucí desetinná čárka|První 4 parametry - XMM0 prostřednictvím XMM3. Ostatní předány v zásobníku.|
|Integer|První 4 parametry – RCX, RDX, R8 R9. Ostatní předány v zásobníku.|
|Agregace (8, 16, 32 nebo 64 bitů) a __m64|První 4 parametry – RCX, RDX, R8 R9. Ostatní předány v zásobníku.|
|Agregace (ostatní)|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|
|__m128|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Příklad 1 - všech celých čísel předávání argumentů

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Příklad 2 – všechny floaty předávání argumentů

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Příklad 3 - smíšené celá čísla a float předávání argumentů

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Příklad 4 předávání argumentů-__m64, \__m128 a agregace

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Vararg

Pokud parametry jsou předány prostřednictvím vararg (například tlačítko se třemi tečkami argumenty), pak předávání konvence parametrů normální register vztahuje, včetně přesahu páté a následné argumenty do zásobníku. Je zodpovědností volaného na argumenty s výpisem paměti, které adresu. Pouze hodnoty s plovoucí desetinnou čárkou registru celých čísel a registr s plovoucí desetinnou čárkou musí obsahovat hodnotu, v případě, že volaný očekává, že hodnota v registrech celé číslo.

## <a name="unprototyped-functions"></a>Neprototypové funkce

Pro funkce nelze používat plně prototypované volající předá celočíselné hodnoty jako celá čísla a hodnoty s plovoucí desetinnou čárkou jako dvojitou přesností. Pouze hodnoty s plovoucí desetinnou čárkou registru celých čísel a registr s plovoucí desetinnou čárkou obsahovat hodnoty typu float v případě, že volaný očekává, že hodnota v registrech celé číslo.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Vrácené hodnoty

Skalární návratovou hodnotu, která se vejde do 64 bitů, je vrácena prostřednictvím RAX; To zahrnuje typů __m64. Non Skalární typy, včetně float, Double a typy vektoru, jako [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) jsou vráceny v XMM0. Stav nevyužité bity v hodnotě vrácené v RAX nebo XMM0 není definován.

Uživatelem definované typy mohou být vráceny hodnotou z globální funkce a statické členské funkce. Chcete-li hodnota v RAX VRÁTÍ návratový typ definovaný uživatelem, musí mít o délce 1, 2, 4, 8, 16, 32 nebo 64 bitů. Musíte také mít žádný uživatelem definovaný konstruktor, destruktor ani operátor copy assignment; žádné soukromé nebo chráněné nestatické datové členy. žádné nestatické datové členy typu odkazu; žádné základní třídy; žádné virtuální funkce. a žádné datové členy, které nesplňují také tyto požadavky. (To je v podstatě definice C ++ 03 typem POD. Protože došlo ke změně definice v C ++ 11 standard, nedoporučujeme používat `std::is_pod` pro tento test.) V opačném případě volající předpokládá odpovědnost přidělení paměti a předání ukazatele pro vrácenou hodnotu jako první argument. Další argumenty jsou potom posunuty o jeden argument vpravo. Stejný ukazatel musí být vrácen volaným v RAX.

Tyto příklady ukazují, jak předané parametry a návratové hodnoty pro funkce s zadané deklarace:

### <a name="example-of-return-value-1---64-bit-result"></a>Příklad vrácené hodnoty 1 – 64-bit výsledek

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Příklad vrácené hodnoty 2 - 128-bit výsledek

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Příklad vrácené hodnoty 3 – výsledek uživatelského typu ukazatel

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Příklad vrácené hodnoty 4 – výsledek uživatelského typu podle hodnoty

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry

Poškození registrů RAX RCX, RDX, R8, R9, R10, R11 jsou považovány za volatile a musíte vzít v úvahu při volání funkce (není-li jinak bezpečnost dokázat analýzou například celková optimalizace programu).

Registry RBX RBP, RDI, RSI, RSP, r 12, R13, R14 a R15 jsou považovány za stálé a musí být uloženy a obnovit pomocí funkce, která je používá.

## <a name="function-pointers"></a>Ukazatele na funkce

Ukazatele na funkce jsou jednoduše ukazatele na popisek příslušné funkce. Neexistují žádná tabulka požadavků na obsah (TOC) pro ukazatele na funkce.

## <a name="floating-point-support-for-older-code"></a>Podpora plovoucí desetinné čárky pro starší kód

MMX a registry zásobníku s plovoucí desetinnou čárkou (MM0-MM7/ST0-ST7) jsou zachovány v kontextu. Neexistuje žádné explicitní konvenci volání pro tyto registry. Použití těchto registrů je přísně zakázáno v kódu v režimu jádra.

## <a name="fpcsr"></a>FpCsr

Stav registrace obsahuje také x87 FPU řídicího slova. Určuje konvenci volání tento registr stálé.

X87 FPU kontrolní slovo registru je nastavena na následující standardní hodnoty na začátku provádění programu:

| Zaregistrujte\[bits] | Nastavení |
|-|-|
| FPCSR\[0:6] | Výjimka zakrývá všechny 1 (maskované všechny výjimky) |
| FPCSR\[7] | Vyhrazené - 0 |
| FPCSR\[8:9] | Ovládací prvek přesnost – 10B (Dvojitá přesnost) |
| FPCSR\[10:11] | Ovládací prvek zaokrouhlení – 0 (zaokrouhlit na nejbližší) |
| FPCSR\[12] | Ovládací prvek nekonečno - 0 (nepoužívá) |

Volaný, který upravuje některé z polí v rámci FPCSR musí obnovit před vrácením volající funkci. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného Pokud smlouvou volaný očekává, že změněné hodnoty.

Existují dvě výjimky pravidla týkající se jiných volatility příznaky ovládacích prvků:

1. Ve funkcích, kde zdokumentovaných účel danou funkci stálé FpCsr příznaků.

1. Pokud je prokazatelně správné, že porušení pravidla výsledky v programu v jazyce, který se chová stejně jako program, ve kterém nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.

## <a name="mxcsr"></a>MxCsr

Stav registrace také zahrnuje MxCsr. Konvence volání tento registr rozděluje volatile část a stálé část. Volatile část se skládá z šesti stav příznaky, v registru MXCSR\[0:5], zatímco zbytek do registru MXCSR\[6:15], je považován za stálé.

Stálé část je nastaven na následující standardní hodnoty na začátku spuštění programu:

| Zaregistrujte\[bits] | Nastavení |
|-|-|
| MXCSR\[6] | Denormals jsou nulové hodnoty - 0 |
| MXCSR\[7:12] | Výjimka zakrývá všechny 1 (maskované všechny výjimky) |
| MXCSR\[13:14] | Ovládací prvek zaokrouhlení – 0 (zaokrouhlit na nejbližší) |
| MXCSR\[15] | Vyprázdnění na nulu maskované podtečení - 0 (vypnuto) |

Volaný, který změní libovolné stálé pole v rámci MXCSR musí obnovit před vrácením volající funkci. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného Pokud smlouvou volaný očekává, že změněné hodnoty.

Existují dvě výjimky pravidla týkající se jiných volatility příznaky ovládacích prvků:

- Ve funkcích, kde zdokumentovaných účel danou funkci stálé MxCsr příznaků.

- Pokud je prokazatelně správné, že porušení pravidla výsledky v programu v jazyce, který se chová stejně jako program, ve kterém nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.

Žádné předpoklady nelze realizovat týkající se stavu volatile část MXCSR přes hranice funkce, pokud není výslovně uvedeno v dokumentaci funkce.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Pokud zahrnete setjmpex.h nebo setjmp.h, veškerá volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) za následek unwind vyvolávající destruktory a `__finally` volání.  Tím se liší od x86, kde výsledkem včetně setjmp.h `__finally` klauzule a destruktory.

Volání `setjmp` zachová aktuální ukazatel zásobníku, bez registry a MxCsr registrů.  Volání `longjmp` vraťte se na nejnovější `setjmp` volání webu a obnoví ukazatel zásobníku, bez registry a MxCsr zaregistruje, zpět do stavu jako zachovaný nejnovější `setjmp` volání.

## <a name="see-also"></a>Viz také:

[x64 – softwarové konvence](../build/x64-software-conventions.md)
