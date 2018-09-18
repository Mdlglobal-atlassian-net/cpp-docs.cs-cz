---
title: Příklad výsledků volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8f09109aab5823f339de76a1337eea77a0794cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037746"
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