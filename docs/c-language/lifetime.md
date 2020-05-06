---
title: Doba platnosti
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 962e5ef4cae1be142091d2a209b4c60c0b789e74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232771"
---
# <a name="lifetime"></a>Doba platnosti

„Životnost“ je doba provádění při vykonávání programu, ve které existuje proměnná nebo funkce. Doba trvání úložiště identifikátoru určuje jeho životnost.

Identifikátor deklarovaný pomocí **statického** *specifikátoru třídy úložiště* má trvání statického úložiště. Identifikátory se statickou dobou úložiště (nazývané také „globální“) mají úložiště a definovanou hodnotu po dobu vykonávání programu. Úložiště je vyhrazeno a uložená hodnota identifikátoru je inicializována pouze jednou, před spuštěním programu. Identifikátor deklarovaný s externím nebo interním propojením má také trvání statického úložiště (viz [propojení](../c-language/linkage.md)).

Identifikátor deklarovaný bez specifikátoru třídy úložiště **static** má automatickou dobu trvání úložiště, pokud je deklarovaný uvnitř funkce. Identifikátor s automatickou dobou trvání úložiště („místní identifikátor“) má úložiště a definovanou hodnotou pouze v rámci bloku, kde je identifikátor definován nebo deklarován. Automatickému identifikátoru je přiděleno nové úložiště pokaždé, když program přejde do tohoto bloku a ztratí své úložiště (a jeho hodnotu) při opuštění bloku programem. Identifikátory, které jsou deklarovány ve funkci bez propojení, mají také automatickou dobu trvání úložiště.

Následující pravidla určují, zda má identifikátor globální (statickou) nebo místní (automatickou) životnost:

- Všechny funkce mají statickou životnost. A proto existují po celou dobu při provádění programu. Identifikátory deklarované na vnější úrovni (tedy mimo všechny bloky v programu na stejné úrovni definic funkcí) mají vždy globální (statickou) životnost.

- Pokud místní proměnná má inicializátor, je proměnná inicializována při každém vytvoření (Pokud není deklarována jako **statická**). Parametry funkce mají také místní životnost. V rámci bloku můžete zadat globální životnost identifikátoru zahrnutím specifikátoru třídy úložiště **static** ve své deklaraci. Po deklaraci **static**zachová proměnná hodnotu z jedné položky bloku do další.

I když identifikátor s globální životností existuje během provádění zdrojového programu (například externě deklarovanou proměnnou nebo místní proměnnou deklarovaná pomocí klíčového slova **static** ), nemusí být viditelný ve všech částech programu. Viz téma [Rozsah a viditelnost](../c-language/scope-and-visibility.md) pro informace o viditelnosti a viz [třídy úložiště](../c-language/c-storage-classes.md) pro diskuzi o neterminálu *specifikátoru úložiště-třídy* .

Paměť lze rozdělit podle potřeby (dynamicky), pokud je vytvářena pomocí speciálních rutin knihovny, jako je `malloc`. Jelikož dynamické přidělování paměti používá rutiny knihoven, není považováno za součást jazyka. Podívejte se [na funkci propracovat v](../c-runtime-library/reference/malloc.md) *Referenci knihovny run-time*.

## <a name="see-also"></a>Viz také

[Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)
