---
title: Příklad výsledků volání
ms.date: 09/05/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 96582e48912bb591d869bbc4df179299e6459f1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500932"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání

**Specifické pro Microsoft**

## <a name="cdecl"></a>__cdecl

Název upravený funkce jazyka C je `_MyFunc`.

![Konvenci volání CDECL](../cpp/media/vc37i01.gif "vc37I01") **__cdecl** konvence volání

## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall

Dekorovaného názvu C (**__stdcall**) je `_MyFunc@20`. Název jazyka C++ dekorovaných je specifický pro implementaci.

![&#95;&#95;stdcall čárky a konvence volání thiscall](../cpp/media/vc37i02.gif "vc37I02") __stdcall a konvence volání thiscall

## <a name="fastcall"></a>__fastcall

Dekorovaného názvu C (**__fastcall**) je `@MyFunc@20`. Název jazyka C++ dekorovaných je specifický pro implementaci.

![Konvence pro volání &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03") konvenci volání __fastcall

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)