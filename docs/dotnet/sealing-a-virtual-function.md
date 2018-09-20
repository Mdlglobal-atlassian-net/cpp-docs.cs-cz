---
title: Zapečetění virtuální funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385180"
---
# <a name="sealing-a-virtual-function"></a>Zapečetění virtuální funkce

Syntaxe zapečetění virtuální funkce změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

`__sealed` – Klíčové slovo se používá ve spravovaných rozšíření k úpravě buď typ odkazu, zakazuje následné odvození z něj (naleznete v tématu [deklarace spravovaného typu třídy](../dotnet/declaration-of-a-managed-class-type.md)), nebo pro úpravu virtuální funkce, zákaz následné přepsání metody v odvozené třídě. Příklad:

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

V tomto příkladu `derived::f()` přepsání `base::f()` instance založené na přesnou shodu prototypu funkce. `__sealed` – Klíčové slovo označuje, že následná třída dědí z odvozené třídy nemůže poskytnout přepsání `derived::f()`.

V nové syntaxi `sealed` je umístěn za podpis a ne kdekoli před prototyp skutečné funkce, jako byl dřív povolen. Kromě toho používání `sealed` vyžaduje explicitní použití atributu `virtual` také – klíčové slovo. To znamená, správný překlad `derived`výše, vypadá takto:

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

Chybí `virtual` – klíčové slovo v tomto případě má za následek chybu. V nové syntaxi kontextové klíčové slovo `abstract` lze použít místo `=0` udávajících čistě virtuální funkce. To není podporováno v rámci spravovaného rozšíření. Příklad:

```
__gc class base { public: virtual void f()=0; };
```

může být přepsán ve formátu

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)