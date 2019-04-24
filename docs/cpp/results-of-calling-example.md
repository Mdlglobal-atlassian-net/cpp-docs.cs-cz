---
title: Příklad výsledků volání
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268047"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání

**Microsoft Specific**

## <a name="cdecl"></a>__cdecl

Název upravený funkce jazyka C je `_MyFunc`.

![Konvenci volání CDECL](../cpp/media/vc37i01.gif "konvenci volání CDECL") <br/>
**__Cdecl** konvence volání

## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall

Dekorovaného názvu C (**__stdcall**) je `_MyFunc@20`. Název jazyka C++ dekorovaných je specifický pro implementaci.

![&#95;&#95;stdcall čárky a konvence volání thiscall](../cpp/media/vc37i02.gif "&#95;&#95;stdcall čárky a konvence nespravovaného volání") <br/>
__Stdcall a konvence volání thiscall

## <a name="fastcall"></a>__fastcall

Dekorovaného názvu C (**__fastcall**) je `@MyFunc@20`. Název jazyka C++ dekorovaných je specifický pro implementaci.

![Konvence pro volání &#95; &#95;fastcall](../cpp/media/vc37i03.gif "konvencí pro volání &#95; &#95;fastcall") <br/>
Konvence volání __fastcall

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)