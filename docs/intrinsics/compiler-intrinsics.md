---
title: Vnitřní funkce kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a11efde9be7e990608277a242d7018f347df0ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383232"
---
# <a name="compiler-intrinsics"></a>Vnitřní funkce kompilátoru

Většina funkcí je obsažena v knihovnách, ale některé funkce jsou součástí (to znamená, vnitřní) kompilátoru. Tyto jsou označovány jako vnitřní funkce nebo vnitřní objekty.

## <a name="remarks"></a>Poznámky

Pokud je funkce vnitřní, kód pro tuto funkci je obvykle připojen vloženě, vyhne se tak režii volání funkce a vysoce efektivní strojové instrukce emitování pro tuto funkci povolil. Vnitřní objekt je často rychlejší než ekvivalentní vložené sestavení, protože Optimalizátor má integrované znalosti o tom, kolik vnitřní objekty se chovají, takže může být k dispozici některé optimalizace, které nejsou k dispozici při použití vložené sestavení. Optimalizátor může také, jinak rozbalit vnitřní objekt, jinak zarovnat vyrovnávací paměti nebo provést jiné úpravy v závislosti na kontextu a argumentech volání.

Použití vnitřních objektů ovlivňuje přenositelnost kódu, protože vnitřní objekty, které jsou k dispozici v jazyce Visual C++ nemusí být k dispozici, pokud kód je kompilován jinými kompilátory a některé vnitřní objekty, které mohou být k dispozici pro některé cílové architektury nejsou k dispozici pro všechny architektury. Vnitřní objekty jsou však obvykle obecnější než vložené sestavení. Vnitřní objekty jsou nutné na 64bitové architektury, kde vložené sestavení není podporováno.

Některé vnitřní objekty, jako například `__assume` a `__ReadWriteBarrier`, poskytují informace kompilátoru, který má vliv na chování optimalizačního.

Některé vnitřní objekty jsou k dispozici pouze jako vnitřní a některé jsou dostupné ve funkci i vnitřní implementaci. Můžete dát pokyn kompilátoru, aby použil vnitřní implementace jedním ze dvou způsobů, v závislosti na tom, jestli chcete povolit pouze určité funkce nebo chcete povolit všechny vnitřní objekty. První způsob je použít `#pragma intrinsic(` *vnitřní funkce název seznamu*`)`. Direktivy pragma lze použít k určení jednoho vnitřní objektu nebo více vnitřních objektů, oddělených čárkami. Druhým je použití [/Oi (Generovat vnitřní funkce)](../build/reference/oi-generate-intrinsic-functions.md) – možnost kompilátoru, který zpřístupňuje všechny vnitřní objekty na dané platformě. V části **/Oi**, použijte `#pragma function(` *vnitřní funkce název seznamu* `)` k vynucení funkce volání, který se má použít namísto použití vnitřního objektu. Pokud v dokumentaci pro konkrétní vnitřní typ si všimne, že rutina je dostupný jenom jako vnitřní, pak bez ohledu na to, zda se použije vnitřní implementace **/Oi** nebo `#pragma intrinsic` určena. Ve všech případech **/Oi** nebo `#pragma intrinsic` umožňuje, ale nenutí Optimalizátor, aby použil vnitřní typy. Optimalizátor může stále volat funkci.

Některé standardní funkce knihovny C/C++ jsou k dispozici při vnitřní implementaci v některých architekturách. Při volání funkce CRT, pokud se používá vnitřní implementace **/Oi** je zadán v příkazovém řádku.

Soubor hlaviček \<intrin.h >, je k dispozici, který deklaruje prototypy pro vnitřní běžné funkce. Specifické pro výrobce vnitřní objekty jsou k dispozici v \<immintrin.h > a \<ammintrin.h > hlavičkové soubory. Některé hlavičky Windows navíc deklarují funkce, které mapovány na vnitřní kompilátor.

V následujících částech všechny vnitřní objekty, které jsou k dispozici v různých architekturách. Další informace o tom, jak na konkrétní cílový procesor funguje uvnitř naleznete v dokumentaci od výrobce.

- [ARM – vnitřní prvky](../intrinsics/arm-intrinsics.md)

- [x86 – seznam vnitřních objektů](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64) – seznam vnitřních objektů](../intrinsics/x64-amd64-intrinsics-list.md)

- [Vnitřní objekty dostupné ve všech architekturách](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Abecední seznam vnitřních funkcí](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Viz také

[Referenční dokumentace assembleru ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft Macro Assembler – referenční dokumentace](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)