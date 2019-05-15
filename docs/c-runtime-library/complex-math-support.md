---
title: Podpora komplexní matematiky C
ms.date: 05/14/2019
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: 493886fcf1dbfd3dc16487dd8650206c428bb06d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707392"
---
# <a name="c-complex-math-support"></a>Podpora komplexní matematiky C

Knihovna Microsoft C Runtime (CRT) poskytuje složitých matematických knihovních funkcí, včetně všech funkcí, které jsou vyžadované ISO C99. Kompilátor nepodporuje přímo **komplexní** nebo **_Complex** – klíčové slovo, proto implementace společnosti Microsoft používá typy struktur k reprezentaci komplexní čísla.

Tyto funkce jsou implementované vyvážit výkon s správnosti. Protože vytváření správně zakulacený výsledky mohou být nepřekonatelně drahé, tyto funkce jsou navržené tak efektivně vytvářet aproximace správně zakulacený výsledek. Ve většině případů výsledek vytvořený je v rámci +/-1 ulp výsledku správně zakulacený, ale můžou nastat případy, ve kterých je větší nepřesnost.

Složité matematické operace závisí na plovoucí bodu matematických knihovních funkcí pro jejich implementaci. Tyto funkce mají různé implementace pro jinou architekturu procesoru. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít několik implementací pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na instrukční sadu podporovaných procesoru. Například v 32bitové x86 CRT, některé funkce mají obě x87 provádění a implementaci SSE2. Při spuštění na procesor, který podporuje SSE2, se používá rychlejší provádění SSE2. Když se používá Procesorem, který nepodporuje SSE2, pomalejší x87 použita implementace. Protože různé implementace matematických knihovních funkcí může pomocí různých procesorů pokyny a různé algoritmy jejich výsledky, funkce mohou mít různé výsledky mezi procesory. Ve většině případů jsou výsledky v rámci +/-1 ulp výsledku správně zakulacený, ale skutečné výsledky se mohou lišit mezi procesory.

## <a name="types-used-in-complex-math"></a>Typy používané v komplexní matematiky

Implementace Microsoft hlavičky complex.h definuje jako ekvivalenty C99 standardní nativní komplexní typy těchto typů:

|Standardní typ|Typ Microsoft|
|-|-|
|**komplexní float** nebo **float _Complex**|**_Fcomplex**|
|**dvojité komplexní** nebo **double _Complex**|**_Dcomplex**|
|**long double komplexní** nebo **_Complex long double**|**_Lcomplex**|

Hlaviček math.h definuje samostatný typ, **struktura _complex**, která se používá pro [_cabs](../c-runtime-library/reference/cabs.md) funkce. **Struktura _complex** typ není používán ekvivalentní složité matematické funkce [soubory CAB, cabsf, cabsl –](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Komplexní konstanty a makra

**Můžu** je definován jako **float** komplexní typ **_Fcomplex** inicializoval `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Trigonometrické funkce

|Funkce|Popis|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|COMPUTE komplexní Arkus kosinus komplexního čísla|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|COMPUTE komplexní Arkus sinus komplexního čísla|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|COMPUTE komplexní Arkus tangens komplexního čísla|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Vypočítat kosinus komplexní komplexního čísla|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|COMPUTE komplexní hodnotu sinus tohoto komplexního čísla|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Vypočítat tangens komplexní komplexního čísla|

## <a name="hyperbolic-functions"></a>Hyperbolické funkce

|Funkce|Popis|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|COMPUTE komplexní oblouk hyperbolický kosinus komplexního čísla|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|COMPUTE komplexní oblouk hyperbolický sinus komplexního čísla|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|COMPUTE komplexní hyperbolický arkustangens komplexního čísla|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|COMPUTE komplexní hyperbolický kosinus komplexního čísla|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|COMPUTE komplexní hyperbolický sinus komplexního čísla|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|COMPUTE komplexní hyperbolický tangens komplexního čísla|

## <a name="exponential-and-logarithmic-functions"></a>Exponenciální a hodnota funkce

|Funkce|Popis|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|COMPUTE komplexní základní -*e* exponenciální komplexního čísla|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|COMPUTE komplexní přirozený (základní -*e*) logaritmus komplexního čísla|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|COMPUTE komplexní základ 10 logaritmus komplexního čísla|

## <a name="power-and-absolute-value-functions"></a>Výkon a absolutní hodnota funkce

|Funkce|Popis|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Výpočtu komplexní absolutní hodnoty (také nazývané norm, modulus nebo velikost) komplexního čísla|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Výpočetní funkce komplexní power x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|COMPUTE komplexní odmocninu komplexního čísla|

## <a name="manipulation-functions"></a>Funkce pro zpracování

|Funkce|Popis|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Vytvoření komplexního čísla z reálné a imaginární části|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|COMPUTE argument komplexní čísla (také nazývané úhel fáze)|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|COMPUTE imaginární části komplexního čísla|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|COMPUTE sdružené komplexního čísla|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Projekce komplexního čísla do oblasti Riemannův COMPUTE|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|COMPUTE skutečné součástí komplexního čísla|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|COMPUTE ve čtverci velikost komplexního čísla|

## <a name="operation-functions"></a>Operace funkce

Protože komplexní čísla nejsou nativní typ v kompilátor společnosti Microsoft, standardní aritmetické operátory nejsou definované v komplexních typů. Pro usnadnění práce jsou k dispozici tyto složitých matematických knihovních funkcí umožňující manipulaci s omezenou komplexních čísel v uživatelském kódu:

|Funkce|Popis|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Vynásobí dvě komplexní čísla|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Vynásobit komplexní a číslo s plovoucí desetinnou čárkou|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
