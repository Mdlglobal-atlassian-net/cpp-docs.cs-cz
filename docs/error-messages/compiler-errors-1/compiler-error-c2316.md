---
title: Chyba kompilátoru C2316 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2868d3a81fcbc94d8b20adcdc775363eb0a8eaeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033014"
---
# <a name="compiler-error-c2316"></a>Chyba kompilátoru C2316

> "*výjimka*': nejde zachytit, protože destruktor nebo kopírovací konstuktor jsou nedostupné

Byla výjimka zachycena hodnotou nebo odkazem, ale nejsou přístupné kopírovací konstruktor a operátor přiřazení.

Tento kód byl přijat ve verzích aplikace Visual C++ před Visual Studio 2003, ale nyní vrátí chybu.

Tuto chybu vyrovnat chybný catch příkazy výjimek knihovny MFC odvozené od provedeny změny přizpůsobení ve Visual Studiu 2015 `CException`. Protože `CException` zděděné soukromý kopírovací konstruktor, třída a odvozené jsou nekopírovatelných a nemůže být předán podle hodnoty, což také znamená, že nemůže být zachycena hodnotou. Catch – příkazy, které zachytila MFC výjimky podle hodnoty dříve vedl k nezachycené výjimky za běhu, ale nyní kompilátor správně identifikuje tuto situaci a chybové zprávy C2316. Chcete-li vyřešit tento problém, doporučujeme že použít makra MFC TRY/CATCH spíše než napsat vlastní obslužné rutiny výjimek, ale pokud to není vhodná pro váš kód, zachytávat výjimky MFC odkazem. místo toho.

## <a name="example"></a>Příklad

Následující ukázka generuje C2316:

```
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

extern "C" int printf_s(const char*, ...);

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&)
    {
    }
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b) {   // C2316
        printf_s("Caught an exception!\n");
    }
}
```