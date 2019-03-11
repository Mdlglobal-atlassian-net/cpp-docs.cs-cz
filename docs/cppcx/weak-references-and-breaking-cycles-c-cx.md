---
title: Slabé odkazy a cykly slov (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 252c9c1d2af0bc6911beca094d97f46e681ba2f6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747070"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Slabé odkazy a cykly slov (C + +/ CX)

V systému libovolný typ, který je založen na počítání odkazů, mohl vytvořit odkazy na typy *cykly*– to znamená, že jeden objekt odkazuje na druhý objekt, druhý objekt, který odkazuje na třetí objekt a tak dále až do některých konečného objektu odkazuje zpět na první objekt. V cyklu nelze odstranit objekty správně při nulový počet odkazů na jeden objekt. Které vám pomůžou vyřešit tento problém, C + +/ CX poskytuje [Platform::weakreference – třída](../cppcx/platform-weakreference-class.md) třídy. A `WeakReference` podporuje [vyřešit](../cppcx/platform-weakreference-class.md#resolve) metodu, která vrátí hodnotu null, pokud objekt již existuje nebo vyvolává [Platform::InvalidCastException –](../cppcx/platform-invalidcastexception-class.md) Pokud objekt je aktivní, ale není typu `T`.

Jeden scénář, ve kterém `WeakReference` musí používat je, když `this` ukazatel je zachycena ve výrazu lambda, který se používá k definování obslužné rutiny události. Doporučujeme použít pojmenované metody při definování obslužné rutiny událostí, ale pokud budete chtít použít výraz lambda pro obslužnou rutinu události, nebo pokud musíte přerušit počítání cyklus v některé situace odkaz – použijte `WeakReference`. Tady je příklad:

```

using namespace Platform::Details;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Input;
using namespace Windows::UI::Xaml::Controls;

Class1::Class1()
{
    // Class1 has a reference to m_Page
    m_Page = ref new Page();

    // m_Page will have a reference to this Class1
    // so create a weak reference to this
    WeakReference wr(this);
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)
    {
       // Use the weak reference to get the object
       Class1^ c = wr.Resolve<Class1>();
       if (c != nullptr)
       {
           c->m_eventFired = true;
       }
       else
       {
           // Inform the event that this handler should be removed
           // from the subscriber list
           throw ref new DisconnectedException();
       }
    });
}

}
```

Když se vyvolá obslužnou rutinu události `DisconnectedException`, dojde k vygenerování události odebrat obslužnou rutinu z seznam předplatitelů.

## <a name="see-also"></a>Viz také:
