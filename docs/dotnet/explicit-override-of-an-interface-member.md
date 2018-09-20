---
title: Explicitní přepsání člena rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409022"
---
# <a name="explicit-override-of-an-interface-member"></a>Explicitní přepsání člena rozhraní

Syntaxe deklarace explicitní přepsání člena rozhraní v rámci třídy byl změněn z spravovaných rozšíření jazyka C++ na Visual C++.

Často chcete poskytnout dvě instance člena rozhraní v rámci třídy, která implementuje rozhraní – ten, který se používá při manipulaci s objekty třídy prostřednictvím popisovače rozhraní a ten, který se používá, když se používají objekty třídy prostřednictvím rozhraní třídy. Příklad:

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

Ve spravovaných rozšíření jsme to provést tím, že poskytuje explicitní deklaraci metody rozhraní s názvem metody kvalifikovány názvem rozhraní. Instance specifický pro třídu neúplný. To eliminuje potřebu přetypování směrem dolů na návratový typ `Clone`, v tomto příkladu, při explicitní volání prostřednictvím instance `R`.

V nové syntaxi obecný mechanismus přepsání je zavedený, který nahrazuje spravovaných rozšíření syntaxe. Náš příklad by být přepsán následujícím způsobem:

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

Tato revize vyžaduje explicitní přepsání člena rozhraní zadat jedinečný název v rámci třídy. Tady zadání není vhodný název `InterfaceClone`. Chování je stále stejný – vyvolání prostřednictvím `ICloneable` rozhraní vyvolá přejmenované `InterfaceClone`, zatímco volání prostřednictvím objektu typu `R` vyvolá druhou `Clone` instance.

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[Explicitní přepsání](../windows/explicit-overrides-cpp-component-extensions.md)