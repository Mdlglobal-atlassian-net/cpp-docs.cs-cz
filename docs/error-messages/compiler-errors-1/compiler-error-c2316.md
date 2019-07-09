---
title: Chyba kompilátoru C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693447"
---
# <a name="compiler-error-c2316"></a>Chyba kompilátoru C2316

> "*class_type*': nejde zachytit, protože destruktor nebo kopírovací konstuktor jsou nedostupné nebo odstraněné

Zachycení výjimky podle hodnoty nebo odkazu, ale kopie konstruktoru, operátor přiřazení, nebo obojí nejsou přístupné.

## <a name="remarks"></a>Poznámky

Tuto chybu vyrovnat chybný catch příkazy výjimek knihovny MFC odvozené od provedeny změny přizpůsobení ve Visual Studiu 2015 `CException`. Protože `CException` zděděné soukromý kopírovací konstruktor, třída a odvozené nejsou kopírovatelné a nemůže být předán podle hodnoty, což také znamená, že nemůže být zachycena hodnotou. Catch – příkazy, které zachytila MFC výjimky podle hodnoty dříve vedl k nezachycené výjimky za běhu. Kompilátor nyní správně identifikuje této situaci a ohlásí chybu C2316. Chcete-li vyřešit tento problém, doporučujeme vám použít makra MFC TRY/CATCH místo psaní vlastních obslužných rutin výjimek. Pokud to není vhodná pro váš kód, zachycujte výjimky MFC místo toho podle odkazu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2316 a ukazuje způsob, jak ho opravit:

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
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
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
