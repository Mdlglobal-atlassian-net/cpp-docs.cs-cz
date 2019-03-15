---
title: Běžné problémy při vytváření sestavení pro vydání
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 7420fd5bbdeec30e9839206803952c02b8b56421
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823355"
---
# <a name="common-problems-when-creating-a-release-build"></a>Běžné problémy při vytváření sestavení pro vydání

Během vývoje bude obvykle sestavovat a testovat pomocí sestavení pro ladění projektu. Pokud potom sestavíte aplikaci pro sestavení pro vydání, můžete obdržet narušení přístupu.

V seznamu níže jsou uvedeny základní rozdíly mezi ladění a sestavení pro vydání (nondebug). Existují další rozdíly, ale toto jsou základní rozdíly, které by mohly způsobit selhání aplikace v sestavení pro vydání, když to funguje v sestavení pro ladění.

- [Rozložení haldy](#_core_heap_layout)

- [Kompilace](#_core_compilation)

- [Podpora ukazatele](#_core_pointer_support)

- [Optimalizace](#_core_optimizations)

Zobrazit [/GZ (zachytávat chyby sestavení pro vydání v sestavení ladění)](reference/gz-enable-stack-frame-run-time-error-checking.md) chyby v sestaveních ladění sestavení pro informace o tom, jak zachytávat release – možnost kompilátoru.

##  <a name="_core_heap_layout"></a> Rozložení haldy

Rozložení haldy bude příčinu o devadesát procent zřejmé problémy při aplikace funguje v ladění, ale ne verzi.

Při vytváření projektu pro ladění používáte přidělení paměti ladění. To znamená, že guard bajtů kolem nich všechna přidělení paměti. Tyto guard bajtů detekovat přepisování paměti. Protože se liší mezi vydání a ladění haldy rozložení verze, přepisování paměti nemusí vytvořit žádné problémy s v sestavení pro ladění, ale může mít katastrofální důsledky v sestavení pro vydání.

Další informace najdete v tématu [zkontrolujte přepsání paměti](checking-for-memory-overwrites.md) a [použít ladění sestavení pro kontroly pro přepsání paměti](using-the-debug-build-to-check-for-memory-overwrite.md).

##  <a name="_core_compilation"></a> Kompilace

Mnohé z maker MFC a mnoho změn implementace MFC při sestavení pro vydání. Zejména makra ASSERT vyhodnotí jako nothing v sestavení pro vydání, takže žádný kód, který najdete v nepodmíněné výrazy se spustí. Další informace najdete v tématu [prozkoumat Assert – příkazy](using-verify-instead-of-assert.md).

Některé funkce jsou vloženy pro zvýšení rychlosti v sestavení pro vydání. V sestavení pro vydání se obecně zapnutými optimalizacemi. Přidělovač paměti různých se také používá.

##  <a name="_core_pointer_support"></a> Podpora ukazatele

Chybí informace o ladění odstraní odsazení z vaší aplikace. Ukazatele stray v sestavení pro vydání, máte pravděpodobně odkazující na neinicializované paměti namísto odkazující na informace o ladění.

##  <a name="_core_optimizations"></a> Optimalizace

V závislosti na povaze určité segmenty kódů optimalizující kompilátor může vygenerovat neočekávaný kód. Toto je nejméně pravděpodobné příčiny problémů se sestavením pro vydání, ale v některých případech dojít. Řešení, najdete v části [optimalizace kódu](optimizing-your-code.md).

## <a name="see-also"></a>Viz také:

[Sestavení pro vydání](release-builds.md)<br/>
[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
