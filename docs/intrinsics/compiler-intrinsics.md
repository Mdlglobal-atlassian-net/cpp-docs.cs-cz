---
title: Vnitřní funkce kompilátoru
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 6f41b56995e1a5a7d7f4267cb1def5370f953d5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171668"
---
# <a name="compiler-intrinsics"></a>Vnitřní funkce kompilátoru

Většina funkcí je obsažena v knihovnách, ale některé funkce jsou integrovány (to znamená vnitřní) pro kompilátor. Tyto prvky se označují jako vnitřní funkce nebo vnitřní objekty.

## <a name="remarks"></a>Poznámky

Pokud je funkce vnitřní, kód pro tuto funkci je obvykle vložen vloženě, což vyloučí režii volání funkce a umožní, aby byly pro tuto funkci generovány vysoce efektivní pokyny pro počítače. Vnitřní je často rychlejší než ekvivalentní vložené sestavení, protože Optimalizátor má integrované znalosti o tom, kolik vnitřních objektů se chová, takže některé optimalizace mohou být k dispozici, které nejsou k dispozici při použití vloženého sestavení. Optimalizátor také může rozšířit vnitřní odlišně, zarovnat vyrovnávací paměti jinak nebo provádět jiné úpravy v závislosti na kontextu a argumentech volání.

Použití vnitřních objektů má vliv na přenositelnost kódu, protože vnitřní objekty, které jsou k dispozici v C++ jazyce Visual, nemusí být k dispozici, pokud je kód zkompilován s jinými kompilátory a některé vnitřní objekty, které mohou být k dispozici pro některé cílové architektury, nejsou k dispozici pro všechny architektury. Vnitřní objekty jsou však obvykle více přenosné než vložené sestavení. Vnitřní objekty jsou požadovány v 64 architekturách, kde není podporováno vložené sestavení.

Některé vnitřní objekty, například `__assume` a `__ReadWriteBarrier`, poskytují informace kompilátoru, který má vliv na chování Optimalizátoru.

Některé vnitřní objekty jsou k dispozici pouze jako vnitřní objekty a některé jsou k dispozici v rámci funkcí i vnitřních implementací. Můžete dát kompilátoru pokyn, aby používal vnitřní implementaci jedním ze dvou způsobů v závislosti na tom, zda chcete povolit pouze konkrétní funkce nebo chcete povolit všechny vnitřní objekty. Prvním způsobem je použití`)``#pragma intrinsic(`*vnitřních funkcí-Name-list* . Direktivu pragma lze použít k určení jednoho vnitřního nebo více vnitřních objektů oddělených čárkami. Druhým je použití možnosti kompilátoru [/Oi (generovat vnitřní funkce)](../build/reference/oi-generate-intrinsic-functions.md) , která zpřístupňuje všechny vnitřní objekty na dané platformě. V části **/Oi**použijte `#pragma function(`*vnitřní funkce-název-seznam*`)` k vynucení použití volání funkce namísto vnitřní. Pokud dokumentace pro konkrétní vnitřní poznámky, kterou rutina je k dispozici pouze jako vnitřní, je použita vnitřní implementace bez ohledu na to, zda je zadána možnost **/Oi** nebo `#pragma intrinsic`. Ve všech případech **/Oi** nebo `#pragma intrinsic` umožňuje, ale nenutí, aby Optimalizátor používal vnitřní. Optimalizátor může stále volat funkci.

Některé standardní funkce jazykaC++ C/knihovny jsou k dispozici ve vnitřních implementacích na některých architekturách. Při volání funkce CRT je použita vnitřní implementace, pokud je **/Oi** zadáno na příkazovém řádku.

K dispozici je hlavičkový soubor \<intrin. h >, který deklaruje prototypy pro společné vnitřní funkce. Vnitřní objekty specifické pro výrobce jsou k dispozici v souboru hlaviček \<immintrin. h > a \<ammintrin. h >. Kromě toho některá Hlavičková okna deklaruje funkce, které jsou mapovány na vnitřní kompilátor.

V následujících částech jsou uvedeny všechny vnitřní objekty, které jsou k dispozici v různých architekturách. Další informace o tom, jak vnitřní funkce fungují na konkrétním cílovém procesoru, najdete v referenční dokumentaci výrobce.

- [Vnitřní objekty ARM](../intrinsics/arm-intrinsics.md)

- [Vnitřní objekty ARM64](../intrinsics/arm64-intrinsics.md)

- [x86 – seznam vnitřních objektů](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64) – seznam vnitřních objektů](../intrinsics/x64-amd64-intrinsics-list.md)

- [Vnitřní objekty dostupné ve všech architekturách](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Abecední seznam vnitřních funkcí](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Viz také

[Referenční dokumentace assembleru ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft Macro Assembler – referenční dokumentace](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Referenční dokumentace běhové knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md)
