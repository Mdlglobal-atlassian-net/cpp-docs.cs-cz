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

Během vývoje, obvykle sestavíte a otestujete pomocí ladicího buildu projektu. Pokud sestavíte aplikaci pro sestavení pro vydání, může dojít k narušení přístupu.

V následujícím seznamu jsou uvedeny hlavní rozdíly mezi laděním a sestavením verze (neladit). Existují i další rozdíly, ale následující jsou hlavní rozdíly, které by způsobily selhání aplikace v buildu pro vydání, když funguje v sestavení pro ladění.

- [Rozložení haldy](#_core_heap_layout)

- [Kompilace](#_core_compilation)

- [Podpora ukazatelů](#_core_pointer_support)

- [Optimalizace](#_core_optimizations)

Informace o tom, jak zachytit chyby sestavení vydaných verzí v sestaveních ladění, naleznete v možnosti kompilátoru [/GZ (catch release-build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) .

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Rozložení haldy

Rozložení haldy bude příčinou přibližně 90 procent zjevné problémy, když aplikace funguje v ladění, ale ne verze.

Při sestavování projektu pro ladění používáte přidělování paměti ladění. To znamená, že všechna přidělená paměť mají na sebe chráněné bajty. Tyto bajty Guard zjišťují přepsání paměti. Vzhledem k tomu, že rozložení haldy se mezi verzemi verze a ladění liší, přepsání paměti nemusí v sestavení ladění vytvořit žádné problémy, ale může mít v sestavení pro vydání závažné účinky.

Další informace naleznete v tématu [Zkontrolujte přepsání paměti](checking-for-memory-overwrites.md) a [použijte sestavení ladění pro kontrolu přepsání paměti](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Kompilace

Mnohé z maker knihovny MFC a většina implementace knihovny MFC se mění při sestavení pro vydání. Konkrétně se makro ASSERT vyhodnotí jako Nothing v sestavení pro vydání, takže se neprovede žádný kód, který by byl nalezen v kontrolním výrazu. Další informace naleznete v tématu [prostudování příkazů kontrolního výrazu](using-verify-instead-of-assert.md).

Některé funkce jsou vloženy za účelem zvýšené rychlosti sestavení pro vydání. Optimalizace jsou obecně zapnuté v buildu pro vydání. Používá se i jiný Alokátor paměti.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Podpora ukazatelů

Chybějící informace o ladění odstraní odsazení z aplikace. V sestavení pro vydání vydaných verzí mají osamocený ukazatel možnost ukazovat na neinicializovaná paměť místo nasměrování na informace o ladění.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optimalizace

V závislosti na povaze určitých segmentů kódu může optimalizovat kompilátor generovat neočekávaný kód. Jedná se o nejmenší pravděpodobnou příčinu problémů s vydáním sestavení, ale k tomu dojde v některých případech. Řešení najdete v tématu [optimalizace kódu](optimizing-your-code.md).

## <a name="see-also"></a>Viz také

[Sestavení pro vydání](release-builds.md)<br/>
[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
