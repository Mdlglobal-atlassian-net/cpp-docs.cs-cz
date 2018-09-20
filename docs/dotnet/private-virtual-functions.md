---
title: Soukromé virtuální funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0058d023268fa4d9ca5abe802ff45856e9855dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418070"
---
# <a name="private-virtual-functions"></a>Soukromé virtuální funkce

Způsob, jakým jsou zpracovány soukromé virtuální funkce v odvozených třídách změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

Úroveň přístupu virtuální funkce v spravovaného rozšíření neomezuje schopnosti přepsat v odvozené třídě. V nové syntaxi virtuální funkce nemůže přepsat virtuální funkce základní třídy nemůže získat přístup. Příklad:

```
__gc class MyBaseClass {
   // inaccessible to a derived class
   virtual void g();
};

__gc class MyDerivedClass : public MyBaseClass {
public:
   // okay in Managed Extensions; g() overrides MyBaseClass::g()
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible
   void g();
};
```

Neexistuje žádné skutečné mapování tento druh návrh na novou syntaxi. Jeden má jednoduše zpřístupnit členy základní třídy – to znamená, veřejné. Zděděné metody nemusí mít stejný přístup. V tomto příkladu je nejméně invazivní změnit, aby člen MyBaseClass `protected`. Přístup k metodě prostřednictvím MyBaseClass obecné programu tímto způsobem je stále zakázaná.

```
ref class MyBaseClass {
protected:
   virtual void g();
};

ref class MyDerivedClass : MyBaseClass {
public:
   virtual void g() override;
};
```

Všimněte si, že chybí explicitní `virtual` – klíčové slovo v základní třídě v nové syntaxi, vygeneruje upozornění.

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
