---
title: Deklarace vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 019b8eae17952bfe53fd8fbf14db4bafce1bf463
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438298"
---
# <a name="property-declaration"></a>Deklarace vlastnosti

Způsob, jak deklarovat vlastnost ve spravované třídě byl změněn z spravovaných rozšíření jazyka C++ na Visual C++.

Ve spravovaných rozšíření návrhu, každý `set` nebo `get` přistupující objekt vlastnosti je zadán jako nezávislá metoda. Deklarace každé metody předchází `__property` – klíčové slovo. Název metody, který začíná buď `set_` nebo `get_` za nímž následuje skutečný název vlastnosti (jako je viditelné pro uživatele). Proto `Vector` poskytování `x` koordinovat `get` by název vlastnosti `get_x` a uživatel by ho vyvolat jako `x`. Tato konvence pojmenování a stará samostatná specifikace metod představuje ve skutečnosti základní implementace modulu runtime vlastnosti. Například tady je náš `Vector` sadu souřadnice vlastnosti:

```
public __gc __sealed class Vector {
public:
   __property double get_x(){ return _x; }
   __property double get_y(){ return _y; }
   __property double get_z(){ return _z; }

   __property void set_x( double newx ){ _x = newx; }
   __property void set_y( double newy ){ _y = newy; }
   __property void set_z( double newz ){ _z = newz; }
};
```

Tím se šíří si moct funkce související s vlastností a vyžaduje, aby uživatel lexikálně sjednotit přidružené nastaví a získá. Kromě toho je verbose. V nové syntaxi, což je více, C#, `property` klíčovým slovem následovalo typ vlastnosti a jeho prostým názvem. `set` a `get` přístupové metody jsou umístěny v rámci bloku následující název vlastnosti. Všimněte si, že na rozdíl od jazyka C#, podpis metody přístupu je zadán. Tady je příklad výše uvedeném příkladu kódu přeložit na novou syntaxi.

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

      void set( double newx ) {
         _x = newx;
      }
   } // Note: no semi-colon
};
```

Pokud přístupové metody, vlastnosti, jako odrážet přístup různé úrovně – `public get` a `private` nebo `protected set`, můžete zadat explicitní přístup popisku. Ve výchozím nastavení zobrazuje úroveň přístupu vlastnosti, která z nadřazené úrovně přístupu. Například ve výše uvedené definice `Vector`, obojí `get` a `set` metody jsou `public`. Chcete-li `set` metoda `protected` nebo `private`, definice by být upravena takto:

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

   private:
      void set( double newx ) {
         _x = newx;
      }

   } // note: extent of private culminates here

// note: dot is a public method of Vector
double dot( const Vector^ wv );

// etc.
};
```

Obor přístupu klíčového slova v rámci vlastnosti rozšiřuje do obou pravé složené závorce vlastnosti nebo specifikace – klíčové slovo další přístup. Nerozšiřuje mimo definici vlastnosti do nadřazené úrovně přístupu, ve kterém je definována vlastnost. Ve výše uvedené prohlášení, například `Vector::dot()` je veřejné metody.

Zápis nastavení nebo získání vlastností pro tři `Vector` souřadnice zahrnuje tři kroky:

1. deklarování člena soukromý stav příslušného typu.

1. Pokud chce uživatel získat jeho hodnotu, vrátí jej.

1. přiřadí novou hodnotu.

V nové syntaxi je syntaxi ve zkráceném tvaru vlastnost k dispozici která automatizuje tento vzor využití:

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   property double x;
   property double y;
   property double z;
};
```

Zajímavé vedlejším účinkem syntaxi ve zkráceném tvaru vlastnost je, že i když stav backstage je generovaný kompilátorem, není dostupná ve třídě s výjimkou prostřednictvím přístupové objekty set/get.

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[property](../windows/property-cpp-component-extensions.md)