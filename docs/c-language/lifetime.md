---
title: Životnost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34873681d0bc33cede9cda994aa9684e04a689e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113770"
---
# <a name="lifetime"></a>Doba platnosti

„Životnost“ je doba provádění při vykonávání programu, ve které existuje proměnná nebo funkce. Doba trvání úložiště identifikátoru určuje jeho životnost.

Identifikátor deklarovaný pomocí *storage-class-specifier* **statické** má statickou dobu úložiště. Identifikátory se statickou dobou úložiště (nazývané také „globální“) mají úložiště a definovanou hodnotu po dobu vykonávání programu. Úložiště je vyhrazeno a uložená hodnota identifikátoru je inicializována pouze jednou, před spuštěním programu. Identifikátor deklarovaný pomocí externího nebo interního propojení má také statickou dobu ukládání (viz [propojení](../c-language/linkage.md)).

Identifikátor deklarovaný bez **statické** – specifikátor třídy úložiště má automatickou dobu ukládání v případě, že je deklarována uvnitř funkce. Identifikátor s automatickou dobou trvání úložiště („místní identifikátor“) má úložiště a definovanou hodnotou pouze v rámci bloku, kde je identifikátor definován nebo deklarován. Automatickému identifikátoru je přiděleno nové úložiště pokaždé, když program přejde do tohoto bloku a ztratí své úložiště (a jeho hodnotu) při opuštění bloku programem. Identifikátory, které jsou deklarovány ve funkci bez propojení, mají také automatickou dobu trvání úložiště.

Následující pravidla určují, zda má identifikátor globální (statickou) nebo místní (automatickou) životnost:

- Všechny funkce mají statickou životnost. A proto existují po celou dobu při provádění programu. Identifikátory deklarované na vnější úrovni (tedy mimo všechny bloky v programu na stejné úrovni definic funkcí) mají vždy globální (statickou) životnost.

- Pokud má lokální proměnná inicializátor, je proměnná inicializována pokaždé, když je vytvořena (Pokud je deklarovaná jako **statické**). Parametry funkce mají také místní životnost. Můžete zadat globální životnost identifikátoru v rámci bloku zahrnutím **statické** specifikátor třídy úložiště v jeho deklaraci. Jakmile je deklarován jako **statické**, proměnná zachová svou hodnotu z jedné položky bloku na další.

Přestože identifikátor s globální životností existuje během spuštění zdrojového programu (například externě deklarovaná proměnná nebo místní proměnná deklarovaná pomocí **statické** – klíčové slovo), nemusí být viditelný ve všech části programu. Zobrazit [rozsah a viditelnost](../c-language/scope-and-visibility.md) informace o viditelnosti naleznete v tématu [třídy úložiště](../c-language/c-storage-classes.md) diskuzi o *storage-class-specifier* neterminálu.

Paměť lze rozdělit podle potřeby (dynamicky), pokud je vytvářena pomocí speciálních rutin knihovny, jako je `malloc`. Jelikož dynamické přidělování paměti používá rutiny knihoven, není považováno za součást jazyka. Najdete v článku [malloc](../c-runtime-library/reference/malloc.md) fungovat v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také

[Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)