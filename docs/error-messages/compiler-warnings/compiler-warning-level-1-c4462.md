---
title: Upozornění kompilátoru (úroveň 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: bd4d5c1fd7dd8d7419fc901149ceab7e769e7076
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404049"
---
# <a name="compiler-warning-level-1-c4462"></a>Upozornění kompilátoru (úroveň 1) C4462

> Nelze určit identifikátor GUID tohoto typu. Program může při běhu selhat.

Upozornění c4462 v aplikaci Windows Runtime nebo komponenty, pokud veřejná `TypedEventHandler` má jako jeden ze svých parametrů odkaz na ohraničující třídy.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Například převeďte C4462 na problém upozornění úrovně 4, přidejte tento řádek do souboru zdrojového kódu:

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Příklad

Tato ukázka vygeneruje upozornění C4462:

```cpp
namespace N
{
    public ref struct EventArgs sealed {};
    public ref struct R sealed
    {
        R() {}
        event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
    };
}

[Platform::MTAThread]
int main()
{
    auto x = ref new N::R();
}
```

Tuto chybu lze obejít dvěma způsoby. Jeden z nich, uvedený v následujícím příkladu, spočívá v tom, že události udělíte interní přístupnost, aby byla dostupná kódu ve stejném spustitelném souboru, ale nikoli kódu v jiných součástech prostředí Windows Runtime.

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

Pokud musí být událost veřejná, můžete použít jiné zástupné řešení, a sice ji zpřístupnit prostřednictvím výchozího rozhraní:

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

Identifikátor GUID typu `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` se používá pouze při typu přistupuje z jiné součásti. První zástupné řešení funguje, protože k němu lze získat přístup pouze v rámci vlastní komponenty. V opačném případě musí kompilátor předpokládat nejhorší případ a vydat upozornění.
