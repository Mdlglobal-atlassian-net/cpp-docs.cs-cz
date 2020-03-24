---
title: __vectorcall
ms.date: 12/17/2018
f1_keywords:
- __vectorcall_cpp
- __vectorcall
- _vectorcall
helpviewer_keywords:
- __vectorcall keyword
- __vectorcall
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
ms.openlocfilehash: c933f995c57094b28e477e439c7b9ff5a13c2063
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187515"
---
# <a name="__vectorcall"></a>__vectorcall

**Specifické pro společnost Microsoft**

Konvence volání **__vectorcall** určuje, že argumenty funkcí mají být předány v registrech, pokud je to možné. **__vectorcall** používá další registry pro argumenty než [__fastcall](../cpp/fastcall.md) nebo výchozí [konvenci volání x64](../build/x64-calling-convention.md) . Konvence volání **__vectorcall** je podporována pouze v nativním kódu u procesorů x86 a x64, které zahrnují streaming SIMD Extensions 2 (SSE2) a vyšší. Použijte **__vectorcall** k urychlení funkcí, které předají několik argumentů s plovoucí desetinnou čárkou nebo SIMD vektor a provádějí operace, které využívají argumentů načtených v registrech. V následujícím seznamu jsou uvedeny funkce, které jsou společné pro implementace **__vectorcall**x86 a x64. Rozdíly jsou vysvětleny dále v tomto článku.

|Prvek|Implementace|
|-------------|--------------------|
|Konvence pro dekorace názvu C|Názvy funkcí jsou zaregistrované pomocí dvou znaků "on" (\@\@) následovaných počtem bajtů (v desítkové soustavě) v seznamu parametrů.|
|Konvence pro posunutí|Neprovádí se žádný překlad případu.|

Použití možnosti kompilátoru [/GV](../build/reference/gd-gr-gv-gz-calling-convention.md) způsobí, že každá funkce v modulu bude zkompilována jako **__vectorcall** , pokud funkce není členskou funkcí, je deklarována s konfliktním atributem konvence volání, používá seznam argumentů `vararg` proměnných nebo má název `main`.

Můžete předat tři druhy argumentů registrací ve **__vectorcall** Functions: hodnoty *typu Integer* , hodnoty *vektorového typu* a hodnoty HVA ( *homogenní vektor agregace* ).

Celočíselný typ splňuje dva požadavky: vejde se do nativní velikosti registru procesoru – například 4 bajty na počítači x86 nebo 8 bajtů v počítači x64 – a je převoditelné na celé číslo délky registru a zpátky bez změny bitu. obrázek. Například libovolný typ, který lze zvýšit na **int** na platformě x86 (**dlouhodobě** na platformě x64) – například **znak** nebo **krátký**, nebo který lze přetypovat na **int** (**Long Long** na platformě x64) a zpět na jeho původní typ bez změny, je celočíselný typ. Typy celých čísel zahrnují typy ukazatelů, odkazů a **struktur** nebo **sjednocení** o 4 bajty (8 bajtů na platformě x64) nebo méně. Na platformách x64 jsou větší typy **struktury** a **sjednocení** předány odkazem na paměť přidělenou volajícím. na platformách x86 jsou předávány hodnotou v zásobníku.

Vektorový typ je typ s plovoucí desetinnou čárkou, například **float** nebo **Double**– nebo typ vektoru SIMD, například **__m128** nebo **__m256**.

Typ HVA je složený typ až čtyř datových členů, které mají stejné vektorové typy. Typ HVA má stejný požadavek na zarovnání jako typ vektoru jeho členů. Toto je příklad definice **struktury** HVA, která obsahuje tři identické vektorové typy a má 32 zarovnání v bajtech:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Deklarujte své funkce explicitně pomocí klíčového slova **__vectorcall** v hlavičkových souborech, aby bylo možné samostatně kompilovaný kód propojit bez chyb. Funkce musí být prototypem pro použití **__vectorcall**a nelze použít `vararg` seznamu argumentů délky proměnné.

Členská funkce může být deklarována pomocí specifikátoru **__vectorcall** . Skrytý **Tento** ukazatel je předán registrem jako první argument typu Integer.

V počítačích ARM je **__vectorcall** přijat a ignorován kompilátorem.

U nestatických členských funkcí třídy, pokud je funkce definovaná mimo řádek, modifikátor konvence volání není nutné zadat na definici mimo řádek. To znamená, že u nestatických členů třídy se konvence volání zadaná během deklarace předpokládá v bodě definice. Při této definici třídy:

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

Je-li vytvořen ukazatel na funkci **__vectorcall** , je nutné zadat modifikátor konvence volání **__vectorcall** . V dalším příkladu se vytvoří **definice** typu pro ukazatel na **__vectorcall** funkce, která přijímá čtyři argumenty typu **Double** a vrátí **__m256** hodnotu:

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

Z důvodu kompatibility s předchozími verzemi je **_vectorcall** synonymem pro **__vectorcall** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="__vectorcall-convention-on-x64"></a>__vectorcall konvence v x64

Konvence volání **__vectorcall** na platformě x64 rozšiřuje standardní konvenci volání x64, aby mohla využívat další registry. Argumenty typu Integer i argumenty vektorového typu jsou mapovány na Registry na základě pozice v seznamu argumentů. Argumenty HVA jsou přiděleny nepoužívaným vektorovým registrům.

Pokud některý z prvních čtyř argumentů v pořadí zleva doprava jsou argumenty typu Integer, jsou předány v registru, který odpovídá této pozici – RCX, RDX, R8 nebo R9. Skrytý **Tento** ukazatel je považován za první argument typu Integer. V případě, že argument HVA v jednom z prvních čtyř argumentů nelze předat v dostupných registrech, je místo toho předán odkaz na paměť přidělenou volajícímu v odpovídajícím registru typu Integer. Argumenty typu Integer po umístění čtvrtého parametru jsou předány do zásobníku.

Pokud některý z prvních šesti argumentů v pořadí zleva doprava jsou argumenty typu vektoru, jsou předávány hodnotou v registru ve vektoru SSE 0 až 5 podle pozice argumentu. Typy s plovoucí desetinnou čárkou a **__m128** jsou předány v registrech XMM a **__m256** typy jsou předány v registrech YMM. To se liší od standardní konvence volání x64, protože vektorové typy jsou předávány hodnotou namísto odkazování a jsou použity další registry. Velikost stínového zásobníku přidělená pro argumenty vektorového typu je pevně nastavená na 8 bajtů a možnost [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) se nepoužije. Argumenty vektorového typu v sedmé a pozdější pozici parametru jsou předány v zásobníku odkazem na paměť přidělenou volajícím.

Po přidělení registrů vektorovým argumentům jsou datové členy argumentů HVA přiděleny ve vzestupném pořadí pro nepoužité vektorové Registry XMM0 na XMM5 (nebo YMM0 na YMM5 pro **__m256** typy), pokud je k dispozici dostatek registrů pro celou HVA. Není-li k dispozici dostatek registrů, argument HVA je předán odkazem na paměť přidělenou volajícím. Stínový prostor zásobníku pro argument HVA je pevně nastaven na 8 bajtů s nedefinovaným obsahem. Argumenty HVA jsou přiřazeny k registrům v pořadí zleva doprava v seznamu parametrů a můžou být na jakékoli pozici. Argumenty HVA v jedné z prvních čtyř pozic argumentu, které nejsou přiřazeny ke vektorovým registrům, jsou předány odkazem v celočíselném registru, který odpovídá této pozici. Argumenty HVA předané odkazem po umístění čtvrtého parametru jsou vloženy do zásobníku.

Výsledky funkcí **__vectorcall** jsou vráceny podle hodnoty v registrech, pokud je to možné. Výsledky typu Integer, včetně struktur nebo sjednocení o 8 nebo méně bajtů, jsou vráceny hodnotou v RAX. Výsledky vektorového typu jsou vraceny hodnotou v XMM0 nebo YMM0 v závislosti na velikosti. Výsledky HVA mají každý datový prvek vrácený hodnotou v registrech XMM0: XMM3 nebo YMM0: YMM3 v závislosti na velikosti prvku. Typy výsledků, které se nevejdou do odpovídajících registrů, jsou vráceny odkazem na paměť přidělenou volajícím.

Zásobník je udržován volajícím v implementaci **__vectorcall**x64. Kód prologu a epilogu volajícího přiděluje a vymaže zásobník volané funkce. Argumenty jsou vloženy do zásobníku zprava doleva a jsou přiděleny stínové místo zásobníku pro argumenty předané v registrech.

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

## <a name="__vectorcall-convention-on-x86"></a>__vectorcall konvence v x86

Konvence volání **__vectorcall** následuje **__fastcall** konvence 32 pro HVA celočíselné argumenty typu Integer a využívá vektorové Registry SSE pro vektorové typy a argumenty.

První dva argumenty celočíselného typu nalezené v seznamu parametrů zleva doprava jsou umístěny v ECX a EDX v uvedeném pořadí. Skrytý **Tento** ukazatel je považován za první argument typu Integer a je předán do ecx. Prvních šest argumentů vektorového typu jsou předávány hodnotou prostřednictvím vektorového registru SSE 0 až 5 v registrech XMM nebo YMM v závislosti na velikosti argumentu.

Prvních šest argumentů vektorového typu v pořadí zleva doprava jsou předány hodnotou ve vektorovém registru SSE 0 až 5. Typy s plovoucí desetinnou čárkou a **__m128** jsou předány v registrech XMM a **__m256** typy jsou předány v registrech YMM. Není přidělené žádné místo stínového zásobníku pro argumenty vektorového typu předané registrem. Sedmý a následné argumenty typu vektoru jsou předány v zásobníku odkazem na paměť přidělenou volajícím. Omezení chyby kompilátoru [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) se nevztahuje na tyto argumenty.

Po přidělení registrů vektorovým argumentům jsou datové členy argumentů HVA přiděleny vzestupnému pořadí pro nepoužité vektorové Registry XMM0 na XMM5 (nebo YMM0 pro YMM5 pro **__m256** typy), pokud je pro celý HVA k dispozici dostatek registrů. Není-li k dispozici dostatek registrů, argument HVA je předán do zásobníku odkazem na paměť přidělenou volajícím. Není přidělen žádný prostor pro stín zásobníku pro argument HVA. Argumenty HVA jsou přiřazeny k registrům v pořadí zleva doprava v seznamu parametrů a můžou být na jakékoli pozici.

Výsledky funkcí **__vectorcall** jsou vráceny podle hodnoty v registrech, pokud je to možné. Výsledky typu Integer, včetně struktur nebo sjednocení o 4 bajty nebo méně, jsou vraceny hodnotou v EAX vrátí. Struktury typu Integer nebo sjednocení o 8 bajtů nebo méně jsou vraceny hodnotou v EDX: EAX vrátí. Výsledky vektorového typu jsou vraceny hodnotou v XMM0 nebo YMM0 v závislosti na velikosti. Výsledky HVA mají každý datový prvek vrácený hodnotou v registrech XMM0: XMM3 nebo YMM0: YMM3 v závislosti na velikosti prvku. Další typy výsledků jsou vráceny odkazem na paměť přidělenou volajícím.

Implementace x86 **__vectorcall** se řídí konvencí argumentů přesunutých do zásobníku zprava doleva volajícím a volaná funkce vymaže zásobník těsně před jeho vrácením. Do zásobníku jsou vloženy pouze argumenty, které nejsou umístěny v registrech.

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
