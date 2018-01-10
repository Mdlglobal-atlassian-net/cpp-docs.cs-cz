---
title: "Upozornění (úroveň 1) C4462 kompilátoru | Microsoft Docs"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4462
dev_langs: C++
helpviewer_keywords: C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95fef51c6b96146842413cd52ab203b747247398
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4462"></a>Upozornění kompilátoru (úroveň 1) C4462

> Nelze určit identifikátor GUID tohoto typu. Program může při běhu selhat.

Upozornění C4462 dojde v prostředí Windows Runtime aplikace nebo součást při veřejné `TypedEventHandler` odkazuje jako jeden z jeho parametry typu na nadřazených tříd.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Například C4462 do problémem upozornění úroveň 4, přidáte tento řádek k souboru zdrojového kódu:

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Příklad

Tato ukázka generuje upozornění C4462:

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

Identifikátor GUID typu `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` se používá pouze při přístupu k typ z jiné komponenty. První zástupné řešení funguje, protože k němu lze získat přístup pouze v rámci vlastní komponenty. V opačném případě musí kompilátor předpokládat nejhorší případ a vydat upozornění.
