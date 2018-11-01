---
title: __vectorcall
ms.date: 10/10/2018
f1_keywords:
- __vectorcall_cpp
- __vectorcall
- _vectorcall
helpviewer_keywords:
- __vectorcall keyword
- __vectorcall
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
ms.openlocfilehash: ab542a7fbae286a7f39b66bb4857cd8e8ff6ab59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507221"
---
# <a name="vectorcall"></a>__vectorcall

**Specifické pro Microsoft**

**__Vectorcall** konvence volání Určuje, že argumenty funkcí mají být předány v registrech, pokud je to možné. **__vectorcall** používá více registrů pro argumenty než [__fastcall](../cpp/fastcall.md) nebo výchozí hodnotu [x64 konvence volání](../build/overview-of-x64-calling-conventions.md) použít. **__Vectorcall** konvence volání je podporována pouze v nativním kódu x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Použití **__vectorcall** k urychlení funkcí, které předávají několik s plovoucí desetinnou čárkou nebo SIMD vektorovým argumentům a provádět operace, které využívají argumenty načtené do registrů. Následující seznam obsahuje funkce, které jsou společné pro implementace x86 a x64 **__vectorcall**. Rozdíly jsou vysvětleny dále v tomto článku.

|Prvek|Implementace|
|-------------|--------------------|
|Konvence pro vzhled názvu C|Názvy funkcí jsou doplněny dvěma ""symboly zavináč (\@\@) následovaný počtem bajtů (v desítkové soustavě) v seznamu parametrů.|
|Konvence pro posunutí|Provádí se žádný překlad případu.|

Použití [/Gv](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru způsobí, že každá funkce v modulu je kompilována jako **__vectorcall** Pokud funkce je členská funkce, je deklarována s konfliktním atributem konvence volání, používá `vararg` Proměnný seznam argumentů, nebo má název `main`.

Můžete předat tři typy argumentů podle registru ve **__vectorcall** funkce: *celočíselný typ* hodnoty, *vektorového typu* hodnoty, a *homogenního vektoru agregační* hodnoty (HVA).

Typ celého čísla splňuje dva požadavky: vejde se do nativní velikosti registru procesoru – například 4 bajty v x x86 počítače nebo 8 bajtů na x x64 počítači – a je lze převést na celé číslo délky registru a zpět znovu beze změny jeho bitové reprezentace. Například libovolný typ, který může být povýšen na **int** na x86 (**long long** na x64) – například **char** nebo **krátký**– nebo, který lze převést na **int** (**long long** na x64) a zpět do původního stavu bez změn je typu integer. Celočíselné typy zahrnují ukazatel, odkaz a **struktura** nebo **sjednocení** typy 4 bajtů (8 bajtů na x64) nebo méně. Na x64 platformy **struktura** a **sjednocení** typy jsou předávány odkazem na paměť přidělenou volajícím; na x86 platformy, jsou předány podle hodnoty v zásobníku.

Typ vektoru je typ s plovoucí desetinnou čárkou, například **float** nebo **double**– nebo typ vektoru SIMD – například **__m128** nebo **__m256**.

Typ HVA je složený typ z až čtyř datových členů, které mají identický vektorový. Typ HVA má stejný požadavek na zarovnání jako typ vektoru jeho členů. Toto je příklad hva **struktura** definice, která obsahuje tři totožné typy vektoru a má 32bajtové zarovnání:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Deklarace vašich funkcí explicitně s **__vectorcall** – klíčové slovo v záhlaví souborů, aby bylo možné samostatně zkompilovat kód k propojení bez chyb. Funkce musí být prototypem pomocí **__vectorcall**a nelze použít `vararg` seznam argumentů s proměnnou délkou.

Členské funkce mohou být deklarovány s použitím **__vectorcall** specifikátor. Skrytý **to** ukazatel je registrem odeslán jako první argument typu celé číslo.

Na počítačích ARM **__vectorcall** je přijato a ignorováno kompilátory.

Pro nestatické třídy členské funkce je-li funkce definovaná mimo řádek, modifikátor konvence volání nemá být stanoven na definici mimo řádek. To znamená, že pro nestatické členy třídy, se předpokládá konvence volání zadaná během deklarace Přejme během definice. Při této definici třídy:

```cpp
struct MyClass {
   void __vectorcall mymethod();
};
```

toto:

```cpp
void MyClass::mymethod() { return; }
```

je ekvivalentem tohoto:

```cpp
void __vectorcall MyClass::mymethod() { return; }
```

**__Vectorcall** modifikátor konvence volání při musí být zadán ukazatel **__vectorcall** funkce se vytvoří. Následující příklad vytvoří **– typedef** ukazatele na **__vectorcall** funkce, která přebírá čtyři **double** argumenty a vrátí **__m256**hodnotu:

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

Z důvodu kompatibility s předchozími verzemi **_vectorcall** je synonymum pro **__vectorcall** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md)určena.

## <a name="vectorcall-convention-on-x64"></a>konvence __vectorcall na x64

**__Vectorcall** konvence volání na x64 rozšiřuje standardní x64 konvence volání, která tak využívá dalších registrů trvat. Argumenty typu integer a argumenty vektorového typu jsou mapovány do registrů na základě pozice v seznamu argumentů. Nepoužité vektorové registry jsou přiděleny argumentům HVA.

Pokud některý z prvních čtyř argumentů v pořadí zleva doprava jsou argumenty typu celého čísla, jsou předány do registru, který odpovídá této pozici – RCX, RDX, R8 a R9. Skrytý **to** ukazatel je považován za první argument typu celé číslo. Pokud argument HVA v jednom z prvních čtyř argumentů nelze předávat do dostupných registrů, odkaz na paměť přidělenou volajícímu je místo něho předán do odpovídajícího registru typu celého čísla. Argumenty typu celého čísla po pozici čtvrtého parametru jsou předány do zásobníku.

Pokud některý z prvních šesti argumentů v pořadí zleva doprava jsou argumenty vektorového typu, jsou předány podle hodnoty v vektorového registru SSE 0 až 5 podle pozice argumentu. S plovoucí desetinnou čárkou a **__m128** typy jsou předány v registrech XMM a **__m256** typy jsou předány v registrech YMM zaregistruje. Tím se liší od standardní x64 konvence volání, protože vektorové typy jsou předávány hodnotou místo pomocí odkazu a jsou použity další registry. Vystínovaný prostor zásobníku přidělený pro argumenty vektorového typu je nastaven na 8 bajtech a [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) neplatí. Argumenty vektorového typu sedmé a následujících pozicích parametru jsou předány do zásobníku s odkazem na paměť přidělenou volajícím.

Po přidělení registrů vektorovým argumentům datové členy argumentů HVA přiděleny vzestupně nepoužívaným vektorovým registrům XMM0 až XMM5 (nebo YMM0 k YMM5, pro **__m256** typy), dokud nejsou k dispozici dostatek registrů k dispozici pro celé HVA. Pokud jsou k dispozici dostatek registrů, HVA argument je předán odkazem na paměť přidělenou volajícím. Stínovaný prostor zásobníku pro HVA argument je nastaven na 8 bajtech s nedefinovaným obsahem. Argumenty HVA jsou přiřazeny k registrům v pořadí zleva doprava v seznamu parametrů a mohou být v jakékoliv pozici. Argumenty HVA v jednom z prvních čtyř argumentů, že umístění, které nejsou přiřazeny k vektorovým registrům jsou předány podle odkazu v registru celých čísel, která odpovídá této pozici. Argumenty HVA předané podle odkazu po pozici čtvrtého parametru jsou poslány do zásobníku.

Výsledky **__vectorcall** funkce jsou vrácené hodnotou v registrech, pokud je to možné. Výsledky celočíselného typu, včetně struktur nebo sjednocení 8 bajtů nebo méně, jsou vrácené hodnotou v RAX. Výsledky vektorového typu jsou vrácené hodnotou v XMM0 nebo YMM0, v závislosti na velikosti. Výsledky HVA mají každý datový element vrácen podle hodnoty v registrech XMM0: XMM3 nebo ymm0: ymm3, v závislosti na velikosti elementu. Typy výsledků, které se nehodí do příslušného registru se vrátil s odkazem na paměť přidělenou volajícím.

Zásobník je zachován volající v x64 provádění **__vectorcall**. Kód prologu a epilogu volajícího přiděluje a maže zásobník volané funkce. Argumenty jsou posunuty v zásobníku zprava doleva a je přiděleno stínové místo zásobníku argumenty předány v registrech.

Příklady:

```cpp
// crt_vc64.c
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c
// This example creates an annotated assembly listing in
// crt_vc64.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,
// f in XMM5, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.
// Passes b by element in [XMM0:XMM1];
// b's stack shadow area is 8-bytes of undefined value.
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: Discontiguous HVA
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because
// vector arguments b and d were allocated first.
// Shadow area for c is an 8-byte undefined value.
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in RCX, c in R8, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with
// stack shadow areas of an 8-byte undefined value.
// Return value in RAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

## <a name="vectorcall-convention-on-x86"></a>konvence __vectorcall na x86

**__Vectorcall** následující konvence volání **__fastcall** konvence pro argumenty typu celého čísla 32 bitů a využívá registrů vektoru SSE pro typ vektoru a argumenty HVA.

První argumenty celočíselného typu v seznamu parametrů zleva doprava jsou umístěny jeden do ECX a EDX, v uvedeném pořadí. Skrytý **to** ukazatel je považován za první argument typu integer a je předáván v ECX. Prvních šest argumentů vektorového typu jsou předávány hodnotou prostřednictvím vektorového registru SSE 0 až 5 v registrech XMM nebo YMM v závislosti na velikost argumentu.

Prvních šest argumentů vektorových typů v pořadí zleva doprava jsou předávány hodnotou vektorového registru SSE 0 až 5. S plovoucí desetinnou čárkou a **__m128** typy jsou předány v registrech XMM a **__m256** typy jsou předány v registrech YMM zaregistruje. Žádné stínové místo zásobníku je přidělen pro argumenty vektorového typu registrem odeslán. Argumenty sedmý a následující vektorového typu jsou předány do zásobníku s odkazem na paměť přidělenou volajícím. Omezení chyby kompilátoru [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) se nevztahují na tyto argumenty.

Po přidělení registrů vektorovým argumentům datové členy argumentů HVA přiděleny vzestupně nepoužívaným vektorovým registrům XMM0 až XMM5 (nebo YMM0 k YMM5, pro **__m256** typy), dokud nejsou k dispozici dostatek registrů k dispozici pro celé HVA. Pokud jsou k dispozici dostatek registrů, HVA argument je předán do zásobníku s odkazem na paměť přidělenou volajícím. Místo ve stínovém zásobníku pro HVA argument je přidělen. Argumenty HVA jsou přiřazeny k registrům v pořadí zleva doprava v seznamu parametrů a mohou být v jakékoliv pozici.

Výsledky **__vectorcall** funkce jsou vrácené hodnotou v registrech, pokud je to možné. Hodnota v eax VRÁTÍ jsou vráceny výsledky celočíselného typu, včetně struktur nebo sjednocení 4 bajtů nebo méně. Hodnota EDX: eax vrátí jsou vrácené struktury celočíselného typu nebo sjednocení 8 bajtů nebo i rychleji. Výsledky vektorového typu jsou vrácené hodnotou v XMM0 nebo YMM0, v závislosti na velikosti. Výsledky HVA mají každý datový element vrácen podle hodnoty v registrech XMM0: XMM3 nebo ymm0: ymm3, v závislosti na velikosti elementu. Ostatní typy výsledků jsou vráceny s odkazem na paměť přidělenou volajícím.

X86 provádění **__vectorcall** následuje konvenci argumentů předaných v zásobníku zprava doleva volajícím a volané funkce vymaže zásobníku těsně před vrácením. Pouze argumenty, které nejsou uloženy v registrech, jsou odeslány do zásobníku.

Příklady:

```cpp
// crt_vc86.c
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c
// This example creates an annotated assembly listing in
// crt_vc86.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,
// f in XMM3, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in ECX, c in EDX, d and e pushed on stack.
// Passes b by element in [XMM0:XMM1].
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: HVA assigned after vector types
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.
// Passes c by element in [YMM2:YMM5].
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in ECX, c in EDX, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].
// Return value in EAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

**Specifické pro end Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)