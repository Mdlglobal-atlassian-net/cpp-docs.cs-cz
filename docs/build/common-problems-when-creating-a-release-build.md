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
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328870"
---
# <a name="common-problems-when-creating-a-release-build"></a>Běžné problémy při vytváření sestavení pro vydání

Během vývoje obvykle sestavíte a otestujete s ladicím sestavením projektu. Pokud pak vytvoříte aplikaci pro sestavení verze, může dojít k narušení přístupu.

Níže uvedený seznam ukazuje primární rozdíly mezi ladění a verze (nondebug) sestavení. Existují další rozdíly, ale následující jsou hlavní rozdíly, které by způsobily selhání aplikace v sestavení verze, když pracuje v sestavení ladění.

- [Rozložení haldy](#_core_heap_layout)

- [Kompilace](#_core_compilation)

- [Podpora ukazatele](#_core_pointer_support)

- [Optimalizace](#_core_optimizations)

Naleznete [/GZ (Catch Release-Build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) kompilace možnost informace o tom, jak zachytit chyby sestavení vydání v sestavení ladění.

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Rozložení haldy

Rozložení haldy bude příčinou asi devadesát procent zdánlivé problémy, když aplikace pracuje v ladění, ale ne vydání.

Při vytváření projektu pro ladění, používáte přidělení paměti ladění. To znamená, že všechna přidělení paměti mají kolem sebe umístěny bajty stráží. Tyto stráž bajty deteprovatují přepsání paměti. Vzhledem k tomu, že rozložení haldy se liší mezi verzí release a ladění, přepsání paměti nemusí způsobit žádné problémy v sestavení ladění, ale může mít katastrofální účinky v sestavení verze.

Další informace naleznete [v tématu Kontrola přepsání paměti](checking-for-memory-overwrites.md) a použití sestavení ladění ke kontrole [přepsání paměti](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Kompilace

Mnoho makra knihovny MFC a velká část změny implementace knihovny MFC při vytváření pro vydání. Zejména assert makro vyhodnotí na nic v sestavení verze, takže žádný z kódu nalezeného v ASSERTs budou provedeny. Další informace naleznete v [tématu Examine ASSERT Statements](using-verify-instead-of-assert.md).

Některé funkce jsou vloženy pro zvýšení rychlosti v sestavení verze. Optimalizace jsou obvykle zapnuty v sestavení verze. Používá se také jiný alokátor paměti.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Podpora ukazatele

Nedostatek informací o ladění odebere odsazení z aplikace. V sestavení verze mají zbloudilé ukazatele větší šanci ukázat na neinicializovanou paměť namísto toho, aby ukazovaly na informace o ladění.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optimalizace

V závislosti na povaze určitých segmentů kódu může optimalizační kompilátor generovat neočekávaný kód. Toto je nejméně pravděpodobná příčina problémů se sestavením verze, ale příležitostně vzniká. Řešení naleznete v [tématu Optimalizace kódu](optimizing-your-code.md).

## <a name="see-also"></a>Viz také

[Sestavení pro vydání](release-builds.md)<br/>
[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
