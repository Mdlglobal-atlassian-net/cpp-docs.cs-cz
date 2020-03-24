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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179052"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání

**Specifické pro společnost Microsoft**

## <a name="__cdecl"></a>__cdecl

Název vydekorované funkce jazyka C je `_MyFunc`.

![Konvence volání CDECL](../cpp/media/vc37i01.gif "Konvence volání CDECL") <br/>
Konvence volání **__cdecl**

## <a name="__stdcall-and-thiscall"></a>__stdcall a thiscall

Upravený název jazyka C ( **__stdcall**) je `_MyFunc@20`. C++ Dekorovaný název je specifický pro konkrétní implementaci.

![&#95;&#95;konvence volání StdCall a thiscall](../cpp/media/vc37i02.gif "&#95;&#95;konvence volání StdCall a thiscall") <br/>
Konvence volání __stdcall a thiscall

## <a name="__fastcall"></a>__fastcall

Upravený název jazyka C ( **__fastcall**) je `@MyFunc@20`. C++ Dekorovaný název je specifický pro konkrétní implementaci.

![Konvence volání &#95; &#95;pro fastcall](../cpp/media/vc37i03.gif "Konvence volání &#95; &#95;pro fastcall") <br/>
Konvence volání __fastcall

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)
