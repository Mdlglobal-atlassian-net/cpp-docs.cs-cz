---
title: __vectorcall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54c1473e2341c783ebf73883680d51f161d99163
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorcall"></a>__vectorcall
**Konkrétní Microsoft**  
  
 `__vectorcall` Konvence volání Určuje, že argumenty funkce mají být předány v registrech, pokud je to možné. `__vectorcall`používá další registry argumenty než [__fastcall](../cpp/fastcall.md) nebo výchozí [x64 konvence volání](../build/overview-of-x64-calling-conventions.md) použít. `__vectorcall` Konvence volání je podporována pouze v nativním kódu na x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Použití `__vectorcall` rychlost funkce, které předat několik s plovoucí desetinnou čárkou nebo argumenty vektoru SIMD a provádět operace, které využívají argumenty načíst v registrech. Následující seznam obsahuje funkce, které jsou společné pro implementace x86 a x64 `__vectorcall`. Rozdíly jsou vysvětlené později v tomto článku.  
  
|Prvek|Implementace|  
|-------------|--------------------|  
|Konvence dekorování názvů jazyka C|Názvy funkcí jsou na konci se dvěma "na" znaky @@ následovaný počtem bajtů (decimální): v seznamu parametrů.|  
|Konvence pro posunutí|Není proveden žádný případu překlad.|  
  
 Pomocí [/gv](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru způsobí, že jednotlivé funkce v modulu zkompilovat jako `__vectorcall` Pokud funkce není členské funkce, je deklarovaný s atributem konfliktní konvence volání, používá `vararg` proměnné Seznam argumentů, nebo má název `main`.  
  
 Tři druhy argumenty můžete předat pomocí registrace v `__vectorcall` funkce: *typ integer* hodnoty, *vector typ* hodnoty, a *homogenní vektoru agregace* (HVA ) hodnoty.  
  
 Celočíselného typu splňuje dva požadavky: její souvislosti s velikostí nativní registrace procesoru – například 4 bajtů na x86 počítače nebo 8 bajtů na x64 počítače – a je převést na celé číslo registrace dlouhé a zpět znovu beze změny jeho verze reprezentace. Například libovolného typu, který bude sloužit k `int` na x86 (`long long` na x64) – například `char` nebo `short`– nebo které lze převést na `int` (`long long` na x64) a zpět na původní bez změny je celé číslo typ. Typy Integer patří ukazatelů, reference, a `struct` nebo `union` typy 4 bajtů (8 bajtů na x64) nebo méně. Na x64 platforem, větší `struct` a `union` typy jsou předaná odkaz na paměť přidělená volající; na x86 platformy, jsou předávány podle hodnoty v zásobníku.  
  
 Typ vektoru je typu s plovoucí desetinnou čárkou – například `float` nebo `double`– nebo typ vektoru SIMD – například `__m128` nebo `__m256`.  
  
 Typ HVA je složeného typu až čtyři datových členů, které mají stejné vektoru typy. Typ HVA má stejný požadavek zarovnání jako typ vektoru její členy. Jedná se o příklad HVA `struct` definice, který obsahuje tři typy identické vektoru a má zarovnání 32 bajtů:  
  
```cpp  
typedef struct {  
   __m256 x;  
   __m256 y;  
   __m256 z;  
} hva3;    // 3 element HVA type on __m256  
  
```  
  
 Deklarace funkcí explicitně s `__vectorcall` – klíčové slovo v hlavičkových souborů umožňuje samostatně zkompilovaný kód propojení bez chyb. Funkce musí být deklaraci použít `__vectorcall`a nemůžete použít `vararg` seznam argumentů proměnlivou délkou.  
  
 Členské funkce může deklarovat pomocí `__vectorcall` specifikátor. Skrytého `this` ukazatel je předaná registrace jako první argument typu celé číslo.  
  
 Na počítačích ARM `__vectorcall` je přijatá a ignorovat kompilátoru.  
  
 Pro třídu nestatické členské funkce Pokud je funkce definované z přesahujících, volání modifikátor konvence nemá být zadaný v definici--line. To znamená pro nestatické členy třídy, se předpokládá konvence volání během deklarace byly zadány v místě definice. Při této definici třídy:  
  
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
  
 `__vectorcall` Volání modifikátor konvence musí zadat při ukazatel na `__vectorcall` funkce se vytvoří. V dalším příkladu se vytváří `typedef` pro ukazatel `__vectorcall` funkce, která přebírá čtyři `double` argumentů a vrátí `__m256` hodnotu:  
  
```cpp  
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);  
```  
  
## <a name="vectorcall-convention-on-x64"></a>konvence __vectorcall na x64  
 `__vectorcall` Konvence volání na x64 rozšiřuje standardní x64 konvence využít další registrů volání. Argumenty typu celé číslo a argumenty typu vektoru jsou namapované na registrů na základě pozice v seznamu argumentů. Argumenty HVA jsou přiděleny nepoužívané vektoru Registry.  
  
 Pokud některý z argumentů první čtyři v pořadí zleva doprava jsou argumenty typu integer, jsou předávány v registru, který odpovídá této pozici – RCX, RDX, R8 nebo R9. Skrytý `this` ukazatel je považován za první argument typu celé číslo. Pokud argument HVA v jednom z první čtyři argumenty nelze předat v registry k dispozici, je odkaz na volající přidělené paměti místo předán v odpovídající registru typu integer. Argumenty typu Integer po čtvrtého parametru pozice se předávají v zásobníku.  
  
 Pokud některý z prvních šesti argumentů, aby zleva doprava se vector argumenty typu, jsou předávány podle hodnoty v registrech vektoru SSE 0 až 5 podle pozice argument. S plovoucí desetinnou čárkou a `__m128` typy se předávají v XMM registrů a `__m256` typy jsou předané YMM zaregistruje. To se liší od standardní x64 konvence, volání, protože vektoru typy jsou předány podle hodnoty místo odkazem a další zaregistruje se používají. Stínové zásobníku místo přidělené pro argumenty typu vektoru vyřešen na 8 bajtů a [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) možnost se nevztahuje. Argumenty typu vektoru v pozice sedmého a novější parametrů jsou předaná v zásobníku odkaz na paměti přidělené volající.  
  
 Po registry jsou přiděleny vektoru argumenty, datové členy HVA argumentů přidělovány ve vzestupném pořadí, nepoužívané vektoru registruje XMM0 XMM5 závislé (nebo YMM0 k YMM5, pro `__m256` typy), a pokud nejsou k dispozici pro dostatek registrů celý HVA. Není-li dostatek registry jsou k dispozici, je HVA argument předaná odkaz na paměti přidělené volající. Prostoru stínové zásobníku pro HVA argument se stanoví na 8 bajtů s nedefinované obsahem. Argumenty HVA přiřazené k registrů v pořadí zleva doprava v seznamu parametrů a může být ve všech pozici. HVA argumenty v jednom z první čtyři argument, že pozice, které nejsou přiřazeny k vector zaregistruje se budou předávat odkazem v registru integer, která odpovídá této poloze. HVA argumenty předávané odkazem po čtvrtého parametru pozice se instaluje v zásobníku.  
  
 Výsledky `__vectorcall` se funkce vrátí hodnotu ve registrů, pokud je to možné. Výsledky typu integer, včetně struktury a sjednocení 8 bajtů nebo méně, se vrátí hodnotu ve RAX. Vektor typ výsledky se vrátí hodnotu ve XMM0 nebo YMM0, v závislosti na velikosti. Výsledky HVA musí každý datový prvek vrácené hodnoty v XMM0:XMM3 registry nebo YMM0:YMM3, v závislosti na velikosti elementu. Typy výsledků, které se nehodí v odpovídající zaregistruje se vrátí pomocí odkazu na paměti přidělené volající.  
  
 V zásobníku se spravuje pomocí volající v x64 implementace `__vectorcall`. Kód volající prolog a epilog přiděluje a vymaže zásobníku pro volaná funkce. Argumenty se instaluje v zásobníku zprava doleva a místa v zásobníku stínové přidělené argumentů předaných v registrech.  
  
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
 `__vectorcall` Způsobem konvenci volání `__fastcall` konvence pro argumenty typu 32bitové celé číslo a trvá výhod registry vektoru SSE HVA argumentů a vektoru typu.  
  
 První argumenty typu dva celé číslo najít v seznamu parametrů zleva doprava jsou umístěny v ECX a EDX, v uvedeném pořadí. Skrytý `this` ukazatel je považován za první argument typu celé číslo a je předán v ECX. První argumenty typu šesti vektoru jsou předaná hodnota prostřednictvím SSE vektoru registry 0 až 5 v registrech XMM nebo YMM, v závislosti na velikosti argument.  
  
 Prvních šest vector argumenty typu, aby zleva doprava jsou předaná hodnota v registrech vektoru SSE 0 až 5. S plovoucí desetinnou čárkou a `__m128` typy se předávají v XMM registrů a `__m256` typy jsou předané YMM zaregistruje. Argumenty typu vektoru předaná registrace je přiděleno místo žádné stínové zásobníku. Argumenty typu sedmého a následné vektoru jsou předaná v zásobníku odkaz na paměti přidělené volající. Omezení kompilátoru chyby [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) nevztahuje na tyto argumenty.  
  
 Po registry jsou přiděleny vektoru argumenty, data členy HVA argumenty jsou přiděleny ve vzestupném pořadí k nepoužívané vektoru zaregistruje XMM0 k XMM5 závislé (nebo YMM0 k YMM5, pro `__m256` typy), a pokud nejsou k dispozici pro celý dostatek registry HVA. Pokud jsou k dispozici dostatek registrů, HVA argument předaná v zásobníku odkaz na paměti přidělené volající. Žádné místo stínové zásobníku pro HVA argument je přidělen. Argumenty HVA přiřazené k registrů v pořadí zleva doprava v seznamu parametrů a může být ve všech pozici.  
  
 Výsledky `__vectorcall` se funkce vrátí hodnotu ve registrů, pokud je to možné. Výsledky typu integer, včetně struktury a sjednocení 4 bajtů nebo méně, se vrátí hodnotu ve EAX. Podle hodnoty v EDX:EAX jsou vráceny struktury typ celé číslo nebo sjednocení 8 bajtů nebo méně. Vektor typ výsledky se vrátí hodnotu ve XMM0 nebo YMM0, v závislosti na velikosti. Výsledky HVA musí každý datový prvek vrácené hodnoty v XMM0:XMM3 registry nebo YMM0:YMM3, v závislosti na velikosti elementu. Ostatní typy výsledků se vrátí pomocí odkazu na paměti přidělené volající.  
  
 X86 implementace `__vectorcall` způsobem konvence argumenty nabídnutých v zásobníku zprava doleva volající a volaná funkce vymaže zásobníku těsně před vrátí. V zásobníku se odesílají pouze argumenty, které nejsou umístěné v registrech.  
  
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
  
 **Konkrétní Microsoft end**  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)