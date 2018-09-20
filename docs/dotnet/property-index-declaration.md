---
title: Deklarace indexu vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6917742b285b3700548b54fef164d01c0594e5e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380462"
---
# <a name="property-index-declaration"></a>Deklarace indexu vlastnosti

Syntaxe pro deklarování indexovanou vlastnost byl změněn z spravovaných rozšíření jazyka C++ na Visual C++.

Dva primární nedostatku spravovaných rozšíření jazykové podpory indexovaných vlastností je nemožnost zadejte úroveň třídy předplatné; To znamená, jsou všechny indexované vlastnosti musí být zadaný název, a proto neexistuje žádný způsob, například k poskytování spravovaného dolní index operátor, který je možné použít přímo na `Vector` nebo `Matrix` objektu třídy. Druhým, méně důležité nedostatku je, že je vizuálně obtížně rozlišovat vlastnost z indexované vlastnosti – počet parametrů je jediné, co zjistí. Nakonec indexované vlastnosti trpí stejnými problémy, jako u neindexované vlastnosti – přístupové objekty nejsou považovány za atomickou jednotku, ale rozdělené na jednotlivé metody.  Příklad:

```
public __gc class Vector;
public __gc class Matrix {
   float mat[,];

public:
   __property void set_Item( int r, int c, float value);
   __property float get_Item( int r, int c );

   __property void set_Row( int r, Vector* value );
   __property Vector* get_Row( int r );
};
```

Jak je vidět tady, jsou indexery jen tak další parametry, jak zadat dvě nebo jeden index dimenze. V nové syntaxi jsou indexery závorku ([],) za název indexeru a označující počet a typ každý index:

```
public ref class Vector {};
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   property float Item [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

K označení na úrovni indexer tříd, který lze použít přímo pro objekty třídy v nové syntaxi `default` – klíčové slovo je znovu k nahrazení pro explicitní název. Příklad:

```
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   // ok: class level indexer now
   //
   //     Matrix mat;
   //     mat[ 0, 0 ] = 1;
   //
   // invokes the set accessor of the default indexer

   property float default [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

V nové syntaxi používání výchozí hodnota je zadána vlastnost, oba tyto názvy jsou vyhrazené: `get_Item` a `set_Item`. Je to proto, že jedná se o základní názvy generovaný pro výchozí indexovanou vlastnost.

Všimněte si, že neexistuje žádná jednoduchá index syntaxe podobná syntaxe jednoduchou vlastnost.

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
